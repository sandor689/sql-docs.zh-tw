---
title: "快速入門 1：可讓 Transact-SQL 擁有更快效能的記憶體內部 OLTP 技術 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c25a164-547d-43c4-8484-6b5ee3cbaf3a
caps.latest.revision: 31
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
---
# 快速入門 1：可讓 Transact-SQL 擁有更快效能的記憶體內部 OLTP 技術
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
本文適用的對象是急著學習 Microsoft SQL Server 和 Azure SQL 資料庫的記憶體內部 OLTP 效能功能基本概念的開發人員。  
  
本文提供下列記憶體內部 OLTP 資訊：  
  
- 功能的快速說明。  
- 實作功能的核心程式碼範例。  
  
  
SQL Server 和 SQL Database 在它們對記憶體內部技術的支援上只有微小差異。  
  
  
在現實世界裡，某些部落客會將記憶體內部 OLTP 稱為 *Hekaton*。  
  
  
<a name="benefits-of-in-memory-features-21a"></a>  
  
## <a name="benefits-of-in-memory-features"></a>記憶體內部功能的優點  
  
SQL Server 提供記憶體內部功能，以大幅改進許多應用程式系統的效能。 本節說明最直接的考量。  
  
  
### <a name="features-for-oltp-online-transactional-processing"></a>OLTP (線上交易處理) 的功能  
  
  
必須同時處理大量 SQL INSERT 的系統是 OLTP 功能的絕佳候選項目。  
  
- 我們的基準測試顯示若採用記憶體內部功能，可將速度從 5 倍加快到 20 倍。  
  
  
處理 Transact-SQL 中大量計算的系統是絕佳候選項目。  
  
- 專用於大量計算之預存程序的執行速度最快可以高達 99 倍。  
  
  
您稍後可以瀏覽下列示範記憶體內部 OLTP 效能提升的各篇文章：  
  
- [示範：記憶體內部 OLTP 的效能改進](../../relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp.md)提供小規模示範來示範較大的潛在效能提升。  
- [記憶體內部 OLTP 的範例資料庫](../../relational-databases/in-memory-oltp/sample-database-for-in-memory-oltp.md)提供較大規模示範。  
  
  
  
### <a name="features-for-operational-analytics"></a>作業分析的功能  
  
記憶體內部分析指的是彙總交易資料的 SQL SELECT，通常是透過包含 GROUP BY 子句。 稱為 *columnstore* 的索引類型是作業分析的核心。  
  
有兩個主要案例︰  
  
- 「批次作業分析」指的是在營業時間後或在具有交易資料複本的次要硬體上執行的彙總程序。  
  - [Azure SQL 資料倉儲](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-overview-what-is/)也與批次作業分析有關。  
- 「即時作業分析」指的是在營業時間內以及在用於交易工作量的主要硬體上執行的彙總程序。  
  
  
目前文章的焦點是放在 OLTP，而不是分析。 如需資料行存放區索引如何將分析帶入 SQL 的資訊，請參閱：  
  
- [開始使用資料行存放區進行即時作業分析](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
- [資料行存放區索引指南](Columnstore%20Indexes%20Guide.xml)  
  
  
> [AZURE.NOTE] 有關 [Azure SQL Database - 記憶體內部技術中可用之記憶體內部功能的兩分鐘影片](http://channel9.msdn.com/Blogs/Windows-Azure/Azure-SQL-Database-In-Memory-Technologies)。 影片張貼日期為 2015 年 12 月。  


### <a name="columnstore"></a>資料行存放區

這一系列的優質部落格文章從多種角度清楚說明資料行存放區索引。 大部分文章進一步描述資料行存放區索引支援的即時作業分析概念。  這些文章由 Microsoft 專案經理 Sunil Agarwal 於 2016 年 3 月撰寫。

#### <a name="real-time-operational-analytics"></a>即時作業分析

1. [即時作業分析使用記憶體內部技術](https://blogs.technet.microsoft.com/dataplatforminsider/2015/12/09/real-time-operational-analytics-using-in-memory-technology/)
2. [即時作業分析 - 概覽非叢集資料行存放區索引 (NCCI)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/29/real-time-operational-analytics-using-nonclustered-columnstore-index/)
3. [即時作業分析：在 SQL Server 2016 中使用非叢集資料行存放區索引 (NCCI) 的簡單範例](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/29/real-time-operational-analytics-simple-example-using-nonclustered-clustered-columnstore-index-ncci/)
4. [即時作業分析：SQL Server 2016 中的 DML 作業與非叢集資料行存放區索引 (NCCI)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/04/real-time-operational-analytics-dml-operations-and-nonclustered-columnstore-index-ncci-in-sql-server-2016/)
5. [即時作業分析：經過篩選的非叢集資料行存放區索引 (NCCI)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-filtered-nonclustered-columnstore-index-ncci/)
6. [即時作業分析：非叢集資料行存放區索引 (NCCI) 的壓縮延遲選項](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-compression-delay-option-for-nonclustered-columnstore-index-ncci/)
7. [即時作業分析：使用 NCCI 的壓縮延遲選項與效能](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-compression-delay-option-with-ncci-and-the-performance/)
8. [即時作業分析：記憶體最佳化資料表與資料行存放區索引](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/real-time-operational-analytics-memory-optimized-table-and-columnstore-index/)

#### <a name="defragment-a-columnstore-index"></a>重組資料行存放區索引

1. [使用 REORGANIZE 命令的資料行存放區索引磁碟重組](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/columnstore-index-defragmentation-using-reorganize-command/)
2. [REORGANIZE 的資料行存放區索引合併原則](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/08/columnstore-index-merge-policy-for-reorganize/)

#### <a name="bulk-importation-of-data"></a>資料大量匯入

1. [叢集資料行存放區：大量載入](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2014/07/27/clustered-column-store-index-bulk-loading-the-data/)
2. [叢集資料行存放區索引︰資料載入最佳化 - 最低限度記錄](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/10/clustered-columnstore-index-data-load-optimizations-minimal-logging/)
3. [叢集資料行存放區索引︰資料載入最佳化 - 平行大量匯入](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/28/clustered-columnstore-index-parallel-bulk-import/)





<a name="features-on-in-memory-oltp-13b"></a>  
  
## <a name="features-of-in-memory-oltp"></a>記憶體內部 OLTP 的功能  
  
請查看記憶體內部 OLTP 的主要功能。  
  
  
#### <a name="memory-optimized-tables"></a>記憶體最佳化的資料表  
  
CREATE TABLE 陳述式上的 T-SQL 關鍵字 MEMORY_OPTIMIZED 是建立資料表使其存在於使用中的記憶體上而非磁碟上的方式。  
  
  
[記憶體最佳化資料表](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)會在使用中記憶體中有一個代表它自己的表示方式，並在磁碟中有第二個表示方式副本。  
  
- 磁碟副本是在伺服器或資料庫關機然後重新啟動之後用於例行復原。 您和您的程式碼完全看不到這個記憶體加磁碟雙重性。  
  
  
#### <a name="natively-compiled-modules"></a>原生編譯模組  
  
CREATE PROCEDURE 陳述式上的 T-SQL 關鍵字 NATIVE_COMPILATION 為建立原生程序的方式。 每次資料庫重新上線時，都會在第一次使用原生處理序時將 T-SQL 陳述式編譯成機器碼。 T-SQL 指令無法再忍受緩慢解譯每個指令。  
  
- 我們已經看到原生編譯可讓持續時間只有解譯之持續時間的 1/100。  
  
  
原生模組只能參考記憶體最佳化資料表，且其無法參考磁碟資料表。  
  
有三種類型的原生編譯模組：  
  
- [原生編譯的預存程序](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)。  
- 原生編譯的使用者定義函數 (UDF)，也就是純量。  
- 原生編譯的觸發程序。  
  
  
#### <a name="availability-in-azure-sql-database"></a>Azure SQL Database 中的可用性  
  
記憶體內部 OLTP 和資料行存放區可在 Azure SQL Database 中使用。 如需詳細資訊，請參閱[在 SQL Database 中使用記憶體內部技術最佳化效能](https://docs.microsoft.com/azure/sql-database/sql-database-in-memory)。
  
  
<a name="ensure-compatibility-level-gteq-130-99c"></a>  
  
## <a name="1-ensure-compatibility-level-130"></a>1.確保相容性層級高於或等於 130  
  
  
本節是一系列已編製號碼之一節的開始，並且示範您可以用來實作記憶體內部 OLTP 功能的 Transact-SQL 語法。  
  
  
首先，將您的資料庫設定為至少 130 的相容性層級很重要。 接下來是使用 T-SQL 程式碼來檢視您目前的資料庫所設定的相容性層級。  
  
  
  
  
  
    SELECT d.compatibility_level  
        FROM sys.databases as d  
        WHERE d.name = Db_Name();  
  
  
  
  
然後是使用 T-SQL 程式碼來更新層級 (如有必要)。  
  
  
  
  
    ALTER DATABASE CURRENT  
        SET COMPATIBILITY_LEVEL = 130;  
  
  
  
  
<a name="elevate-to-snapshot-26n"></a>  
  
## <a name="2-elevate-to-snapshot"></a>2.提升至 SNAPSHOT  
  
  
當交易涉及磁碟資料表和記憶體最佳化資料表時，我們稱之為*跨容器交易*。 在這樣的交易中，很重要的一點是交易的記憶體最佳化部分需在名為 SNAPSHOT 的交易隔離等級中執行。  
  
若要在跨容器交易中針對記憶體最佳化資料表可靠地強制執行此等級，請透過執行以下 T-SQL 來[修改您的資料庫設定](ALTER%20DATABASE%20SET%20Options%20%28Transact-SQL%29.xml)。  
  
  
  
  
    ALTER DATABASE CURRENT  
        SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
  
  
  
  
<a name="create-an-optimized-filegroup-24r"></a>  
  
## <a name="3-create-an-optimized-filegroup"></a>3.建立最佳化的 FILEGROUP  
  
  
在 Microsoft SQL Server 中，在您能夠建立記憶體最佳化資料表之前，您必須先建立宣告 CONTAINS MEMORY_OPTIMIZED_DATA 的 FILEGROUP。 FILEGROUP 會指派給您的資料庫。 如需詳細資料，請參閱：  
  
- [記憶體最佳化的 FILEGROUP](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md)  
  
  
在 Azure SQL Database 中，您不需要也無法建立這樣的 FILEGROUP。  

下列 T-SQL 指令碼範例會針對記憶體內部 OLTP 啟用資料庫，並設定所有建議的設定。 它會同時使用 SQL Server 和 Azure SQL Database：[enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)。
  
  
<a name="create-a-memory-optimized-table-26y"></a>  
  
## <a name="4-create-a-memory-optimized-table"></a>4.建立記憶體最佳化資料表  
  
  
  
  
重要的 Transact-SQL 關鍵字是 MEMORY_OPTIMIZED。  
  
  
  
  
    CREATE TABLE dbo.SalesOrder  
    (  
        SalesOrderId   integer        not null  IDENTITY  
            PRIMARY KEY NONCLUSTERED,  
        CustomerId     integer        not null,  
        OrderDate      datetime       not null  
    )  
        WITH  
            (MEMORY_OPTIMIZED = ON,  
            DURABILITY = SCHEMA_AND_DATA);  
  
  
  
  
針對記憶體最佳化資料表的 Transact-SQL INSERT 和 SELECT 陳述式與一般資料表無異。  
  
#### <a name="alter-table-for-memory-optimized-tables"></a>適用於記憶體最佳化資料表的 ALTER TABLE  
  
ALTER TABLE...ADD/DROP 可以從記憶體最佳化資料表或索引新增或移除資料行。  
  
- CREATE INDEX 和 DROP INDEX 無法針對記憶體最佳化資料表執行，請改用 ALTER TABLE ...ADD/DROP INDEX。  
- 如需詳細資料，請參閱[修改記憶體最佳化資料表](../../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md)。  
  
  
#### <a name="plan-your-memory-optimized-tables-and-indexes"></a>規劃您的記憶體最佳化資料表及索引  
  
  
- [記憶體最佳化資料表的索引](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)  
- [記憶體內部 OLTP 不支援的 Transact-SQL 建構](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
  
<a name="create-a-natively-compiled-stored-procedure-native-proc-29u"></a>  
  
## <a name="5-create-a-natively-compiled-stored-procedure-native-proc"></a>5.建立原生編譯的預存程序 (原生程序)  
  
  
重要關鍵字為 NATIVE_COMPILATION。  
  
  
  
  
    CREATE PROCEDURE ncspRetrieveLatestSalesOrderIdForCustomerId  
        @_CustomerId   INT  
        WITH  
            NATIVE_COMPILATION,  
            SCHEMABINDING  
    AS  
    BEGIN ATOMIC  
        WITH  
            (TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
            LANGUAGE = N'us_english')  
      
        DECLARE @SalesOrderId int, @OrderDate datetime;  
      
        SELECT TOP 1  
                @SalesOrderId = s.SalesOrderId,  
                @OrderDate    = s.OrderDate  
            FROM dbo.SalesOrder AS s  
            WHERE s.CustomerId = @_CustomerId  
            ORDER BY s.OrderDate DESC;  
      
        RETURN @SalesOrderId;  
    END;  
  
  
  
  
關鍵字 SCHEMABINDING 表示原生程序中參考的資料表無法卸除，除非先卸除原生程序。 如需詳細資料，請參閱[建立原生編譯的預存程序](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md)。  
  
  
<a name="execute-the-native-proc-31e"></a>  
  
## <a name="6-execute-the-native-proc"></a>6.執行原生程序  
  
  
填入包含兩個資料列的資料表。  
  
  
  
  
    INSERT into dbo.SalesOrder  
            ( CustomerId, OrderDate )  
        VALUES  
            ( 42, '2013-01-13 03:35:59' ),  
            ( 42, '2015-01-15 15:35:59' );  
  
  
  
  
接著會對原生編譯的預存程序進行 EXECUTE 呼叫。  
  
  
  
  
    DECLARE @LatestSalesOrderId int, @mesg nvarchar(128);  
      
    EXECUTE @LatestSalesOrderId =  
        ncspRetrieveLatestSalesOrderIdForCustomerId 42;  
      
    SET @mesg = CONCAT(@LatestSalesOrderId,  
        ' = Latest SalesOrderId, for CustomerId = ', 42);  
    PRINT @mesg;  
      
    -- Here is the actual PRINT output:  
    -- 2 = Latest SalesOrderId, for CustomerId = 42  
  
  
  
  
<a name="guide-to-the-documentation-and-next-steps-32w"></a>  
  
### <a name="guide-to-the-documentation-and-next-steps"></a>文件與後續步驟的指南  
  
  
上述一般範例可提供基礎知識，以協助您了解記憶體內部 OLTP 的更進階功能。 下列小節為您可能需要知道之特殊考量，以及您可以移至何處以查看每項特殊考量之相關詳細資料的指南。  
  
  
  
<a name="how-do-in-memory-oltp-features-work-so-much-faster-33v"></a>  
  
## <a name="how-in-memory-oltp-features-work-so-much-faster"></a>記憶體內部 OLTP 功能如何運作得這麼快  
  
  
下列子小節會概略描述記憶體內部 OLTP 功能如何在內部運作以提供改進效能。  
  
  
<a name="how-do-memory-optimized-tables-perform-faster-34q"></a>  
  
### <a name="how-memory-optimized-tables-perform-faster"></a>記憶體最佳化資料表如何執行得更快  
  
  
**雙重本質：**記憶體最佳化資料表具有雙重本質：一個是在使用中記憶體中的表示方式，另一個是在硬碟中的表示方式。 每項交易都會對資料表的兩種代表方式進行認可。 交易會針對速度較快的使用中記憶體表示方式運作。 記憶體最佳化資料表可從速度更快的使用中記憶體 (相較於硬碟) 獲益。 此外，使用中記憶體較高的敏捷性也讓針對速度最佳化的更先進資料表結構得以實現。 進階結構也是無頁面結構，因此它可以避免閂鎖和執行序同步鎖定超出負荷及競爭。  
  
  
**無鎖定：**記憶體最佳化資料表依賴*開放式*方法來達到資料完整性和並行處理及高輸送量之間的競爭目標。 在交易期間，資料表不會鎖定任何版本的已更新資料列。 這可以顯著降低某些高容量系統中的競爭。  
  
  
**資料列版本：**記憶體最佳化資料表會在本身的資料表 (而非在 tempdb) 中新增已更新之資料列的新版本，而非鎖定。 原始資料列會保留到交易被認可之後。 在交易期間，其他處理序可以讀取資料表的原始版本。  
  
- 為磁碟資料表建立多個版本的資料列時，資料列版本會暫時儲存在 tempdb 中。  
  
  
**記錄較少：**已更新資料表之前與之後的版本會保留在記憶體最佳化資料表中。 資料列配對可提供許多傳統上會寫入記錄檔的資訊。 這可以讓系統寫入較少的資訊，以及降低寫入記錄的頻率。 同時還能確保交易完整性。  
  
  
<a name="how-do-native-procs-perform-faster-35x"></a>  
  
### <a name="how-native-procs-perform-faster"></a>原生程序如何執行得更快  
  
將一般轉譯的預存程序轉換成原生編譯的預存程序，能夠大幅減少執行階段期間執行的指令數目。  
  
  
<a name="trade-offs-of-in-memory-features-36j"></a>  
  
## <a name="trade-offs-of-in-memory-features"></a>記憶體內部功能的取捨  
  
  
如同電腦科學中常見的取捨考量一樣，記憶體內部功能所提供的效能提升就是一項取捨考量。 更好的功能所帶來的好處，其價值高於為功能所付出的額外成本。 您可以找到有關取捨的完整指導︰

- [規劃在 SQL Server 中採用記憶體內部 OLTP 功能](../../relational-databases/in-memory-oltp/plan-your-adoption-of-in-memory-oltp-features-in-sql-server.md)

本節的其餘部分會列出一些主要的規劃和取捨考量。
  
<a name="trade-offs-of-memory-optimized-tables-37d"></a>  
  
### <a name="trade-offs-of-memory-optimized-tables"></a>memory_optimized 資料表的取捨  
  
  
**評估記憶體：**您必須評估您的記憶體最佳化資料表將耗用的使用中記憶體總量。 您的電腦系統必須擁有足夠的記憶體容量，才能裝載記憶體最佳化資料表。 如需詳細資料，請參閱：  
  
- [監視與疑難排解記憶體使用量](../../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)  
- [估計記憶體最佳化資料表的記憶體需求](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)  
- [記憶體最佳化資料表中的資料表和資料列大小](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)  
  
  
**分割大型資料表：**滿足大部分使用中記憶體需求的方式之一是將您的大型資料表分割成多個部分，部分位於儲存*最近使用*之資料列的記憶體內部，其他部分則位於儲存*舊版未使用*之資料列 (例如已經完全出貨並結單的銷售訂單) 的磁碟中。 此資料分割的設計與實作程序為手動程序。 請參閱：  
  
- [應用程式層級資料分割](../../relational-databases/in-memory-oltp/application-level-partitioning.md)  
- [分割記憶體最佳化資料表的應用程式模式](../../relational-databases/in-memory-oltp/application-pattern-for-partitioning-memory-optimized-tables.md)  
  
  
<a name="trade-offs-of-native-procs-38p"></a>  
  
### <a name="trade-offs-of-native-procs"></a>原生程序的取捨  
  
  
- 原生編譯的預存程序無法存取磁碟資料表。 原生程序只能存取記憶體最佳化資料表。  
- 當原生程序在伺服器或資料庫最近恢復上線之後第一次執行時，必須將原生程序重新編譯一次。 這會造成在原生程序開始執行之前出現延遲。  
  
  
<a name="advanced-considerations-for-memory-optimized-tables-39n"></a>  
  
## <a name="advanced-considerations-for-memory-optimized-tables"></a>記憶體最佳化資料表的進階考量  
  
  
[記憶體最佳化資料表的索引](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)有些部分與傳統磁碟之資料表上的索引不同。  
  
- 只有在記憶體最佳化資料表上才能使用[雜湊索引](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md)。  
  
  
您必須加以規劃，以確保有足夠的使用中記憶體可供您規劃的記憶體最佳化資料表和其索引使用。 請參閱：  
  
- [為記憶體內部 OLTP 管理記憶體](Managing%20Memory%20for%20In-Memory%20OLTP.xml)  
- [建立及管理記憶體最佳化物件的儲存體](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
記憶體最佳化資料表可以使用 DURABILITY = SCHEMA_ONLY 進行宣告：  
  
- 此語法可在資料庫離線時，告知系統捨棄來自記憶體最佳化資料表的所有資料。 只會保存資料表定義。  
- 當資料庫恢復上線時，記憶體最佳化資料表會載入回使用中記憶體，但其中不包含任何資料。  
- 包含數千個資料列時，SCHEMA_ONLY 資料表可以是 tempdb 中 [#temporary 資料表](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)的較佳替代項目。  
  
  
資料表變數也可以宣告為記憶體最佳化。 請參閱：  
  
- [使用記憶體最佳化加快暫存資料表與資料表變數的速度](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)  
  
  
  
<a name="advanced-considerations-for-natively-compiled-modules-40k"></a>  
  
## <a name="advanced-considerations-for-natively-compiled-modules"></a>原生編譯模組的進階考量  
  
  
可透過 Transact-SQL 使用的原生編譯模組類型為：  
  
- 原生編譯的預存程序 (原生程序)。  
- 原生編譯的 [純量使用者定義函數](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)。  
- 原生編譯的觸發程序 (原生觸發程序)。  
  - 記憶體最佳化資料表中只允許使用原生編譯的觸發程序。  
- 原生編譯的 [資料表值函式](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md)。  
  - [使用記憶體最佳化提升暫存資料表與資料表變數效能](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)  
  
  
原生編譯使用者定義函數 (UDF) 的執行速度比解譯的 UDF 還要快。 以下是使用 UDF 時所需考慮的數個事項：  
  
- 當 T-SQL SELECT 使用 UDF 時，一律會在每個傳回資料列上呼叫一次 UDF。  
  - UDF 永遠不會以內嵌方式執行，而是一律以呼叫的方式執行。  
  - 相較於所有 UDF 固有之重複呼叫的額外負荷，編譯的差異並沒有那麼重要。  
  - 而且，在實際層級，通常可接受 UDF 呼叫的額外負荷。  
  
如需原生 UDF 效能的測試資料和說明，請參閱︰  
  
  - [在 SQL Server 2016 中使用原生編譯的 UDF 來降低 RBAR 影響](https://blogs.msdn.microsoft.com/sqlcat/2016/02/17/soften-the-rbar-impact-with-native-compiled-udfs-in-sql-server-2016/)  
  - [Gail Shaw 撰寫的優秀部落格文章](http://sqlinthewild.co.za/index.php/2016/01/12/natively-compiled-user-defined-functions/)，張貼日期為2016 年 1 月。  
  
  
<a name="documentation-guide-for-memory-optimized-tables-41z"></a>  
  
## <a name="documentation-guide-for-memory-optimized-tables"></a>記憶體最佳化資料表的文件指南  
  
  
以下是其他討論記憶體最佳化資料表之特殊考量的文章連結：  
  
- [移轉至記憶體內部 OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  - [判斷是否應將資料表或預存程序移植至記憶體內部 OLTP](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)  
  - SQL Server Management Studio 中的交易效能分析報告可協助您評估記憶體內部 OLTP 是否能改善您資料庫應用程式的效能。  
  - 請使用[記憶體最佳化建議程式](../../relational-databases/in-memory-oltp/memory-optimization-advisor.md)協助您將磁碟資料庫資料表移轉至記憶體內部 OLTP。   
- [備份、還原及復原記憶體最佳化資料表](Backup,%20Restore,%20and%20Recovery%20of%20Memory-Optimized%20Tables.xml)  
  - 記憶體最佳化資料表所使用的儲存空間可能會遠超過它在記憶體中的大小，而且會影響資料庫備份的大小。  
- [與記憶體最佳化資料表的交易](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)  
  - 包含 T-SQL 中記憶體最佳化資料表交易的重試邏輯相關資訊。  
- [記憶體內部 OLTP 的 Transact-SQL 支援](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  - 記憶體最佳化資料表和原生程序支援及不支援的 T-SQL 和資料類型。  
- [將包含記憶體最佳化資料表的資料庫繫結至資源集區](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)中會討論選擇性的進階考量。  
  
  
  
<a name="documentation-guide-for-native-procs-42b"></a>  
  
## <a name="documentation-guide-for-native-procs"></a>原生程序的文件指南  
  
  
  
<a name="related-links-43f"></a>  
  
## <a name="related-links"></a>相關連結  
  
- 內部文章：[記憶體內部 OLTP (記憶體內部最佳化)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
下列文章提供程式碼，示範您可以使用記憶體內部 OLTP 達到的效能提升︰  
  
- [示範：記憶體內部 OLTP 的效能改進](../../relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp.md)提供小規模示範來示範較大的潛在效能提升。  
- [記憶體內部 OLTP 的範例資料庫](../../relational-databases/in-memory-oltp/sample-database-for-in-memory-oltp.md)提供較大規模示範。  
  
  
  
\<!--  
  
e1328615-6b59-4473-8a8d-4f360f73187d , dn817827.aspx ,  "Get started with Columnstore for real time operational analytics"  
  
f98af4a5-4523-43b1-be8d-1b03c3217839 , gg492088.aspx , "Columnstore Indexes Guide"  
  
14dddf81-b502-49dc-a6b6-d18b1ae32d2b , dn133165.aspx , "Memory-Optimized Tables"  
  
d5ed432c-10c5-4e4f-883c-ef4d1fa32366 , dn133184.aspx , "Natively compiled stored procedures"  
  
14106cc9-816b-493a-bcb9-fe66a1cd4630 , dn639109.aspx , "The Memory Optimized Filegroup"  
  
f222b1d5-d2fa-4269-8294-4575a0e78636 , dn465873.aspx , "Bind a Database with Memory-Optimized Tables to a Resource Pool"  
  
86805eeb-6972-45d8-8369-16ededc535c7 , dn511012.aspx , "Indexes on Memory-Optimized Tables"  
  
16ef63a4-367a-46ac-917d-9eebc81ab29b , dn133166.aspx , "Guidelines for Using Indexes on Memory-Optimized Tables"  
  
e3f8009c-319d-4d7b-8993-828e55ccde11 , dn246937.aspx , "Transact-SQL Constructs Not Supported by In-Memory OLTP"  
  
2cd07d26-a1f1-4034-8d6f-f196eed1b763 , dn133169.aspx , "Transactions in Memory-Optimized Tables"  
NOTE: SEE mt668425.aspx "Behaviors and Guidelines for Transactions with Memory-Optimized Tables", its soon replacement for these!  
f2a35c37-4449-49ee-8bba-928028f1de66 , dn169141.aspx , "Guidelines for Retry Logic for Transactions on Memory-Optimized Tables"  
  
7a458b9c-3423-4e24-823d-99573544c877 , dn465869.aspx , "Monitor and Troubleshoot Memory Usage"  
  
5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8 , dn282389.aspx , "Estimate Memory Requirements for Memory-Optimized Tables"  
  
b0a248a4-4488-4cc8-89fc-46906a8c24a1 , dn205318.aspx , "Table and Row Size in Memory-Optimized Tables"  
  
162d1392-39d2-4436-a4d9-ee5c47864c5a , dn296452.aspx , "Application-Level Partitioning"  
  
3f867763-a8e6-413a-b015-20e9672cc4d1 , dn133171.aspx , "Application Pattern for Partitioning Memory-Optimized Tables"  
  
86805eeb-6972-45d8-8369-16ededc535c7 , dn511012.aspx , "Indexes on Memory-Optimized Tables"  
  
d82f21fa-6be1-4723-a72e-f2526fafd1b6 , dn465872.aspx , "Managing Memory for Memory-Optimized OLTP"  
  
622aabe6-95c7-42cc-8768-ac2e679c5089 , dn133174.aspx , "Creating and Managing Storage for Memory-Optimized Objects"  
  
bd102e95-53e2-4da6-9b8b-0e4f02d286d3 , dn535766.aspx , "Memory-Optimized Table Variables"; "table variable of a memory-optimized table"  
OBSOLETE. Instead see 38512a22-7e63-436f-9c13-dde7cf5c2202 , mt718711.aspx , "Faster temp table and table variable by using memory optimization"  
  
  
f0d5dd10-73fd-4e05-9177-07f56552bdf7 , ms191320.aspx , "Create User-defined Functions (Database Engine)"; "table-valued functions"  
  
d2546e40-fdfc-414b-8196-76ed1f124bf5 , dn935012.aspx , "Scalar User-Defined Functions for In-Memory OLTP"; "scalar user-defined functions"  
  
405cdac5-a0d4-47a4-9180-82876b773b82 , dn247639.aspx , "Migrating to In-Memory OLTP"  
  
3f083347-0fbb-4b19-a6fb-1818d545e281 , dn624160.aspx , "Backup, Restore, and Recovery of Memory-Optimized Tables"  
  
690b70b7-5be1-4014-af97-54e531997839 , dn269114.aspx , "Altering Memory-Optimized Tables"  
  
  
b1cc7c30-1747-4c21-88ac-e95a5e58baac , dn133080.aspx , "New and Updated Properties, System Views, Stored Procedures, Wait Types, and DMVs for In-Memory OLTP"  
. . . . .  
ALSO: "Transact-SQL Support for In-Memory OLTP"  
  
  
c1ef96f1-290d-4952-8369-2f49f27afee2 , dn205133.aspx , "Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP"  
  
181989c2-9636-415a-bd1d-d304fc920b8a , dn284308.aspx , "Memory Optimization Advisor"  
  
55548cb2-77a8-4953-8b5a-f2778a4f13cf , dn452282.aspx , "Monitoring Performance of Natively Compiled Stored Procedures"  
  
d3898a47-2985-4a08-bc70-fd8331a01b7b , dn358355.aspx , "Native Compilation Advisor"  
  
f43faad4-2182-4b43-a76a-0e3b405816d1 , dn296678.aspx , "Migration Issues for Natively Compiled Stored Procedures"  
  
e1d03d74-2572-4a55-afd6-7edf0bc28bdb , dn133186.aspx , "In-Memory OLTP (In-Memory Optimization)"  
  
c6def45d-d2d4-4d24-8068-fab4cd94d8cc , dn530757.aspx , "Demonstration: Performance Improvement of In-Memory OLTP"  
  
405cdac5-a0d4-47a4-9180-82876b773b82 , dn247639.aspx , "Migrating to In-Memory OLTP"  
  
f76fbd84-df59-4404-806b-8ecb4497c9cc , bb522682.aspx , "ALTER DATABASE SET Options (Transact-SQL)"  
  
e6b34010-cf62-4f65-bbdf-117f291cde7b , dn452286.aspx , "Creating Natively Compiled Stored Procedures"  
  
df347f9b-b950-4e3a-85f4-b9f21735eae3 , mt465764.aspx , "Sample Database for In-Memory OLTP"  
  
38512a22-7e63-436f-9c13-dde7cf5c2202 , mt718711.aspx , "Faster temp table and table variable by using memory optimization"  
  
38512a22-7e63-436f-9c13-dde7cf5c2202 , mt718711.aspx , "Faster temp table and table variable by using memory optimization"  
  
  
  
  
H1 # Quick Start 1: In-Memory technologies for faster transactional workloads  
{1c25a164-547d-43c4-8484-6b5ee3cbaf3a} in CAPS  
mt718711.aspx on MSDN  
  
GeneMi , 2016-05-07  00:07am  
-->  
  
  
  