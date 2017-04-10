---
title: "查詢處理架構指南 | Microsoft Docs"
ms.custom: ""
ms.date: "10/26/2016"
ms.prod: "sql-non-specified"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "指南, 查詢處理架構"
  - "查詢處理架構指南"
ms.assetid: 44fadbee-b5fe-40c0-af8a-11a1eecf6cb5
caps.latest.revision: 5
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 5
---
# 查詢處理架構指南
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

Database Engine 會處理各種資料儲存架構上的查詢，例如本機資料表、資料分割資料表，以及分散到多部伺服器的資料表。 下列主題涵蓋 SQL Server 如何處理查詢，以及透過執行計畫快取來將查詢重複使用最佳化。

## <a name="sql-statement-processing"></a>SQL 陳述式處理

處理單一 SQL 陳述式是 SQL Server 執行 SQL 陳述式的最基本方式。 用於處理僅參考本機基底資料表 (非檢視表或遠端資料表) 之單一 `SELECT` 陳述式的步驟可說明這個基本程序。

#### <a name="optimizing-select-statements"></a>最佳化 SELECT 陳述式

`SELECT` 陳述式為非程序性，它無法敘述資料庫伺服器應用來擷取所需資料的正確步驟。 這是表示資料庫伺服器應該先分析陳述式，才能判斷出取得所需資料的最有效方式。 這稱為將 `SELECT` 陳述式最佳化。 執行此動作的元件稱為查詢最佳化工具。 最佳化工具的輸入是由查詢、資料庫結構描述 (資料表和索引定義) 以及資料庫統計資料所組成。 最佳化工具的輸出是查詢執行計畫，有時稱為查詢計畫或只是計畫。 在本主題稍後將更詳盡地描述查詢計畫的內容。

下圖說明在單一 `SELECT` 陳述式最佳化期間，查詢最佳化工具的輸入與輸出：  
![query_processor_io](../relational-databases/media/query-processor-io.gif)

`SELECT` 陳述式僅定義下列項目：  
* 結果集的格式。 這大部份是在選取清單中指定。 不過，其他如 `ORDER BY` 和 `GROUP BY` 等子句也會影響結果集的最後格式。
* 包含來源資料的資料表。 這指定於 `FROM` 子句中。
* 資料表如何在邏輯上與 `SELECT` 陳述式的目的產生關聯。 這定義於聯結規格中，其可能出現在 `FROM` 後面的 `WHERE` 子句或 `ON` 子句中。
* 來源資料表中的資料列必須滿足才能符合 `SELECT` 陳述式的條件。 這些條件指定於 `WHERE` 和 `HAVING` 子句中。


查詢執行計畫是用以定義下列項目： 

* 存取來源資料表的順序。  
  一般而言，資料庫伺服器存取基底資料表以建立結果集的順序有很多種。 例如，如果 `SELECT` 陳述式參考三個資料表，則資料庫伺服器會先存取 `TableA`、使用 `TableA` 中的資料來擷取 `TableB` 中相符的資料列，然後使用 `TableB` 中的資料來擷取 `TableC` 中的資料。 資料庫伺服器可以存取資料表的其他順序如下：  
  `TableC`、`TableB`、`TableA` 或  
  `TableB`、`TableA`、`TableC` 或  
  `TableB`、`TableC`、`TableA` 或  
  `TableC`、`TableA`、`TableB`  

* 從各資料表取得資料所用的方法。  
  一般而言，有各種不同的方式可存取每個資料表中的資料。 如果僅需要特定索引鍵值的一些資料列，則資料庫伺服器可以使用索引。 如果需要資料表中的所有資料列，則資料庫伺服器可以忽略索引，並執行資料表掃描。 如果需要資料表中的所有資料列，但其中有一個索引的索引鍵資料行是在 `ORDER BY` 中，那麼，執行索引掃描來替代資料表掃描，就能儲存不同排序的結果集。 如果資料表非常小，則資料表掃描可能是所有資料表存取中最有效率的方式。 


從許多可能的計畫中選擇其中一個執行計畫的程序，便稱為最佳化。 查詢最佳化工具是 SQL 資料庫系統中最重要的元件之一。 因為查詢最佳化工具使用部份負擔來分析查詢並選取計畫，所以當查詢最佳化工具挑出最有效率的執行計畫時，這個負擔通常已經儲存了好幾層。 例如，兩家營造公司可能對同一間房屋有相同的藍圖。 如果有一家公司在剛開始時，願意花幾天的時間計畫將如何建造房屋，而另一家公司則不計畫就開始建造，那麼有花時間規劃其專案的公司，最有可能在第一時間完成。

SQL Server 查詢最佳化工具是以成本為基礎的最佳化工具。 每個可能的執行計畫都有計算所使用資源量的相關成本。 查詢最佳化工具必須分析可能的計畫並選擇最低估計成本的計畫。 有些複雜的 `SELECT` 陳述式具備數千個可能的執行計畫。 在這樣的情況下，查詢最佳化工具不會分析所有可能的組合。 相反的，它會使用複雜的演算法來尋找最接近最小可能成本的執行計畫。

SQL Server 查詢最佳化工具不僅會選擇資源成本最低的執行計畫，也會在傳回給使用者的結果中，選擇具合理資源成本且傳回結果速度最快的計畫。 例如，一般平行處理查詢時，需使用比循序處理時使用更多的資源，但完成的速度較快。 如果伺服器的負載不會受到負面的影響，則 SQL Server 最佳化工具將使會使用平行執行計畫來傳回結果。

查詢最佳化工具在估計以不同方法擷取資料表或索引中資訊的資源成本時，是根據散發統計資料。 散發統計資料適用於資料行和索引。 他們可指出特殊索引或資料行中值的選擇性。 例如，在表示車種的資料表中，許多車種的製造商都是相同的，但每輛車都有一個唯一的汽車識別號碼。 因此索引 VIN 比索引製造商更具選擇性。 如果目前沒有索引統計資料，則最佳化工具可能無法針對目前的資料表狀態做出最佳選擇。 如需讓索引統計資料保持最新的詳細資訊，請參閱＜使用統計資料來改善查詢效能＞。 

查詢最佳化工具非常重要，因為它可以讓資料庫伺服器進行動態調整，以變更資料庫中的情況，而不需要由程式設計人員或資料庫管理員來輸入。 這樣程式設計師便不用將焦點集中在描述查詢的最後結果。 他們可以相信每次執行陳述式時，查詢最佳化工具將依資料庫的狀態建立最有效率的執行計畫。

#### <a name="processing-a-select-statement"></a>處理 SELECT 陳述式

SQL Server 用來處理單一 SELECT 陳述式的基本步驟如下： 

1. 剖析器會掃描 `SELECT` 陳述式，並將其分成數個邏輯單位，例如關鍵字、運算式、運算子和識別碼。
2. 然後系統會建立查詢樹 (有時也稱為序列樹)，描述將來源資料轉換成結果集所需格式的邏輯步驟。
3. 查詢最佳化工具會分析可存取來源資料表的數種方式。 接著它會選取一系列的步驟，以利使用更少的資源以最快的速度傳回結果。 將會更新查詢以記錄所有的系列步驟。 查詢樹的最後最佳版本就稱為執行計畫。
4. 關聯式引擎開始執行執行計畫。 當在處理需要基底資料表中資料的步驟時，關聯式引擎會要求儲存引擎，從取自關聯式引擎的資料列集中傳回資料。
5. 關聯式引擎處理從儲存引擎傳回的資料，並將其設定成結果集所定義的格式，然後將結果集傳回給用戶端。

#### <a name="processing-other-statements"></a>處理其他的陳述式

這裡描述來用以處理 `SELECT` 陳述式的基本步驟適用於其他 SQL 陳述式，例如 `INSERT`、`UPDATE`及 `DELETE`。 `UPDATE` 與 `DELETE` 陳述式都必須將目標設定為要修改或刪除的資料列集合。 識別這些資料列的處理序，與用以識別參與 `SELECT` 陳述式結果集之來源資料列的處理序相同。 `UPDATE` 和 `INSERT` 陳述式可能都包含內嵌的 `SELECT 陳述式，其可提供要更新或插入的資料值。

即使資料定義語言 (DDL) 陳述式 (如 `CREATE PROCEDURE` 或 `ALTER TABL`) 最後會解析為系統目錄資料表上一連串的關聯式作業，但有時還是會根據資料表來解析 (如 `ALTER TABLE ADD COLUMN`)。

### <a name="worktables"></a>工作資料表

關聯式引擎在執行 SQL 陳述式中所指定的邏輯作業前，可能需要先建立一個工作資料表。 工作資料表屬於內部資料表，可用來保存中繼結果。 工作資料表會針對特定的 `GROUP BY`、`ORDER BY` 或 `UNION` 查詢而產生。 例如，如果 `ORDER BY` 子句會參考不在任何索引範圍內的資料行，則關聯式引擎可能需要產生工作資料表，根據所要求的順序來排序結果集。 工作資料表有時候也當作多工緩衝處理使用，可暫時保存執行部份查詢計畫的結果。 工作資料表建置於 `tempdb` 中，並且會在不再需要時自動卸除。

### <a name="view-resolution"></a>檢視解析

SQL Server 查詢處理器對待索引及非索引檢視表的方式不同： 

* 索引檢視的資料列是儲存在資料表庫中，並使用與資料表相同的格式。 如果查詢最佳化工具決定使用查詢計畫中的索引檢視，將以處理基底資料表的相同方式來處理索引檢視。
* 只會儲存非索引檢視的定義，而不會儲存檢視的資料列。 查詢最佳化工具會將檢視定義中的邏輯，合併到它為參考非索引檢視之 SQL 陳述式所建立的執行計畫中。 

SQL Server 查詢最佳化工具用來決定何時使用索引檢視表的邏輯，類似於用以決定何時使用資料表中索引的邏輯。 如果索引檢視中的資料涵蓋了全部或部分的 SQL 陳述式，並且查詢最佳化工具判斷出檢視中的索引是低成本的存取路徑，那麼查詢最佳化工具便會選擇該索引，而不論查詢中是否有依名稱參考此檢視。

當 SQL 陳述式參考無索引的檢視時，剖析器與查詢最佳化工具會分析 SQL 陳述式和檢視的來源，然後將它們解析成單一執行計畫。 SQL 陳述式與檢視不會分屬於不同的計畫。

例如，請考慮下列檢視：

```
USE AdventureWorks2014;
GO
CREATE VIEW EmployeeName AS
SELECT h.BusinessEntityID, p.LastName, p.FirstName
FROM HumanResources.Employee AS h 
JOIN Person.Person AS p
ON h.BusinessEntityID = p.BusinessEntityID;
GO
```

根據此檢視，這兩個 SQL 陳述式會在基底資料表上執行相同的作業，並產生相同的結果：

```
/* SELECT referencing the EmployeeName view. */
SELECT LastName AS EmployeeLastName, SalesOrderID, OrderDate
FROM AdventureWorks2014.Sales.SalesOrderHeader AS soh
JOIN AdventureWorks2014.dbo.EmployeeName AS EmpN
ON (soh.SalesPersonID = EmpN.BusinessEntityID)
WHERE OrderDate > '20020531';

/* SELECT referencing the Person and Employee tables directly. */
SELECT LastName AS EmployeeLastName, SalesOrderID, OrderDate
FROM AdventureWorks2014.HumanResources.Employee AS e 
JOIN AdventureWorks2014.Sales.SalesOrderHeader AS soh
ON soh.SalesPersonID = e.BusinessEntityID
JOIN AdventureWorks2014.Person.Person AS p
ON e.BusinessEntityID =p.BusinessEntityID
WHERE OrderDate > '20020531';
```

SQL Server Management Studio 的執行程序表功能顯示關聯式引擎為這兩個 `SELECT` 陳述式建立相同的執行計畫。

#### <a name="using-hints-with-views"></a>使用檢視的提示

在查詢中檢視所放置的提示可能與在擴充檢視以存取基底資料表時所發現的其他提示衝突。 當這種情況發生時，查詢會傳回錯誤： 例如，請考慮下列在其定義中包含資料表提示的檢視：

```
USE AdventureWorks2014;
GO
CREATE VIEW Person.AddrState WITH SCHEMABINDING AS
SELECT a.AddressID, a.AddressLine1, 
    s.StateProvinceCode, s.CountryRegionCode
FROM Person.Address a WITH (NOLOCK), Person.StateProvince s
WHERE a.StateProvinceID = s.StateProvinceID;
```

現在假設您輸入以下查詢：

```
SELECT AddressID, AddressLine1, StateProvinceCode, CountryRegionCode
FROM Person.AddrState WITH (SERIALIZABLE)
WHERE StateProvinceCode = 'WA';
```

查詢會失敗，因為查詢中 `Person.AddrState` 檢視表上所套用的 `SERIALIZABLE` 提示，會在展開該檢視表時傳播至檢視表的 `Person.Address` 與 `Person.StateProvince` 資料表中。 不過，展開檢視表也會顯示 `Person.Address` 上的 `NOLOCK` 提示。 由於 `SERIALIZABLE` 提示與 `NOLOCK` 提示相衝突，因此會產生不正確的查詢。 

`PAGLOCK`、`NOLOCK`、`ROWLOCK`、`TABLOCK` 或 `TABLOCKX` 資料表提示彼此衝突，如同 `HOLDLOCK`、`NOLOCK`、`READCOMMITTED`、`REPEATABLEREAD`、`SERIALIZABLE` 資料表提示。

提示可以透過巢狀檢視層級來傳播。 例如，假設查詢在 `v1` 檢視表中套用 `HOLDLOCK` 提示。 展開 `v1` 時，發現 `v2` 檢視是其定義的一部份。 `v2` 的定義包括其中一個基底資料表上的 `NOLOCK` 提示。 但此資料表也會繼承 `v1` 檢視表中查詢的 `HOLDLOCK` 提示。 因為 `NOLOCK` 與 `HOLDLOCK` 提示相衝突，所以查詢會失敗。

在包含檢視表的查詢中使用 `FORCE ORDER` 提示時，檢視表中資料表的聯結順序將由依序建構中的檢視表位置來決定。 例如，下列查詢會從三個資料表和一個檢視中選取：

```
SELECT * FROM Table1, Table2, View1, Table3
WHERE Table1.Col1 = Table2.Col1 
    AND Table2.Col1 = View1.Col1
    AND View1.Col2 = Table3.Col2;
OPTION (FORCE ORDER);
```

而 `View1` 的定義如下所示：

```
CREATE VIEW View1 AS
SELECT Colx, Coly FROM TableA, TableB
WHERE TableA.ColZ = TableB.Colz;
```

查詢計畫中的聯結順序為 `Table1`、`Table2`、`TableA`、`TableB`、`Table3`。

### <a name="resolving-indexes-on-views"></a>解析檢視上的索引

對於任何索引，只有在查詢最佳化工具認為有所助益時，SQL Server 才會選擇在其查詢計畫中使用索引檢視表。

所有版本的 SQL Server 中均可建立索引檢視表。 在某些 SQL Server 版本的部分版次中，查詢最佳化工具會自動考量索引檢視表。 在某些 SQL Server 版本的部分版次中，若要使用索引檢視表，必須使用 `NOEXPAND` 資料表提示。 如需進一步釐清，請參閱每個版本的說明文件。

SQL Server 查詢最佳化工具會在符合下列條件時使用索引檢視： 

* 下列工作階段選項會設定為 `ON`： 
  * `ANSI_NULLS`
  * `ANSI_PADDING`
  * `ANSI_WARNINGS`
  * `ARITHABORT`
  * `CONCAT_NULL_YIELDS_NULL`
  * `QUOTED_IDENTIFIER` 
  * `NUMERIC_ROUNDABORT` 工作階段選項會設定為 OFF。
* 查詢最佳化工具會從檢視索引資料行與查詢中的元素之間找出相符之處，例如： 
  * 位於 WHERE 子句中的搜尋條件述詞
  * 聯結作業
  * 彙總函式
  * `GROUP BY` 子句
  * 資料表參考
* 使用索引時的預估成本，擁有最佳化工具所考量的任何存取機制成本的最低值。 
* 在對應於索引檢視中之資料表參考的查詢中，每個參考的資料表 (直接參考，或藉由展開檢視以存取其基礎資料表) 都必須在查詢中套用同一組提示。

> [!NOTE] 
。 無論目前的交易隔離等級為何，在此內容中，永遠都會將 `READCOMMITTED` 和 `READCOMMITTEDLOCK` 提示視為不同的提示。
 
除了 `SET` 選項與資料表提示的需求以外，這些也是查詢最佳化工具用來判斷資料表索引是否涵蓋查詢的相同規則。 不需在查詢中指定其他項目，即可使用索引檢視。

查詢不一定要在 `FROM` 子句中明確參考索引檢視表，才能讓最佳化工具使用索引檢視表。 如果查詢中包含了基底資料表中的資料行的參考，而這些資料行也同時出現於索引檢視中，且最佳化工具的估計結果是使用索引檢視提供最低成本的存取機制，那麼最佳化工具便選擇索引檢視，這和查詢中並未直接參考基底資料表的索引時，最佳化工具選擇這些索引的方式類似。 當檢視包含查詢所未參考到的資料行，只要檢視針對涵蓋在查詢中所指定的一個或多個資料行提供最低的成本選項，最佳化工具可能就會選擇該檢視。

查詢最佳化工具會將 `FROM` 子句中參考的索引檢視表視為標準檢視表。 在最佳化程序開始時，查詢最佳化工具會將檢視的定義擴充到查詢中。 接著，會執行索引檢視比對。 索引檢視可用在最佳化工具所選取的最終執行計畫中，或者，此計畫可存取檢視所參考的基底資料表，藉以從檢視具體化必要的資料。 最佳化工具會選擇成本最低的方式。

#### <a name="using-hints-with-indexed-views"></a>搭配索引檢視使用提示

您可以使用 `EXPAND VIEWS` 查詢提示來防止在查詢中使用檢視表索引，或者可以使用 `NOEXPAND` 資料表提示，針對查詢的 `FROM` 子句所指定的索引檢視表強制使用索引。 然而，您應該讓查詢最佳化工具動態判斷每個查詢最適用的存取方法。 只有在測試已顯現出其大幅改善效能的特定情況下，才能使用 `EXPAND` 和 `NOEXPAND`。

`EXPAND VIEWS` 選項指定查詢最佳化工具在整個查詢中不會使用任何檢視表索引。 

針對檢視表指定 `NOEXPAND` 時，查詢最佳化工具就會考慮使用檢視表中所定義的任何索引。 (透過選擇性 `INDEX()` 子句來指定 `NOEXPAND`) 將強制查詢最佳化工具使用指定的索引。 `NOEXPAND` 只能指定給索引檢視表，且不得指定給尚未編製索引的檢視表。

如果未在含有檢視表的查詢中指定 `NOEXPAND` 或 `EXPAND VIEWS`，即會展開檢視表以存取基礎資料表。 若構成檢視的查詢中含有任何資料表提示，這些提示便會傳播到基礎資料表。 (此處理序在＜檢視解析＞中有較為詳盡的說明。)只要檢視的基礎資料表上所存在的多個提示彼此相同，則查詢即可與索引檢視比對。 這些提示大多會彼此相符，因為它們都直接繼承自檢視。 然而，若查詢參考資料表 (而非檢視) 以及直接套用於這些資料表的提示不相同，這種查詢將無法與索引檢視進行比對。 若 `INDEX`、`PAGLOCK`、`ROWLOCK`、`TABLOCKX`、`UPDLOCK` 或 `XLOCK` 提示會在檢視表展開後套用到查詢中所參考的資料表，查詢就無法與索引檢視表進行比對。

如果格式為 `INDEX (index_val[ ,...n] )` 的資料表提示會參考查詢中的檢視表，而您也未指定 `NOEXPAND` 提示，則會忽略索引提示。 若要指定使用特定的索引，請使用 `NOEXPAND。 

一般而言，當查詢最佳化工具將索引檢視比對到查詢時，資料表上指定的任何提示或查詢中的檢視，都會直接套用到索引檢視。 若查詢最佳化工具選擇不使用索引檢視，則所有提示都會直接傳播到檢視中所參考的資料表。 如需詳細資訊，請參閱＜檢視解析＞。 這種傳播方式不適用於聯結提示。 只會套用在查詢中的原始位置。 將查詢比對到索引檢視時，查詢最佳化工具不會考慮使用聯結提示。 若查詢計畫所使用的索引檢視表符合含有聯結提示的部分查詢，則計畫中不會使用此聯結提示。

不允許在索引檢視表的定義中使用提示。 在 80 與更高的相容性模式中，SQL Server 會在維護索引檢視表定義時，或在執行使用索引檢視表的查詢時，忽略定義中的提示。 雖然在 80 相容性模式下使用索引檢視定義中的提示並不會產生語法錯誤，但這些提示還是會被忽略。

### <a name="resolving-distributed-partitioned-views"></a>解析分散式資料分割檢視

SQL Server 查詢處理器會將分散式資料分割檢視表的效能最佳化。 分散式資料分割檢視效能最重要的一點，便是將在成員伺服器間傳輸的資料量最小化。

SQL Server 會建置智慧型動態計畫，有效使用分散式查詢來存取遠端成員資料表的資料： 

* 查詢處理器會先使用 OLE DB 來擷取各成員資料表中的檢查條件約束。 這可以讓查詢處理器將索引鍵值的散發對應到每個成員資料表中。
* 查詢處理器會將 SQL 陳述式 `WHERE` 子句中指定的索引鍵範圍，與顯示成員資料表中資料列分散情況的對應做比較。 然後，查詢處理器會建立查詢執行計畫，而此計畫的分散式查詢僅會擷取那些完成 SQL 陳述式所需的遠端資料列。 執行計畫也會以系統取得所需的資訊前，對資料或中繼資料延遲遠端成員資料表存取的方法執行。

例如，假設系統中的客戶資料表是跨 Server1 (從 1 到 3299999 的 `CustomerID`)、Server2 (從 3300000 到 6599999 的 `CustomerID`)，以及 Server3 (從 6600000 到 9999999 的 `CustomerID`) 進行資料分割。

請考慮針對這個在 Server1 上執行之查詢所建置的執行計畫：

```
SELECT *
FROM CompanyData.dbo.Customers
WHERE CustomerID BETWEEN 3200000 AND 3400000;
```

這個查詢的執行計畫會擷取本機成員資料表中 `CustomerID` 索引鍵值從 3200000 到 3299999 之間的資料列，並提交分散式查詢以擷取 Server2 中索引鍵值從 3300000 到 3400000 之間的資料列。

SQL Server 查詢處理器也可以在 SQL 陳述式的查詢執行計畫中建置動態邏輯，但在必須建置該計畫時索引鍵值是未知的。 例如，請參考這個預存程序：

```
CREATE PROCEDURE GetCustomer @CustomerIDParameter INT
AS
SELECT *
FROM CompanyData.dbo.Customers
WHERE CustomerID = @CustomerIDParameter;
```

SQL Server 無法預測每次執行程序時，`@CustomerIDParameter` 參數將提供的索引鍵值。 因為索引鍵值無法預測，所以查詢處理器也無法預測必須存取哪個成員資料表。 為了處理這種情形，SQL Server 建立了具有條件式邏輯的執行計畫 (稱為動態篩選)，可根據輸入參數值來控制要存取的成員資料表。 假設 `GetCustomer` 預存程序是在 Server1 上執行，則執行計畫邏輯就能以下列形式來表示：

```
IF @CustomerIDParameter BETWEEN 1 and 3299999
   Retrieve row from local table CustomerData.dbo.Customer_33
ELSEIF @CustomerIDParameter BETWEEN 3300000 and 6599999
   Retrieve row from linked table Server2.CustomerData.dbo.Customer_66
ELSEIF @CustomerIDParameter BETWEEN 6600000 and 9999999
   Retrieve row from linked table Server3.CustomerData.dbo.Customer_99
```

SQL Server 有時甚至會為尚未參數化的查詢建置這些類型的動態執行計畫。 最佳化工具可能會參數化查詢以重複使用執行計畫。 如果最佳化工具將對參考資料分割檢視的查詢進行參數化，則最佳化工具不會再假設需要的資料列將取自指定的基底資料表。 接著在執行計畫中必須使用動態篩選。


## <a name="stored-procedure-and-trigger-execution"></a>預存程序與觸發程序執行

SQL Server 只會儲存預存程序和觸發程序的來源。 當先執行預存程序或觸發程序時，會將來源編譯成執行計畫。 如果在執行計畫從記憶體中淘汰之前，再執行一次預存程序或觸發程序，關聯式引擎會偵測到現有的計畫並重複使用它。 如果計畫已從記憶體淘汰，就會建立新計畫。 此處理序與 SQL Server 對於所有 SQL 陳述式所依循的處理序類似。 在 SQL Server 中，相較於動態 SQL 的批次，預存程序與觸發程序的主要效能優點在於其 SQL 陳述式永遠都一樣。 因此，關聯式引擎可以輕易地將這些陳述式與任何現有的執行計畫配對。 就可以輕易地重複使用預存程序及觸發程序計畫

預存程序及觸發程序的執行計畫，將分別自呼叫預存程序，或引發觸發程序之批次的執行計畫中執行。 這可以允許更多次重複使用預存程序及觸發程序執行計畫。

## <a name="execution-plan-caching-and-reuse"></a>執行計畫快取與重複使用

SQL Server 具有一個記憶體集區，可用來儲存執行計畫及資料緩衝區。 配置給執行計畫或資料緩衝區的集區百分比，會依系統的狀態而動態調整。 記憶體集區中用來儲存執行計畫的那一部分，稱為程序快取。

SQL Server 執行計畫具有下列主要元件： 

* 執行計畫：大多數的執行計畫是可重新進入的唯讀資料結構，而且可供任意數目的使用者所使用。 此稱為查詢計畫。 查詢計畫中並不會儲存任何使用者內容。 記憶體中絕不會有超過一或兩個的查詢計畫副本：一個是所有序列執行的副本，另一個則是所有平行執行的副本。 平行副本會涵蓋所有的平行執行，不論其平行處理原則的程度為何。 
* 執行內容：目前執行查詢的每位使用者都具有資料結構，其中保存了與其執行相關的特定資料，例如參數值。 此資料結構即稱為執行內容。 而此執行內容資料結構將會重複使用。 如果使用者執行查詢，而且其中有一個結構不在使用中，則系統會根據新使用者的內容來重新初始化該結構。 

![execution_context](../relational-databases/media/execution-context.gif)

在 SQL Server 中執行任何 SQL 陳述式時，關聯式引擎會先尋找整個程序快取，以確認相同 SQL 陳述式的現有執行計畫是否存在。 如果 SQL Server 找到任何現有的計畫，就會重複使用它，如此可省下重新編譯 SQL 陳述式的負擔。 如果沒有現有的執行計畫，SQL Server 會為查詢產生新的執行計畫。

SQL Server 有一個非常有效率的演算法，可為任何特定 SQL 陳述式尋找任何現有的執行計畫。 在大部分的系統中，這個掃描所使用的最少資源，比能夠重複使用現有計畫來取代編譯每個 SQL 陳述式所節省下來的資源還少。

此演算法若要能使得新的 SQL 陳述式符合快取中現有、未使用的執行計畫，所有的物件參考必須是完整的。 例如，這些 `SELECT` 陳述式的第一個不符合現有計畫，而第二個則符合：

```
SELECT * FROM Person;

SELECT * FROM Person.Person;
```

### <a name="removing-execution-plans-from-the-procedure-cache"></a>從程序快取中移除執行計畫

只要記憶體足以存放執行計畫，執行計畫就會保留在程序快取中。 當記憶體壓力存在時，Database Engine 就會使用以成本為基礎的方法，來判斷要從程序快取中移除哪些執行計畫。 為了進行以成本為基礎的決策，Database Engine 會根據下列因素，針對每個執行計畫增加和減少目前的成本變數。

當使用者處理序將執行計畫插入快取時，該使用者處理序會將目前的成本設定為等於原始查詢編譯成本。若為特定執行計畫，使用者處理序則會將目前成本設定為零。 因此，每當使用者程序參考執行計畫時，它都會將目前成本重設為原始編譯成本；如果是特定執行計畫，使用者程序會增加目前成本。 對於所有計畫而言，目前成本的最大值就是原始編譯成本。

當記憶體壓力存在時，Database Engine 會從程序快取中移除執行計畫，藉此進行回應。 為了判斷要移除哪些計畫，Database Engine 會重複檢查每個執行計畫的狀態，然後移除目前成本為零的計畫。 當記憶體壓力存在時，系統不會自動移除目前成本為零的執行計畫。只有當 Database Engine 檢查計畫並發現目前成本為零時，才會移除此計畫。 檢查執行計畫時，如果查詢目前未使用該計畫，Database Engine 就會減少目前成本，藉此將目前成本推向零。

Database Engine 會重複檢查執行計畫，直到移除足夠的計畫，可滿足記憶體需求為止。 當記憶體壓力存在時，執行計畫可能會多次增加和減少其成本。 當記憶體壓力不再存在時，Database Engine 就會停止減少未使用之執行計畫的目前成本，而所有執行計畫都會保留在程序快取中，即使其成本為零也一樣。

為了回應記憶體壓力，Database Engine 會使用資源監視器和使用者執行緒來釋放程序快取中的記憶體。 資源監視器和使用者執行緒可以檢查計畫並同時執行，以便針對每個未使用的執行計畫減少目前成本。 當全域記憶體壓力存在時，資源監視器就會從程序快取中移除執行計畫。 它會釋放記憶體，以便強制執行系統記憶體、處理序記憶體、資源集區記憶體和所有快取大小上限的原則。 

所有快取大小上限是緩衝集區大小的函數，而且不能超過伺服器記憶體的最大值。 如需設定最大伺服器記憶體的詳細資訊，請參閱 `sp_configure` 中的 `max server memory` 設定。 

當單一快取記憶體壓力存在時，使用者執行緒就會從程序快取中移除執行計畫。 它們會強制執行最大單一快取大小和最大單一快取項目的原則。 

下列範例說明要從程序快取中移除哪些執行計畫：

* 執行計畫經常被參考，所以它的成本永遠都不會變成零。 計畫依然在程序快取中，而且除非有記憶體壓力且目前成本為零，否則不會移除計畫。
* 系統會插入特定執行計畫，但在記憶體壓力存在之前，不會再次參考它。 由於特定計畫會以目前成本為零來初始化，所以當資料庫引擎檢查執行計畫時，它將會看到目前成本為零，並從程序快取中移除此計畫。 當記憶體壓力不存在時，特定執行計畫會留在程序快取中，且目前成本為零。


若要手動從快取中移除單一計畫或所有計畫，請使用 [DBCC FREEPROCCACHE](../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md)。

### <a name="recompiling-execution-plans"></a>重新編譯執行計畫

資料庫的特定變更可能會導致執行計畫沒有效率或無效，端視資料庫的新狀態而定。 SQL Server 會偵測讓執行計畫失效的變更並將該計畫標示為無效。 然後系統會根據執行查詢的下一個連接，重新編譯新的計畫。 會使計畫無效的狀況包括： 

* 對查詢所參考之資料表或檢視表所做的變更 (`ALTER TABLE` 和 `ALTER VIEW`)。
* 對單一程序所做的變更，此程序會從快取中卸除該程序的所有計畫 (`ALTER PROCEDURE`)。
* 對執行計畫所使用之任何索引所做的變更。
* 對執行計畫所使用之統計資料的更新，這些更新是由 `UPDATE STATISTICS` 之類的陳述式明確產生或自動產生的。
* 卸除執行計畫所使用的索引。
* 明確呼叫 `sp_recompile`。
* 對索引鍵所做的大量變更 (由 `INSERT` 或 `DELETE` 陳述式所產生，而這類陳述式是來自其他修改查詢所參考之資料表的使用者)。
* 對於含有觸發程序的資料表，是指插入或刪除資料表中的資料列數目有顯著增加的情況。
* 使用 `WITH RECOMPILE` 選項執行預存程序。

不管是為了讓陳述式正確或是要取得可能更快的查詢執行計畫，多數的重新編譯都是必要的。

在 SQL Server 2000 中，每當批次內的陳述式導致重新編譯時，無論是透過預存程序、觸發程序、特定批次或準備陳述式所送出，都會重新編譯整個批次。 在 SQL Server 2005 和更新版本中，只會重新編譯批次內導致重新編譯的陳述式。 因為這項差異，故無法比較 SQL Server 2000 及更新版本中的重新編譯計數。 此外，SQL Server 2005 和更新版本已擴充功能集，因此具有更多種重新編譯類型。

陳述式層級的重新編譯有益於效能，因為在大部分情況下，只有少量的陳述式會導致重新編譯並造成相關負面影響，也就是 CPU 時間及鎖定。 批次中不必重新編譯的其他陳述式則可避免這些負面影響。

SQL Server Profiler 的 `SP:Recompile` 追蹤事件會報告陳述式層級的重新編譯。 此追蹤事件只會報告 SQL Server 2000 中的批次重新編譯。 不僅如此，還會在此事件的 `TextData` 資料行中填入資料。 因此，在 SQL Server 2000 中必須追蹤 `SP:StmtStarting` 或 `SP:StmtCompleted`，以取得導致重新編譯之 Transact-SQL 文字的作法，現在已不再需要。

`SQL:StmtRecompile` 追蹤事件會報告陳述式層級的重新編譯。 此追蹤事件可以用來追蹤及偵錯重新編譯。 `SP:Recompile` 只能針對預存程序及觸發程序來產生；相較之下，`SQL:StmtRecompile` 可針對預存程序、觸發程序、特定批次、使用 `sp_executesql` 執行的批次、準備查詢及動態 SQL 來產生。

`SP:Recompile` 和 `SQL:StmtRecompile` 的 `EventSubClass` 資料行包含一個整數碼，可指出重新編譯的原因。 下表列出每一個代碼的意義。

|EventSubClass 值    |Description    |
|----|----|
|1  |結構描述已變更。    |
|2  |統計資料已變更。    |
|3  |延遲編譯。  |
|4  |SET 選項已變更。    |
|5  |暫存資料表已變更。   |
|6  |遠端資料列集已變更。 |
|7  |`FOR BROWSE` 權限已變更。   |
|8  |查詢通知環境已變更。    |
|9  |資料分割檢視已變更。  |
|10 |資料指標選項已變更。    |
|11 |`OPTION (RECOMPILE)` 要求的 |

> [!NOTE]
> 當 `AUTO_UPDATE_STATISTICS` 資料庫選項 `SET` 為 `ON` 時，若其目標資料表或索引檢視表的統計值或基數明顯和上次執行不同時，就會重新編譯查詢。 此行為適用於標準使用者定義的資料表、暫存資料表，以及 DML 觸發程序所建立的插入和刪除資料表。 如果過多的重新編譯影響了查詢效能，請考慮將此設定值變更為 `OFF`。 當 `AUTO_UPDATE_STATISTICS` 資料庫選項 `SET` 為 `OFF` 時，就不會基於統計資料或基數變更發生重新編譯，但 DML `INSTEAD OF` 觸發程序所建立的插入和刪除資料表例外。 因為這些資料表是在 tempdb 中建立的，所以存取它們的查詢是否要重新編譯，取決於 tempdb 中 `AUTO_UPDATE_STATISTICS` 的設定。 請注意，在 SQL Server 2000 中，即使此設定為 `OFF`，還是會繼續根據 DML 觸發程序之插入和刪除資料表的基數變更來重新編譯查詢。
 

### <a name="parameters-and-execution-plan-reuse"></a>參數和執行計畫的重複使用

參數的使用，包括 ADO、OLE DB、和 ODBC 應用程式中的參數標記，可以增加執行計畫的重複使用。

> [!WARNING] 
> 相較於將值串連到字串，然後使用資料存取 API 方法、`EXECUTE` 陳述式或 `sp_executesql` 預存程序來執行該字串，比較安全的方式是使用參數或參數標記來保留使用者輸入的值。
 
下列這兩個 `SELECT` 陳述式的唯一差異在於 `WHERE` 子句中所比較的值：

```
SELECT * 
FROM AdventureWorks2014.Production.Product 
WHERE ProductSubcategoryID = 1;
```
```
SELECT * 
FROM AdventureWorks2014.Production.Product 
WHERE ProductSubcategoryID = 4;
```

這些查詢執行計畫間的唯一差異是用來比較 `ProductSubcategoryID` 資料行所儲存的值。 雖然目標是要讓 SQL Server 能一直意識到陳述式基本上產生的都是相同計畫並重複使用這些計畫，但有時 SQL Server 並不會在複雜的 SQL 陳述式中偵測到這種情況。

利用參數將 SQL 陳述式中的常數分離出來，可以幫助關聯式引擎識別重複的計畫。 您可以使用以下方式來使用參數： 

* 在 Transact-SQL 中，使用 `sp_executesql`： 

   ```
   DECLARE @MyIntParm INT
   SET @MyIntParm = 1
   EXEC sp_executesql
     N'SELECT * 
     FROM AdventureWorks2014.Production.Product 
     WHERE ProductSubcategoryID = @Parm',
     N'@Parm INT',
     @MyIntParm
   ```

   建議針對 Transact-SQL 指令碼、預存程序或動態產生 SQL 陳述式的觸發程序使用此方法。 


* ADO、OLE DB、和 ODBC 使用參數標記。 參數標記是取代 SQL 陳述式中常數的問號 (?)，這些標記將繫結至程式變數。 例如，您可以在 ODBC 應用程式中執行下列動作： 

   * 使用 `SQLBindParameter`，將整數變數繫結到 SQL 陳述式中的第一個參數標記。
   * 在變數中放入整數值。
   * 執行陳述式，指定參數標記 (?)： 

   ```
   SQLExecDirect(hstmt, 
     "SELECT * 
     FROM AdventureWorks2014.Production.Product 
     WHERE ProductSubcategoryID = ?",
     SQL_NTS);
   ```

   在應用程式中使用參數標記時，SQL Server 所包含的 SQL Server Native Client OLE DB 提供者和 SQL Server Native Client ODBC 驅動程式，都會使用 `sp_executesql`，將陳述式傳送至 SQL Server。 

* 設計預存程序，按設計來使用參數。

如果您未明確在應用程式設計中建置參數，也可以仰賴 SQL Server 查詢最佳化工具，利用簡單參數化的預設行為，自動將特定查詢參數化。 另外，您也可以強制查詢最佳化工具考慮將資料庫中的所有查詢參數化，方式是將 `ALTER DATABASE` 陳述式的 `PARAMETERIZATION` 選項設為 `FORCED`。

啟用強制參數化之後，仍會發生簡單參數化。 例如，根據強制參數化的規則，下列查詢無法參數化：

```
SELECT * FROM Person.Address
WHERE AddressID = 1 + 2;
```

不過，可根據簡單參數化規則將它參數化。 如果強制參數化嘗試失敗，後續仍會嘗試簡單參數化。

### <a name="simple-parameterization"></a>簡單參數化

在 SQL Server 的 Transact-SQL 陳述式中使用參數或參數標記時，可以提升關聯式引擎將新的 SQL 陳述式與先前編譯之現有執行計畫配對的能力。

> [!WARNING] 
> 相較於將值串連到字串，然後使用資料存取 API 方法、`EXECUTE` 陳述式或 `sp_executesql` 預存程序來執行該字串，比較安全的方式是使用參數或參數標記來保留使用者輸入的值。

如果在不使用參數的情況下執行 SQL 陳述式，SQL Server 就會在內部將此陳述式參數化，以增加它與現有執行計畫配對的可能性。 此處理序即稱為簡單參數化。 在 SQL Server 2000 中，此處理序就是指自動參數化。

請參考這個陳述式：

```
SELECT * FROM AdventureWorks2014.Production.Product 
WHERE ProductSubcategoryID = 1;
```

在陳述式尾端的數值 1，可以指定成參數。 關聯式引擎會建立此批次的執行計畫，就像已經指定參數來取代值 1 一樣。 由於這個簡單參數化的緣故，SQL Server 可辨識下列兩個陳述式基本上會產生相同的執行計畫，並重複使用第二個陳述式的第一個計畫：

```
SELECT * FROM AdventureWorks2014.Production.Product 
WHERE ProductSubcategoryID = 1;
```
```
SELECT * FROM AdventureWorks2014.Production.Product 
WHERE ProductSubcategoryID = 4;
```

在處理複雜的 SQL 陳述式時，關聯式引擎可能會無法判斷哪個運算式可以參數化。 若要提升關聯式引擎將複雜 SQL 陳述式與現有、未使用之執行計畫配對的能力，請使用 sp_executesql 或參數標記明確指定參數。 

> [!NOTE]
> 使用 +、-、*、/ 或 % 等算術運算子來將 int、smallint、tinyint 或 bigint 常數值隱含或明確轉換為 float、real、decimal 或 numeric 資料類型時，SQL Server 會套用特定的規則來計算運算式結果的類型與有效位數。 不過，這些規則會隨著查詢是否參數化而有所不同。 因此，在某些情況下，查詢中類似的運算式可能會產生不同的結果。

在簡單參數化的預設行為下，SQL Server 可將相對較小的查詢類別參數化。 不過，您可以藉由將 `ALTER DATABASE` 命令的 `PARAMETERIZATION` 選項設為 `FORCED`，來指定資料庫中所有查詢都會依據特定限制進行參數化。 這麼做可降低查詢編譯的頻率，進而改善經歷大量並行查詢的資料庫效能。

此外，您可以指定單一查詢，以及任何其他語法相同但唯有參數值不同的查詢，使其進行參數化。 


### <a name="forced-parameterization"></a>強制參數化

您可以藉由指定將資料庫中所有的 `SELECT`、`INSERT`、`UPDATE` 及 `DELETE` 陳述式依據特定限制進行參數化，以覆寫 SQL Server 預設的簡單參數化行為。 您可以藉由將 `ALTER DATABASE` 陳述式中的 `PARAMETERIZATION` 選項設為 `FORCED`，來啟用強制參數化。 強制參數化可藉由降低查詢編譯與重新編譯的頻率，來增進特定資料庫的效能。 可經由強制參數化獲益的資料庫通常會有來自來源 (如銷售點應用程式) 的大量並行查詢。

將 `PARAMETERIZATION` 選項設為 `FORCED` 時，出現在 `SELECT`、`INSERT`、`UPDATE` 或 `DELETE` 陳述式中且以任何形式提交的所有常值，都會在查詢編譯期間轉換為參數。 但出現於下列查詢結構中的常值則為例外： 

* `INSERT...EXECUTE` 陳述式。
* 位於預存程序、觸發程序或使用者自訂函數主體中的陳述式。 SQL Server 已經會重複使用這些常式的查詢計畫。
* 已在用戶端應用程式上完成參數化的準備陳述式。
* 含有 XQuery 方法呼叫的陳述式，其方法會出現在引數通常已參數化的內容中，如 `WHERE` 子句。 若此方法出現在引數未參數化的內容中，則該陳述式的其他部分會進行參數化。
* 位於 Transact-SQL 資料指標內的陳述式 (API 資料指標內的 `SELECT` 陳述式會進行參數化)。
* 被取代的查詢結構。
* 將在 `ANSI_PADDING` 或 `ANSI_NULLS` 內容中執行的任何陳述式設為 `OFF`。
* 包含超過 2,097 個可參數化之常值的陳述式。
* 參考變數的陳述式，如 `WHERE T.col2 >= @bb`。
* 含有 `RECOMPILE` 查詢提示的陳述式。
* 含有 `COMPUTE` 子句的陳述式。
* 含有 `WHERE CURRENT OF` 子句的陳述式。

另外，下列查詢子句不參數化。 請注意，在這些案例中，只有子句不參數化。 相同查詢內的其他子句可進行強制參數化。

* 任何 `SELECT` 陳述式的 <select_list>。 這包括子查詢的 `SELECT` 清單和 `INSERT` 陳述式內的 `SELECT` 清單。
* 出現在 `IF` 陳述式內的子查詢 `SELECT` 陳述式。
* 查詢的 `TOP`、`TABLESAMPLE`、`HAVING`、`GROUP BY`、`ORDER BY`、`OUTPUT...INTO` 或 `FOR XM`L 子句。
* 傳送至 `OPENROWSET`、`OPENQUERY`、`OPENDATASOURCE`、`OPENXML` 或任何 `FULLTEXT` 運算子的引數 (直接或做為子運算式)。
* `LIKE` 子句的 pattern 和 escape_character 引數。
* `CONVERT` 子句的 style 引數。
* `IDENTITY` 子句中的整數常數。
* 使用 ODBC 延伸語法指定的常數。
* 可摺疊常數的運算式，其為 +、-、*、/ 及 % 運算子的引數。 考量是否可進行強制參數化時，若符合下列其中一項條件，SQL Server 就會認定運算式為可摺疊常數的：  
  * 運算式中未出現資料行、變數或子查詢。  
  * 運算式包含 `CASE` 子句。  
* 查詢提示子句的引數。 這些包括 `FAST` 查詢提示的 `number_of_rows` 引數、`MAXDOP` 查詢提示的 `number_of_processors` 引數，以及 `MAXRECURSION` 查詢提示的 number 引數。


參數化會發生在個別 Transact-SQL 陳述式層級上。 換句話說，批次中的個別陳述式會進行參數化。 編譯之後，參數化查詢會在最初提交查詢的批次內容中執行。 若已快取查詢的執行計畫，即可藉由參考 sys.syscacheobjects 動態管理檢視表的 sql 資料行，來判斷查詢是否已參數化。 若查詢已參數化，則此資料行中參數的名稱與資料類型會顯示在提交批次的文字之前，如 (@1 tinyint)。

> [!NOTE]
> 參數名稱可以是任意的名稱。 使用者或應用程式不應依賴特定的命名順序。 而且，可以在 SQL Server 版本和 Service Pack 升級之間變更下列各項：參數名稱、已參數化的常值選項，以及參數化文字的間距。
 
#### <a name="data-types-of-parameters"></a>參數的資料類型

當 SQL Server 將常值參數化時，參數會轉換為下列資料類型：

* 將以其他方式調整大小以符合 int 資料類型的整數常值會參數化為 int。 屬於含有任何比較運算子之述詞的較大整數常值 (包括 <、\<=、=、!=、>、>=,、!\<、!>、<>、`ALL`、`ANY`、`SOME`、`BETWEEN` 和 `IN`) 會參數化為 numeric(38,0)。 不屬於含有比較運算子之述詞的較大常值會參數化為 numeric，其有效位數夠大正好足以支援其大小，而其小數位數為 0。
* 屬於含有比較運算子之述詞的固定點數值常值會參數化為 numeric，其有效位數為 38，而其小數位數夠大正好足以支援其大小。 不屬於含有比較運算子之述詞的固定點數值常值會參數化為 numeric，其有效位數與小數位數夠大正好足以支援其大小。
* 浮點數值常值會參數化為 float(53)。
* 如果非 Unicode 字串常值可容納於 8,000 個字元中，即會參數化為 varchar(8000)，如果該常值大於 8,000 個字元，則會參數化為 varchar(max)。
* 如果 Unicode 字串常值可容納於 4,000 個 Unicode 字元中，即會參數化為 nvarchar(4000)，如果該常值大於 4,000 個字元，則會參數化為 nvarchar(max)。
* 如果二進位常值可容納於 8,000 個位元組中，就會參數化為 varbinary(8000)。 如果該常值大於 8,000 個位元組，就會轉換為 varbinary(max)。
* Money 類型常值會參數化為 money。

#### <a name="guidelines-for-using-forced-parameterization"></a>使用強制參數化的指導方針

將 `PARAMETERIZATION` 選項設為 FORCED 時，請考量下列事項：

* 強制參數化一旦生效後，會在編譯查詢時將查詢中的常值 (常數) 變更為參數。 因此，查詢最佳化工具可能會選擇到次佳的查詢計畫。 特別是，查詢最佳化工具較不可能比對查詢與索引檢視或計算資料行上的索引。 它也可會為資料分割資料表與分散式資料分割檢視上的查詢選擇次佳的計畫。 針對非常依賴索引檢視或計算資料行上索引的環境，就不應該使用強制參數化。 一般而言，應由具有經驗的資料庫管理員判斷 `PARAMETERIZATION FORCED` 選項的執行不會對效能造成不良影響後，才能使用此選項。
* 只要在查詢執行之內容所屬的資料庫中，將 `PARAMETERIZATION` 選項設為 `FORCED`，參考多個資料庫的分散式查詢即能使用強制參數化。
* 將 `PARAMETERIZATION` 選項設為 `FORCED`，就會從資料庫的計畫快取中排清所有查詢計畫，但目前正在編譯、重新編譯或執行的計畫除外。 在設定變更期間編譯或執行的查詢計畫，會在下次執行查詢時進行參數化。
* 設定 `PARAMETERIZATION` 選項是不需要資料庫層級獨佔鎖定的線上作業。
* 重新附加或還原資料庫時，會保留 `PARAMETERIZATION` 選項目前的設定。

您可以指定在單一查詢以及語法上相同但只有其參數值不同的查詢嘗試簡單參數化，以覆寫強制參數化的行為。 反之，您可以指定只在一組語法相同的查詢嘗試強制參數化，即使資料庫中已停用強制參數化。 此即為[計畫指南](../relational-databases/performance/plan-guides.md)的用途。

> [!NOTE]
> 將 `PARAMETERIZATION` 選項設為 `FORCED` 時，錯誤訊息的報告可能與簡單參數化的報告不同：當簡單參數化下報告的訊息較少時，可能會報告多個錯誤訊息，而且發生錯誤的行號報告可能不正確。
 

### <a name="preparing-sql-statements"></a>準備 SQL 陳述式

SQL Server 關聯式引擎在執行 SQL 陳述式之前，會先導入準備陳述式的完整支援。 如果應用程式需要執行 SQL 陳述式數次，它可以使用資料庫 API 來執行下列動作： 

* 準備一次陳述式。 這可將 SQL 陳述式編譯成執行計畫。
* 在每次需要執行陳述式時，執行先行編譯的執行計畫。 這樣就不必在第一次之後的每一次執行時重新編譯 SQL 陳述式。   
  準備和執行陳述式是由 API 函數和方法所控制。 它不是 Transact-SQL 語言的一部分。 SQL Server Native Client OLE DB 提供者和 SQL Server Native Client ODBC 驅動程式支援執行 SQL 陳述式的準備/執行模型。 在準備要求中，提供者或驅動程式可搭配準備陳述式的要求來將陳述式傳送到 SQL Server。 SQL Server 會編譯執行計畫，並將該計畫的控制代碼傳回給提供者或驅動程式。 當產生執行要求時，提供者或驅動程式會將要求傳給伺服器，以執行與控制代碼相關聯的計畫。 


準備陳述式無法用來在 SQL Server 上建立暫存物件。 準備陳述式也無法參考可建立暫存物件 (如暫存資料表) 的系統預存程序。 這些程序必須直接執行。

過度使用準備/執行模型會降低效能。 如果陳述式只執行一次，則直接執行只需要一次網路往返到伺服器。 如果先準備再執行只執行一次的 SQL 陳述式，便需要多一次網路往返：一次用來準備陳述式，一次用來執行陳述式。

如果使用參數標記，則準備陳述式會更有效率。 例如，假設應用程式偶爾會被要求從 `AdventureWorks` 範例資料庫擷取產品資訊。 應用程式有兩種方式可以達成此目的。 

使用第一種方式，應用程式可以針對所要求的每個產品執行不同的查詢。

```
SELECT * FROM AdventureWorks2014.Production.Product
WHERE ProductID = 63;
```

使用第二種方式，應用程式會執行下列動作： 

1. 準備含有參數標記 (?) 的陳述式：  
   ```
   SELECT * FROM AdventureWorks2014.Production.Product  
   WHERE ProductID = ?;
   ```
2. 繫結程式變數與參數標記。
3. 每次需要產品資訊時，以索引鍵值填入繫結變數，然後執行陳述式。


如果陳述式執行超過三次以上，則使用第二種方式會比較有效率。

在 SQL Server 中，由於 SQL Server 重複使用執行計畫的方式，讓準備/執行模型相較於直接執行並無任何顯著的優勢。 SQL Server 可提供有效率的演算法，來配對目前的 SQL 陳述式以及先前產生用來執行相同 SQL 陳述式的執行計畫。 如果應用程式多次執行具有參數標記的 SQL 陳述式，則 SQL Server 將自第一次執行之後，在第二次及後續執行中重複使用執行計畫 (除非程序快取中的計畫過期)。 但準備/執行模型仍然具有以下優點： 

* 利用識別代碼來尋找執行計畫，比用演算法來使 SQL 陳述式與現有執行計畫相符更具效率。
* 應用程式可以控制何時建立及重複使用執行計畫。
* 準備/執行模型可以移至其他資料庫使用，包括舊版的 SQL Server。



## <a name="parallel-query-processing"></a>平行查詢處理

SQL Server 提供平行查詢，讓擁有多個處理器 (CPU) 的電腦也能獲得最佳的查詢執行和索引作業。 因為 SQL Server 可利用數個作業系統執行緒平行執行查詢或索引作業，所以可快速且有效率地完成作業。

在查詢最佳化期間，SQL Server 會搜尋可能受益於平行執行的查詢或索引作業。 對於這些查詢，SQL Server 會在查詢執行計畫中插入交換運算子，以準備平行執行的查詢。 所謂的交換運算子，是指查詢執行計畫中，提供存取管理、資料重新散佈以及流量控制的運算子。 交換運算子包括當做子類型的 `Distribute Streams`、`Repartition Streams` 及 `Gather Streams` 邏輯運算子，其中的一或多個可以出現在平行查詢之查詢計畫的執行程序表輸出中。 

插入交換運算子之後，結果便是平行查詢執行計畫。 平行查詢執行計畫可以使用一個以上的執行緒。 非平行查詢所使用的序列執行計畫，執行時只會使用一個執行緒。 平行查詢實際所使用的執行緒數目，是在查詢計畫執行初始化時，由計畫的複雜度與平行處理原則的程度決定。 平行處理原則的程度決定將要使用的 CPU 最大數目，而不是將要使用的執行緒數目。 平行處理原則的程度值是在伺服器層級設定的，可以使用 sp_configure 系統預存程序來修改。 您可以指定 `MAXDOP` 查詢提示或 `MAXDOP` 索引選項，來覆寫個別查詢或索引陳述式的這個值。 

如果符合下列任一個條件，SQL Server 查詢最佳化工具就不會使用平行執行計畫進行查詢：

* 查詢的序列執行成本不夠高，無法考量替代平行執行計畫。 
* 序列執行計畫被認為比特定查詢之任何可能的平行執行計畫更快。
* 此查詢包含無法平行執行的純量或關聯式運算子。 特定運算子可能造成查詢計畫的一個區段以序列模式執行，或整個計畫以序列模式執行。


### <a name="degree-of-parallelism"></a>平行處理原則的程度

SQL Server 會針對平行查詢執行或索引資料定義語言 (DDL) 作業的每一個執行個體，自動偵測平行處理原則的最佳程度。 其作法是依據下列條件： 

1. SQL Server 是否正在具有多個微處理器或 CPU 的電腦上執行，例如對稱式多處理的電腦 (SMP)。  
  具有一個以上 CPU 的電腦，才能使用平行查詢。 

2. 是否有足夠的執行緒可用。  
  每一個查詢或索引作業都需要某個數目的執行緒來執行。 執行平行計畫所需的執行緒會比執行序列計畫還多，而且所需的執行緒數目會隨著平行處理原則的程度增加。 無法滿足適用於平行處理原則之特定程度的平行計畫執行緒需求時，Database Engine 就會自動降低平行處理原則的程度，或是完全放棄指定工作負載內容中的平行計畫。 然後，它會執行序列計畫 (一個執行緒)。 

3. 已執行的查詢或索引作業類型。  
  建立或重建索引，或是卸除叢集索引的索引作業，以及大量使用 CPU 循環的查詢，最適合使用平行計畫。 例如，聯結大型資料表、大型彙總及排序大型結果集，皆適用於平行計畫。 經常在交易處理應用程式中發現的簡單查詢，會尋找執行平行查詢時所需的其他協調作業，此平行查詢比潛在的效能提升更為重要。 為了區分能否從平行處理原則中獲益的查詢，Database Engine 會比較執行查詢或索引作業的預估成本與[平行處理原則的成本臨界值](../database-engine/configure-windows/configure-the-cost-threshold-for-parallelism-server-configuration-option.md)。 雖然不建議這麼做，但使用者可以使用 [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) 來變更預設值 5。 

4. 要處理的資料列數目是否足夠。  
  如果查詢最佳化工具判定資料列數目太少，則它不會引進交換運算子來散發資料列。 因此，運算子會循序執行。 在序列計畫中執行運算子，可避免啟動、散發、協調成本超過執行平行運算子所獲得的利益時的案例。

5. 目前是否有可用的散發統計資料。  
  如果無法使用平行處理原則的最高程度，則在放棄平行計畫前，會先考慮降低程度。  
  例如，當您在檢視中建立叢集索引時，因為叢集索引尚未存在，所以無法評估散發統計資料。 在此情況下，Database Engine 無法為索引作業提供平行處理原則的最高程度。 然而，有些運算子 (如排序及掃描) 仍可從平行執行獲益。

> [!NOTE]
> 只有 SQL Server Enterprise、Developer 和 Evaluation 版本才可使用平行索引作業。
 
Database Engine 會在執行期間，判斷目前系統工作負載和先前描述的組態資訊是否允許平行執行。 如果保證可平行執行，則 Database Engine 會判斷最佳的執行緒數目，並將平行計畫的執行分散到這些執行緒上。 當查詢或索引作業開始在多個執行緒上執行，以進行平行執行時，則在完成作業之前，都會使用相同數目的執行緒。 每次從程序快取中擷取執行計畫時，Database Engine 都會重新檢查最佳的執行緒決策數目。 例如，執行查詢可能會使用到序列計畫，稍後執行同一個查詢會導致平行計畫使用三個執行緒，而第三次執行查詢的結果則是平行計畫使用四個執行緒。

在平行查詢執行計畫中，會循序執行插入、更新及刪除運算子。 然而，UPDATE 或 DELETE 陳述式的 WHERE 子句，或 INSERT 陳述式的 SELECT 部份，可能會以平行方式執行。 真正的資料變更隨即會循序套用到資料庫。

靜態和索引鍵集衍生的資料指標可以利用平行執行計畫來擴展。 但是，動態資料指標的行為僅能由序列執行來提供。 而最佳化工具所產生的查詢序列執行計畫，一定是動態資料指標的一部份。

#### <a name="overriding-degrees-of-parallelism"></a>覆寫平行處理原則的程度

您可以使用[平行處理原則的最大程度](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)伺服器組態選項 ([!INCLUDE[ssSDS_md](../includes/sssds-md.md)][ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md))，來限制要在平行計畫執行中使用的處理器數目。 對於個別查詢及索引作業陳述式，可以指定 MAXDOP 查詢提示或 MAXDOP 索引選項，來覆寫 [平行處理原則的最大程度] 選項。 MAXDOP 所提供的控制會比個別的查詢及索引作業還多。 例如，您可以使用 MAXDOP 選項，利用增加或減少，來控制線上索引作業專用的處理器數目。 如此一來，您就可以平衡索引作業所使用的資源及並行使用者的資源。 將 [平行處理原則的最大程度] 選項設定為 0，可讓 SQL Server 在平行計畫執行中使用所有可用的處理器 (最大值為 64 個處理器)。 針對查詢或索引將 MAXDOP 設定為 0，讓 SQL Server 可針對平行計畫執行中指定的查詢或索引使用所有可用的處理器 (最大值為 64 個處理器)。


### <a name="parallel-query-example"></a>平行查詢範例

下列查詢會計算從 2000 年 4 月 1 日起，某一季之內所下的訂單數量，而這一季的訂單中，至少有一項產品晚於交付日期才送達客戶。 這個查詢會列出這類的訂單數量，並依訂單的優先順序分組，然後以遞增的優先順序排序訂單。 

這個範例使用假設性的資料表和資料行名稱。

```
SELECT o_orderpriority, COUNT(*) AS Order_Count
FROM orders
WHERE o_orderdate >= '2000/04/01'
   AND o_orderdate < DATEADD (mm, 3, '2000/04/01')
   AND EXISTS
         (
          SELECT *
            FROM    lineitem
            WHERE l_orderkey = o_orderkey
               AND l_commitdate < l_receiptdate
         )
   GROUP BY o_orderpriority
   ORDER BY o_orderpriority
```

假設下列索引定義於 lineitem 和 orders 資料表上：

```
CREATE INDEX l_order_dates_idx 
   ON lineitem
      (l_orderkey, l_receiptdate, l_commitdate, l_shipdate)

CREATE UNIQUE INDEX o_datkeyopr_idx
   ON ORDERS
      (o_orderdate, o_orderkey, o_custkey, o_orderpriority)
```

這是針對之前查詢所產生的可能平行計畫：

```
|--Stream Aggregate(GROUP BY:([ORDERS].[o_orderpriority])
                  DEFINE:([Expr1005]=COUNT(*)))
    |--Parallelism(Gather Streams, ORDER BY:
                  ([ORDERS].[o_orderpriority] ASC))
         |--Stream Aggregate(GROUP BY:
                  ([ORDERS].[o_orderpriority])
                  DEFINE:([Expr1005]=Count(*)))
              |--Sort(ORDER BY:([ORDERS].[o_orderpriority] ASC))
                   |--Merge Join(Left Semi Join, MERGE:
                  ([ORDERS].[o_orderkey])=
                        ([LINEITEM].[l_orderkey]),
                  RESIDUAL:([ORDERS].[o_orderkey]=
                        [LINEITEM].[l_orderkey]))
                        |--Sort(ORDER BY:([ORDERS].[o_orderkey] ASC))
                        |    |--Parallelism(Repartition Streams,
                           PARTITION COLUMNS:
                           ([ORDERS].[o_orderkey]))
                        |         |--Index Seek(OBJECT:
                     ([tpcd1G].[dbo].[ORDERS].[O_DATKEYOPR_IDX]),
                     SEEK:([ORDERS].[o_orderdate] >=
                           Apr  1 2000 12:00AM AND
                           [ORDERS].[o_orderdate] <
                           Jul  1 2000 12:00AM) ORDERED)
                        |--Parallelism(Repartition Streams,
                     PARTITION COLUMNS:
                     ([LINEITEM].[l_orderkey]),
                     ORDER BY:([LINEITEM].[l_orderkey] ASC))
                             |--Filter(WHERE:
                           ([LINEITEM].[l_commitdate]<
                           [LINEITEM].[l_receiptdate]))
                                  |--Index Scan(OBJECT:
         ([tpcd1G].[dbo].[LINEITEM].[L_ORDER_DATES_IDX]), ORDERED)
```

![parallel_plan](../relational-databases/media/parallel-plan.gif) 使用 DOP 4 的查詢計畫，其中包含兩個資料表的聯結。

上圖所示為使用平行處理原則程度 4 來執行的查詢最佳化工具計畫，包含兩個資料表的聯結。

平行計畫包含三個 `Parallelism` 運算子。 `o_datkey_ptr` 索引的 `Index Seek` 運算子和 `l_order_dates_idx` 索引的 `Index Scan` 運算子會以平行方式執行。 這會產生數個獨佔的資料流。 這可分別從 `Index Scan` 和 `Index Seek` 運算子上方最接近的 Parallelism 運算子來判斷。 兩者都會重新分割交換類型。 也就是說，它們只是將資料流間的資料重新改組，然後依據其輸入的資料流數量產生等量的輸出資料流。 此資料流數量就等於平行處理原則的程度。

位於 `l_order_dates_idx` `Index Scan` 運算子上方的 `Parallelism `運算子會使用 `L_ORDERKEY` 的值做為索引鍵，重新分割其輸入資料流。 利用這種方式，相同的 `L_ORDERKEY` 值也會在相同的輸出資料流中產生相同的結果。 同時，輸出資料流會維持 `L_ORDERKEY` 資料行上的順序，以符合 `Merge Join` 運算子的輸入需求。

位於 `Index Seek` 運算子上方的 `Parallelism`運算子會使用 `O_ORDERKEY` 的值，重新分割其輸入資料流。 因為其輸入未在 `O_ORDERKEY` 資料行值上進行排序，而且此為 `Merge Join` 運算子中的聯結資料行，所以介於 `Parallelism` 與 `Merge Join` 運算子之間的 Sort 運算子，可確保會在聯結資料行上針對 `Merge Join` 運算子為輸入進行排序。 `Sort` 運算子 (如 `Merge Join` 運算子) 會以平行方式執行。

最頂端的 `Parallelism` 運算子會將數個資料流中的結果集合成單一資料流。 由 `Parallelism` 運算子下方 `Stream Aggregate` 運算子所執行的部分彙總，接著會在 `Parallelism` 運算子上方的 `Stream Aggregate` 運算子中，累積為各個不同 `O_ORDERPRIORITY` 值的單一 `SUM` 值。 由於此計畫具有兩個交換區段，且平行處理原則的程度為 4，因此會使用八個執行緒。


### <a name="parallel-index-operations"></a>平行索引作業

為建立或重建索引，或卸除叢集索引的索引作業所內建的查詢計畫，允許在多個微處理器的電腦上進行平行、多執行緒作業。

> [!NOTE]
> 只有 SQL Server 2008 Enterprise 才支援平行索引作業。
 
SQL Server 會使用與其他查詢相同的演算法，來判斷索引作業的平行處理原則程度 (要執行的個別執行緒總數)。 索引作業的平行處理原則最大程度受限於[平行處理原則的最大程度](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)伺服器組態選項。 您可以在 CREATE INDEX、ALTER INDEX、DROP INDEX 和 ALTER TABLE 陳述式中設定 MAXDOP 索引選項，來覆寫個別索引作業的 [平行處理原則的最大程度] 值。

當 Database Engine 建立索引執行計畫時，會將平行作業的數目設定為下列項目中的最低值： 

* 微處理器的數目或電腦中的 CPU 數。
* [平行處理原則的最大程度] 伺服器組態選項中所指定的數目。
* 未超過 SQL Server 執行緒所執行之工作臨界值的 CPU 數目。


例如，電腦上有 8 個 CPU，但 [平行處理原則的最大程度] 設定為 6，則索引作業不會產生超過六個的平行執行緒。 如果在建立索引執行計畫時，電腦中有五個 CPU 已經超過 SQL Server 工作的臨界值，則執行計畫只會指定三個平行執行緒。

平行索引作業的主要階段包含下列項目： 

* 協定執行緒會快速及隨意掃描資料表，以估計索引鍵的散佈。 協調執行緒會建立索引鍵值界限，此界限將建立數個等於平行作業程度的索引鍵值範圍，預期其中的索引鍵值範圍將包含類似數目的資料列。 例如，如果資料表中有四百萬個資料列，而平行處理原則的程度為 4，則協調執行緒會決定將索引鍵值分成四組資料列，且每個資料列都會有一百萬個資料列。 如果無法建立足夠數目的索引鍵範圍以使用所有 CPU，則平行處理原則的程度也會跟著降低。  
* 協調執行緒會分派與平行作業程度相等數目的執行緒，並且等待這些執行緒完成它們的工作。 每個執行緒會使用篩選來掃描基底資料表，並擷取其索引鍵值在執行緒指定範圍中的資料列。 每個執行緒會在其索引鍵值範圍中，建立資料列的索引結構。 在資料分割索引的例子中，每個執行緒都會建立指定數目的資料分割。 執行緒之間不會共用資料分割。  
* 當所有平行執行緒完成後，協調執行緒便會將索引次單元連接到單一索引中。 此階段僅適用於離線索引作業。

個別的 `CREATE TABLE` 或 `ALTER TABLE` 陳述式可以有多個條件約束，來要求建立索引。 這幾個索引建立作業會以序列方式來執行，即使在有多個 CPU 的電腦上，每個個別索引建立作業可能是平行作業。


## <a name="distributted-query-architecture"></a>分散式查詢結構

Microsoft SQL Server 支援兩種可在 Transact-SQL 陳述式中參考異質 OLE DB 資料來源的方法：

* 連結伺服器名稱  
  系統預存程序 `sp_addlinkedserver` 和 `sp_addlinkedsrvlogin` 可用來將伺服器名稱指定至 OLE DB 資料來源。 您可以使用四個部分名稱，在 Transact-SQL 陳述式中參考這些連結伺服器中的物件。 例如，如果 `DeptSQLSrvr` 的連結伺服器名稱是根據 SQL Server 的另一個執行個體所定義，則下列陳述式會參考該伺服器上的資料表： 
  
  ```
  SELECT JobTitle, HireDate 
  FROM DeptSQLSrvr.AdventureWorks2014.HumanResources.Employee;
  ```

   您也可以在 `OPENQUERY` 陳述式中指定連結伺服器名稱，以開啟 OLE DB 資料來源中的資料列集。 然後您就能在 Transact-SQL 陳述式中，像參考資料表一樣參考這個資料列集。 

* 特定連接子名稱  
  對於資料來源的非經常性參考，需要以連接至連結伺服器所需的資訊來指定 `OPENROWSET` 或 `OPENDATASOURCE` 函數。 然後您就能在 Transact-SQL 陳述式中，使用與參考資料表一樣的方式來參考這個資料列集： 
  
  ```
  SELECT *
  FROM OPENROWSET('Microsoft.Jet.OLEDB.4.0',
        'c:\MSOffice\Access\Samples\Northwind.mdb';'Admin';'';
        Employees);
  ```

SQL Server 會使用 OLE DB，在關聯式引擎與儲存引擎間進行通訊。 關聯式引擎會將每個 Transact-SQL 陳述式分解為簡單 OLE DB 資料列集上的一連串作業，而儲存引擎可從基底資料表加以開啟。 這是表示關聯式引擎也可以在任何 OLE DB 資料來源上，開啟簡單的 OLE DB 資料列集。  
![oledb_storage](../relational-databases/media/oledb-storage.gif)  
關聯式引擎使用 OLE DB 應用程式開發介面 (API) 來開啟連結伺服器上的資料列集、提取資料列、以及管理交易。

針對每個可做為連結伺服器存取的 OLE DB 資料來源，在執行 SQL Server 的伺服器上必須存在 OLE DB 提供者。 這組可根據特定 OLE DB 資料來源使用的 Transact-SQL 作業，取決於 OLE DB 提供者的能力。

對於每個 SQL Server 執行個體，`sysadmin` 固定伺服器角色的成員可藉由使用 SQL Server `DisallowAdhocAccess` 屬性來啟用或停用 OLE DB 提供者的特定連接器名稱的使用。 當啟用特定存取時，任何登入到該執行個體的使用者都可以執行包含特定連接子名稱的 SQL 陳述式，該連接子名稱會參考可使用 OLE DB 提供者存取之網路上的任何資料來源。 若要控制資料來源的存取，`sysadmin` 角色的成員可以停用該 OLE DB 提供者的特定存取，進而限制使用者只能存取由系統管理員定義之連結伺服器名稱所參考的資料來源。 預設會針對 SQL Server OLE DB 提供者啟用特定存取，並針對所有其他的 OLE DB 提供者加以停用。

分散式查詢可使用 Microsoft Windows 帳戶 (SQL Server 服務正在其下執行) 的安全性內容，允許使用者存取其他資料來源 (例如，檔案或 Active Directory 等非關聯式資料來源等)。 SQL Server 會適當地模擬 Windows 登入，但無法模擬 SQL Server 登入。 這可能會允許分散式查詢使用者存取他們沒有使用權限的其他資料來源，但執行 SQL Server 服務的帳戶確實擁有權限。 使用 `sp_addlinkedsrvlogin` 來定義已經授權存取對應連結伺服器的特定登入。 ad hoc 名稱無法使用此控制，所以啟用 ad hoc 存取的 OLE DB 提供者時請特別小心。

如果可能，SQL Server 會將關聯式作業 (例如聯結、限制、投影、排序和依作業分組) 推送至 OLE DB 資料來源。 SQL Server 不會預設為將基底資料表掃描到 SQL Server 並自行執行關聯式作業。 SQL Server 會查詢 OLE DB 提供者以判斷它支援的 SQL 語法層級，然後根據該資訊，盡可能推送最多關聯式作業給提供者。 

SQL Server 會為 OLE DB 提供者指定一種可傳回統計資料的機制，以指如何出在 OLE DB 資料來源中散發索引鍵值。 這讓 SQL Server 查詢最佳化工具能根據各個 SQL 陳述式的需求，分析資料來源中的資料模式，並提升查詢最佳化工具產生最佳執行計畫的能力。 


## <a name="query-processing-enhancements-on-partitioned-tables-and-indexes"></a>分割資料表和索引上的查詢處理增強功能

SQL Server 2008 已針對許多平行計畫提升了資料分割資料表上的查詢處理效能、變更了平行計畫和序列計畫的表示方式，以及增強了編譯時間和執行階段執行計畫內所提供的資料分割資訊。 本主題將描述這些改進的功能、提供如何解譯資料分割資料表和索引之查詢執行計畫的指引，以及提供用來改善資料分割物件上之查詢效能的最佳做法。 

> [!NOTE]
> 只有 SQL Server Enterprise、Developer 和 Evaluation 版本才支援資料分割資料表和索引。

### <a name="new-partition-aware-seek-operation"></a>新資料分割感知的搜尋作業

在 SQL Server 中，資料分割資料表的內部表示法已變更。對於查詢處理器而，資料表看起來像是具有以 `PartitionID` 為開頭資料行的多重資料行索引。 `PartitionID` 是經過計算的隱藏資料行，可在內部用來代表包含特定資料列之資料分割的 `ID`。 例如，假設定義為 `T(a, b, c)` 的資料表 T 已在資料行 a 上進行資料分割，而且資料行 b 上具有叢集索引。 在 SQL Server 中，這個資料分割的資料表會在內部視為非資料分割的資料表，而且具有結構描述 `T(PartitionID, a, b, c)` 及複合索引鍵 `(PartitionID, b)` 上的叢集索引。 如此可讓查詢最佳化工具根據任何資料分割資料表或索引上的 `PartitionID` 來執行搜尋作業。 

現在完成了此搜尋作業中的資料分割刪除。

此外，查詢最佳化工具已經過擴充，能讓具有一個條件的搜尋或掃描作業在 `PartitionID` (當做邏輯前端資料行) 上完成，而其他索引鍵資料行及第二層搜尋 (具有另一個條件) 也可能會在一或多個其他資料行上完成 (針對符合第一層搜尋作業資格的每一個相異值)。 也就是說，這個稱為「略過掃描」的作業可讓查詢最佳化工具根據某一個條件來執行搜尋或掃描作業，以判斷要存取的資料分割及該運算子內的第二層索引搜尋作業，以便從符合其他條件的資料分割中傳回資料列。 例如，假設有以下的查詢。

```
SELECT * FROM T WHERE a < 10 and b = 2;
```

在此範例中，假設定義為 `T(a, b, c)` 的資料表 T 已在資料行 a 上進行資料分割，而且資料行 b 上具有叢集索引。 資料表 T 的資料分割界限是由以下資料分割函數所定義：

```
CREATE PARTITION FUNCTION myRangePF1 (int) AS RANGE LEFT FOR VALUES (3, 7, 10);
```

為了解決此查詢，查詢處理器會執行第一層搜尋作業，以尋找包含符合 `T.a < 10` 條件之資料列的每一個資料分割。 這會找出要存取的資料分割。 然後處理器會在每個識別出的資料分割中，於資料行 b 上執行叢集索引內的第二層搜尋，以找出符合 `T.b = 2` 和 `T.a < 10` 條件的資料列。 

下圖為略過掃描作業的邏輯表示法。 此圖顯示資料表 T，其中的資料行 a 和 b 中有資料。 資料分割以 1 到 4 進行編號，並以垂直虛線來顯示資料分割界限。 對資料分割的第一層搜尋作業 (此圖並未顯示) 已判斷出資料分割 1、2 和 3 符合針對資料行 a 上資料表和述詞定義之資料分割所默許的搜尋條件。 也就是說，`T.a < 10`。 略過掃描作業的第二層搜尋部分所周遊的路徑則以曲線表示。 基本上來說，此略過掃描作業會搜尋每一個資料分割，以找出符合 `b = 2` 條件的資料列。 此略過掃描作業的總成本與三個個別索引搜尋的總成本相同。   
![skip_scan](../relational-databases/media/skip-scan.gif)


### <a name="displaying-partitioning-information-in-query-execution-plans"></a>在查詢執行計畫中顯示資料分割資訊

資料分割資料表和索引上的查詢執行計畫可以使用 Transact-SQL `SET` 陳述式 `SET SHOWPLAN_XML` 或 `SET STATISTICS XML`，或是使用 SQL Server Management Studio 中的圖形化執行計畫輸出進行檢查。 例如，您可以在查詢編輯器工具列上，按一下 [顯示估計執行計畫] 來顯示編譯時間執行計畫，以及按一下 [包括實際執行計畫] 來顯示執行階段計畫。 

您可以使用這些工具來確定以下資訊：

* 像是可以存取分割資料表或索引的 `scans`、`seeks`、`inserts`、`updates`、`merges` 和 `deletes` 等作業。
* 查詢所存取的資料分割。 例如，所存取的資料分割總計數和所存取的連續資料分割範圍可以在執行階段執行計畫內使用。
* 當搜尋或掃描作業中使用略過掃描作業來擷取一或多個資料分割中的資料時。

#### <a name="partition-information-enhancements"></a>資料分割資訊增強

SQL Server 同時針對編譯時間和執行階段的執行計畫提供了增強的資料分割資訊。 執行計畫現在會提供下列資訊：

* 選擇性的 `Partitioned` 屬性，其指出在資料分割的資料表上執行像是 `seek`、`scan`、`insert`、`update`、`merge` 或 `delete` 等運算子。  
* 新的 `SeekPredicateNew` 元素搭配 `SeekKeys` 子元素，其中包含 `PartitionID` 做為前置的索引鍵資料行，以及在 `PartitionID` 上指定範圍搜尋的篩選條件。 兩個 `SeekKeys` 子元素的存在表示會使用 `PartitionID` 上的略過掃描作業。   
* 提供所存取之資料分割總計數的摘要資訊。 只有在執行階段計畫中才能使用這項資訊。 

為了示範如何在圖形化執行計畫輸出和 XML 執行程序表輸出中顯示這項資訊，假設資料分割資料表 `fact_sales` 上有以下的查詢。 此查詢會更新兩個資料分割中的資料。 

```
UPDATE fact_sales
SET quantity = quantity * 2
WHERE date_id BETWEEN 20080802 AND 20080902;
```

下圖顯示在此查詢的編譯時間執行計畫內 `Clustered Index Seek` 運算子的屬性。 若要檢視 `fact_sales` 資料表和資料分割的定義，請參閱本主題的＜範例＞。  
![clustered_index_seek](../relational-databases/media/clustered-index-seek.gif)

#### <a name="partitioned-attribute"></a>Partitioned 屬性

在資料分割的資料表或索引上執行類似 `Index Seek` 的運算子時，`Partitioned` 屬性會出現在編譯時間和執行階段的計畫內，而且會設定為 `True` (1)。 當這個屬性設定為 `False` (0) 時，就不會顯示。

`Partitioned` 屬性可出現在下列實體和邏輯運算子內：  
* `Table Scan`  
* `Index Scan`  
* `Index Seek`  
* `Insert`  
* `Update`  
* `Delete`  
* `Merge`  

如同上圖所示，這個屬性 (Attribute) 會顯示在其定義所在之運算子的屬性 (Property) 內。 在 XML 執行程序表輸出中，這個屬性會以 `Partitioned="1"` 的形式出現在其定義所在之運算子的 `RelOp` 節點內。

#### <a name="new-seek-predicate"></a>新的搜尋述詞

在 XML 執行程序表輸出中，`SeekPredicateNew` 元素會出現在其定義所在的運算子內。 它最多可包含兩個 `SeekKeys` 子元素。 第一個 `SeekKeys` 項目會在邏輯索引的資料分割識別碼層級上指定第一層搜尋作業。 也就是說，這個搜尋會判斷為了滿足查詢條件所必須存取的資料分割。 第二個 `SeekKeys` 項目會指定略過掃描作業的第二層搜尋部分，其發生於第一層搜尋中識別出的每一個資料分割內。 

#### <a name="partition-summary-information"></a>資料分割摘要資訊

在執行階段執行計畫中，資料分割摘要資訊提供了所存取之資料分割以及所存取之實際資料分割識別的計數。 您可以使用這項資訊來確認已存取查詢中的正確資料分割，而且所有其他資料分割都不在考量之內。

系統會提供下列資訊：`Actual Partition Count` 和 `Partitions Accessed`。 

`Actual Partition Count` 是查詢所存取的資料分割總數。

`Partitions Accessed` (位於 XML 執行程序表輸出內) 為資料分割摘要資訊，會出現在它定義所在之運算子的 `RelOp` 節點內的新 `RuntimePartitionSummary` 元素中。 下列範例會顯示 `RuntimePartitionSummary` 元素的內容，指出總共會存取兩個資料分割 (資料分割 2 和 3)。
```
<RunTimePartitionSummary>

    <PartitionsAccessed PartitionCount="2" >

        <PartitionRange Start="2" End="3" />

    </PartitionsAccessed>

</RunTimePartitionSummary>
```

#### <a name="displaying-partition-information-by-using-other-showplan-methods"></a>使用其他執行程序表方法來顯示資料分割資訊

執行程序表方法 `SHOWPLAN_ALL`、`SHOWPLAN_TEXT` 和 `STATISTICS PROFILE` 不會報告本主題所述的資料分割資訊，但以下情況例外。 要存取的資料分割 (屬於 `SEEK` 述詞的一部分) 是由表示資料分割識別碼之計算資料行上的範圍述詞所識別。 下列範例會顯示 `Clustered Index Seek` 運算子的 `SEEK` 述詞。 系統會存取資料分割 2 和 3，而且搜尋運算子會篩選符合 `date_id BETWEEN 20080802 AND 20080902` 條件的資料列。
```
|--Clustered Index Seek(OBJECT:([db_sales_test].[dbo].[fact_sales].[ci]), 

        SEEK:([PtnId1000] >= (2) AND [PtnId1000] <= (3) 

                AND [db_sales_test].[dbo].[fact_sales].[date_id] >= (20080802) 

                AND [db_sales_test].[dbo].[fact_sales].[date_id] <= (20080902)) 

                ORDERED FORWARD)
```

#### <a name="interpreting-execution-plans-for-partitioned-heaps"></a>解譯資料分割堆積的執行計畫

資料分割的堆積會被視為資料分割識別碼上的邏輯索引。 資料分割堆積上的資料分割刪除會在執行計畫中表示為`Table Scan`運算子 (在資料分割識別碼上具有 `SEEK` 述詞)。 下列範例會顯示所提供的執行程序表資訊：
```
|-- Table Scan (OBJECT: ([db].[dbo].[T]), SEEK: ([PtnId1001]=[Expr1011]) ORDERED FORWARD)
```

#### <a name="interpreting-execution-plans-for-collocated-joins"></a>解譯共置聯結的執行計畫

當使用相同或相當的資料分割函數來分割兩個資料表，而且聯結兩端的資料分割資料行指定於查詢的聯結條件內時，可能會發生聯結共現。 查詢最佳化工具可以產生一個計畫，好讓每一個資料表中具有相同資料分割識別碼的資料分割都會個別聯結。 共置聯結的速度快於非共置聯結，因為共置聯結所需的記憶體和處理時間比較少。 查詢最佳化工具會根據成本估計來選擇非共置計畫或共置計畫。

在共置計畫中，`Nested Loops`聯結會從內部讀取一或多個聯結資料表或索引資料分割。 `Constant Scan`運算子內的數字代表資料分割編號。 

當針對資料分割資料表或索引產生共置聯結的平行計畫時，平行處理原則運算子就會出現在`Constant Scan`與`Nested Loops`聯結運算子之間。 在此情況下，聯結外部的多個執行緒每個都會讀取和處理不同的資料分割。 

下圖將示範共置聯結的平行查詢計畫。   
![colocated_join](../relational-databases/media/colocated-join.gif)


#### <a name="parallel-query-execution-strategy-for-partitioned-objects"></a>資料分割物件的平行查詢執行策略

查詢處理器會將平行執行策略用於從資料分割物件選取的查詢。 在執行策略中，查詢處理器會判斷查詢所需的資料表資料分割，以及配置給每一個資料分割的執行緒比例。 在大多數情況下，查詢處理器會將相同或幾乎相同的執行緒數目配置給每一個資料分割，然後以平行方式在資料分割之間執行查詢。 以下段落將更詳細地說明執行緒配置。  
![thread1](../relational-databases/media/thread1.gif) 如果執行緒數目小於資料分割數目，查詢處理器會將每一個執行緒指派給不同的資料分割，一開始會讓一或多個資料分割未指派執行緒。 當執行緒在資料分割上完成執行時，查詢處理器會將它指派給下一個資料分割，直到每一個資料分割都已指派單一執行緒為止。 這是查詢處理器將執行緒重新配置給其他資料分割的唯一情況。  
顯示完成後重新指派的執行緒 如果執行緒數目等於資料分割數目，則查詢處理器會為每一個資料分割指派一個執行緒。 當執行緒完成時，不會將它重新配置給另一個資料分割。  
![thread2](../relational-databases/media/thread2.gif)  
如果執行緒數目大於資料分割數目，則查詢處理器會將相同的執行緒數目指派給每一個資料分割。 如果執行緒數目不是資料分割數目的倍數，則查詢處理器會將一個額外的執行緒配置給某些資料分割，如此才可使用所有可用的執行緒。 請注意，如果只有一個資料分割，則所有執行緒都將指派給該資料分割。 在下圖中，有四個資料分割和 14 個執行緒。 每一個資料分割都指派 3 個執行緒，其中的兩個資料分割有一個額外的執行緒，所以一共指派了 14 個執行緒。 當執行緒完成時，不會將它重新指派給另一個資料分割。  
![thread3](../relational-databases/media/thread3.gif)  
雖然上面的範例建議一個直接的方式來配置執行緒，但是實際的策略會更複雜，而且要考量在查詢執行期間所發生的其他變數。 例如，如果資料表已進行資料分割，並在資料行 A 上有一個叢集索引，而且查詢具有述詞子句 `WHERE A IN (13, 17, 25)`，則查詢處理器會將一或多個執行緒配置給這三個搜尋值 (A=13、A=17 及 A=25) 的每一個，而非每一個資料表資料分割。 只需要執行包含這些值之資料分割內的查詢，而且如果所有的這些搜尋述詞都剛好在相同的資料表資料分割中，則所有的執行緒都將指派給相同的資料表資料分割。

再舉一例，假設資料表在資料行 A 上具有四個資料分割，而界限點為 (10、20、30)、在資料行 B 上有一個索引，而且查詢具有述詞子句 `WHERE B IN (50, 100, 150)`。 由於資料表資料分割是以 A 的值為根據，所以 B 的值可能會發生在任何資料表資料分割內。 因此，查詢處理器將會在這四個資料表資料分割的每一個中，搜尋 B (50, 100, 150) 的這三個值的每一個。 查詢處理器會按比例指派執行緒，好讓它可以透過平行方式執行這 12 個查詢掃描的每一個。

|根據資料行 A 的資料表資料分割 |在每一個資料表資料分割中搜尋資料行 B |
|----|----|
|資料表資料分割 1: A \< 10   |B=50, B=100, B=150 |
|資料表資料分割 2: A >= 10 AND A \< 20   |B=50, B=100, B=150 |
|資料表資料分割 3: A >= 20 AND A \< 30   |B=50, B=100, B=150 |
|資料表資料分割 4: A >= 30  |B=50, B=100, B=150 |

### <a name="best-practices"></a>最佳作法

若要讓從大量資料分割資料表和索引中存取大量資料的查詢提升效能，我們建議您採取以下的最佳做法：

* 在多個磁碟之間條狀配置每一個資料分割。
* 盡可能使用具有充足主記憶體的伺服器，將經常存取的資料分割或所有資料分割納入記憶體中，以減少 I/O 成本。
* 如果您查詢的資料不納入記憶體中，請壓縮資料表和索引。 如此可減少 I/O 成本。
* 請使用具有快速處理器的伺服器並盡量多使用您可以負擔的處理器核心，以充分利用平行查詢處理功能。
* 確定伺服器擁有足夠的 I/O 控制器頻寬。 
* 在每一個大型資料分割資料表上建立叢集索引，以充分利用 B 型樹狀結構的掃描最佳化。
* 當您將資料大量載入資料分割資料表時，請遵循[將大量資料載入資料分割資料表](http://go.microsoft.com/fwlink/?LinkId=154561)白皮書 (英文) 中的最佳作法建議。

### <a name="example"></a>範例

下列範例會建立一個測試資料庫，其中包含具有七個資料分割的單一資料表。 當執行此範例中的查詢時，請使用之前所述的工具，以檢視編譯時間和執行階段計畫的資料分割資訊。 

> [!NOTE]
> 這個範例會將一百萬個以上的資料列插入資料表中。 執行此範例可能需要好幾分鐘的時間 (視您的硬體而定)。 在執行此範例之前，請確認有 1.5 GB 以上的磁碟空間可用。 
 
```
USE master;
GO
IF DB_ID (N'db_sales_test') IS NOT NULL
    DROP DATABASE db_sales_test;
GO
CREATE DATABASE db_sales_test;
GO
USE db_sales_test;
GO
CREATE PARTITION FUNCTION [pf_range_fact](int) AS RANGE RIGHT FOR VALUES 
(20080801, 20080901, 20081001, 20081101, 20081201, 20090101);
GO
CREATE PARTITION SCHEME [ps_fact_sales] AS PARTITION [pf_range_fact] 
ALL TO ([PRIMARY]);
GO
CREATE TABLE fact_sales(date_id int, product_id int, store_id int, 
    quantity int, unit_price numeric(7,2), other_data char(1000))
ON ps_fact_sales(date_id);
GO
CREATE CLUSTERED INDEX ci ON fact_sales(date_id);
GO
PRINT 'Loading...';
SET NOCOUNT ON;
DECLARE @i int;
SET @i = 1;
WHILE (@i<1000000)
BEGIN
    INSERT INTO fact_sales VALUES(20080800 + (@i%30) + 1, @i%10000, @i%200, RAND() * 25, (@i%3) + 1, '');
    SET @i += 1;
END;
GO
DECLARE @i int;
SET @i = 1;
WHILE (@i<10000)
BEGIN
    INSERT INTO fact_sales VALUES(20080900 + (@i%30) + 1, @i%10000, @i%200, RAND() * 25, (@i%3) + 1, '');
    SET @i += 1;
END;
PRINT 'Done.';
GO
-- Two-partition query.
SET STATISTICS XML ON;
GO
SELECT date_id, SUM(quantity*unit_price) AS total_price
FROM fact_sales
WHERE date_id BETWEEN 20080802 AND 20080902
GROUP BY date_id ;
GO
SET STATISTICS XML OFF;
GO
-- Single-partition query.
SET STATISTICS XML ON;
GO
SELECT date_id, SUM(quantity*unit_price) AS total_price
FROM fact_sales
WHERE date_id BETWEEN 20080801 AND 20080831
GROUP BY date_id;
GO
SET STATISTICS XML OFF;
GO
```