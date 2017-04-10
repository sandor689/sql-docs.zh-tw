---
title: "設定及管理全文檢索搜尋的同義字檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "全文檢索索引 [SQL Server], 同義字檔案"
  - "同義字 [全文檢索搜尋], 設定"
  - "同義字 [全文檢索搜尋]"
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
caps.latest.revision: 84
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 83
---
# 設定及管理全文檢索搜尋的同義字檔案
  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，全文檢索查詢可以透過使用同義字 (Thesaurus) 搜尋使用者指定之詞彙的同義字 (Synonym)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]「同義字」 (thesaurus) 會針對特定語言定義一組同義字 (synonym)。 系統管理員可以定義兩種同義字形式：展開集和取代集。 透過開發符合全文檢索資料的同義字，您可以有效地擴大針對該資料進行全文檢索查詢的範圍。 同義字比對會針對所有 [FREETEXT](../../t-sql/queries/freetext-transact-sql.md) 和 [FREETEXTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) 查詢以及指定 FORMSOF THESAURUS 子句的任何 [CONTAINS](../../t-sql/queries/contains-transact-sql.md) 和 [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) 查詢進行。  
  
##  <a name="tasks"></a> 設定同義字檔案的基本工作  
 您必須先針對給定的語言定義同義字 (thesaurus) 對應 (同義字)，然後伺服器執行個體上的全文檢索搜詢查詢才能尋找該語言的同義字 (synonym)。 您必須手動設定每個同義字，以便定義下列項目：  
  
-   變音符號設定  
  
     對於給定的同義字而言，所有搜尋模式都會區分或不區分變音符號，例如波狀符號 (**~**)、尖重音符號 (**´**) 或母音變化 (**¨**) (亦即，「區分腔調字」或「不區分腔調字」)。 例如，假設您在全文檢索查詢中，指定以其他模式取代模式 "café"。 如果同義字不區分腔調字，全文檢索搜尋就會取代模式 "café" 和 "cafe"。 如果同義字區分腔調字，全文檢索搜尋只會取代模式 "café"。 根據預設，同義字不會區分腔調字。  
  
-   展開集  
  
     展開集包含可以由全文檢索查詢彼此替代的一組同義字，例如 "writer"、"author" 和 "journalist"。 包含展開集中任何同義字之相符項目的查詢會展開成包含展開集中的其他每個同義字。  
  
     如需詳細資訊，請參閱本主題後面的「展開集的 XML 結構」。  
  
-   取代集  
  
     取代集包含替代集所要取代的文字模式。 如需範例，請參閱本主題後面的＜取代集的 XML 結構＞一節。  
  
 [&#91;回到頁首&#93;](#Top)  
  
##  <a name="initial_thesaurus_files"></a> 同義字檔案的初始內容  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供了一組 XML 同義字檔案 (每個支援的語言都有一個檔案)。 這些檔案基本上都是空的。 它們僅包含所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 同義字通用的最上層 XML 結構以及標記為註解的範例同義字。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 隨附的同義字檔案都包含下列 XML 程式碼：  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
 [&#91;回到頁首&#93;](#Top)  
  
##  <a name="location"></a> 同義字檔案的位置  
 同義字檔案的預設位置為：  
  
 \<SQL Server 資料檔案路徑>\MSSQL13.MSSQLSERVER\MSSQL\FTDATA\  
  
 這個預設位置包含下列檔案：  
  
-   語言特有的同義字檔案  
  
     安裝期間，空的同義字檔案會安裝在上述位置。 系統會針對每個支援的語言提供一個個別的檔案。 系統管理員可以自訂這些檔案。  
  
     同義字檔案的預設檔案名稱會使用下列格式：  
  
     'ts' + \<由三個英文字母所組成的語言縮寫> + '.xml'  
  
     給定語言之同義字檔案的名稱是使用下列值指定於登錄中：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<執行個體名稱>\MSSearch\\<語言縮寫>。  
  
-   通用同義字檔案  
  
     空的通用同義字檔案：tsGlobal.xml。  
  
 您可以變更同義字檔案的登錄機碼，藉以變更其位置和名稱。 針對每個語言，同義字檔案的位置會指定在下列登錄值中：  
  
 HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/\<執行個體名稱>/MSSearch/Language/\<語言縮寫>/TsaurusFile  
  
 通用同義字檔案會對應至 LCID 0 的中性語言。 只有管理員能夠變更這個值。  
  
 [&#91;回到頁首&#93;](#Top)  
  
##  <a name="how_queries_use_tf"></a> 查詢如何使用同義字檔案  
 同義字查詢會同時使用語言特有的同義字和通用同義字。 首先，查詢會查閱語言特有的檔案並載入此檔案，以便進行處理 (除非已經載入此檔案)。 查詢會展開成包含同義字 (Thesaurus) 檔案中展開集和取代集規則所指定的語言特有同義字 (Synonym)。 然後，系統會針對通用同義字重複這些步驟。 不過，如果某個詞彙已經是語言特有同義字檔案中相符項目的一部分，該詞彙就不適用於在通用同義字中比對。  
  
 [&#91;回到頁首&#93;](#Top)  
  
##  <a name="structure"></a> 了解同義字檔案的結構  
 每個同義字檔案都會定義識別碼為 `Microsoft Search Thesaurus` 的 XML 容器以及 `<!--` … `-->`(包含範例同義字的註解)。 同義字定義於包含子元素範例的 \<thesaurus> 元素中，而這些子元素會定義變音符號設定、展開集和取代集，如下所示：  
  
-   變音符號設定的 XML 結構  
  
     同義字的變音符號設定指定於單一 <diacritics_sensitive> 元素中。 這個元素包含可控制區分腔調字的整數值，如下所示：  
  
    |變音符號設定|值|XML|  
    |------------------------|-----------|---------|  
    |不區分腔調字|0|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |區分腔調字|1|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  此設定只能在檔案中套用一次，而且它會套用至檔案中的所有搜尋模式。 不能針對個別模式指定此設定。  
  
-   展開集的 XML 結構  
  
     每個展開集都是用 \<expansion> 元素括住。 在這個元素內，您可以使用 \<sub> 元素來指定一或多個替代項目。 在展開集中，您可以指定一組彼此是同義字的替代項目。  
  
     例如，您可編輯展開區段，以將 "writer"、"author" 及 "journalist" 替代字視為同義字。 此時會展開包含某個替代項目之相符項目的全文檢索搜尋查詢，以併入展開集中指定的所有其他替代項目。 因此，在上個範例中，發出 FORMS OF THESAURUS 或 FREETEXT 查詢以尋找 "author" 這個字時，全文檢索搜尋也會傳回內含 "writer" 和 "journalist" 這些字的搜尋結果。  
  
     這是上例之展開集區段的樣子：  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   取代集的 XML 結構  
  
     每個取代集都是用 \<replacement> 元素括住。 在這個元素內，您可以使用 \<pat> 元素來指定一或多個模式並且使用 \<sub> 元素來指定零或多個替代項目 (每個同義字指定一個)。 您也可以指定要用替代集取代的模式。 模式和替代項目都可以包含單字或一串文字。 如果沒有針對某個模式指定替代項目，其作用就是從使用者查詢中移除該模式。  
  
     例如，假設您想要查詢 "Win8" (模式) 以將其取代為 "Windows Server 2012" 或 "Windows 8.0" (替代項目)。 如果您要執行全文檢索查詢以找出 "Win8"，則全文檢索搜尋只會傳回內含 "Windows Server 2012" 或 "Windows 8.0" 的搜尋結果。 它不會傳回內含 "Win8" 的結果。 這是因為 "Win8" 模式已「取代」為 "Windows Server 2012" 和 "Windows 8.0" 模式。  
  
     這是上例之取代集區段的樣子：  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     如果您有兩個相似模式相符的取代集，則這兩個取代集中長度較長之取代集的優先順序較高。 例如，如果您執行 FORMS OF THESAURUS 查詢以找出 "Internet Explorer online community" 且具有下列取代集，則 "Internet Explorer" 取代集的優先順序高於 "Internet" 取代集。 因此，系統會將該查詢處理為 "IE online community" 或 "IE 9 online community"。  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     及  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
 [&#91;回到頁首&#93;](#Top)  
  
##  <a name="working_with_thesaurus_files"></a> 使用同義字檔案  
 **編輯同義字檔案**  
  
-   [編輯同義字檔案](#editing)  
  
 **載入更新的同義字檔案**  
  
-   [sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)  
  
 **檢視斷詞工具、同義字及停用字詞表組合的 Token 化結果**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md)  
  
 [&#91;回到頁首&#93;](#Top)  
  
##  <a name="editing"></a> 編輯同義字檔案  
 您可以透過編輯給定語言的同義字檔案 (XML 檔案)，設定同義字。 在安裝期間，系統會安裝僅包含 \<xml> 容器和標記為註解之範例 \<thesaurus> 元素的空白同義字檔案。 若要讓尋找同義字的全文檢索搜詢查詢正常運作，您必須建立定義一組同義字的實際 \<thesaurus> 元素。 您可以定義兩種同義字形式：展開集和取代集。  
  
 **同義字檔案的限制**  
  
 當您編輯同義字檔案時，就會適用下列限制：  
  
-   只有系統管理員能夠更新、修改或刪除同義字檔案。  
  
-   當您使用文字編輯器工具編輯同義字檔案時，必須以 Unicode 格式儲存這些檔案，而且必須指定位元組順序標示 (BOM)。  
  
-   同義字項目不得為空白或斷詞為空字串。  
  
-   同義字檔案中的片語長度不得超過 512 個字元。  
  
-   在展開集的 \<sub> 項目與取代集的 \<pat> 元素之間，同義字不得包含任何重複的項目。  
  
 **同義字檔案的建議**  
  
 我們建議同義字檔案中的項目不應該包含任何特殊字元。 這是因為斷詞工具在處理特殊字元方面具有難以察覺的行為。 如果某個同義字項目包含任何特殊字元，與該項目搭配使用的斷詞工具可能會針對全文檢索查詢產生難以察覺的行為隱含。  
  
 我們建議 \<sub> 項目不應該包含任何停用字詞，因為全文檢索索引已經省略了停用字詞。 查詢會展開成包含同義字的 \<sub> 項目，而且如果 \<sub> 項目包含停用字詞，查詢的大小就會不必要地增加。  
  
#### 編輯同義字檔案  
  
1.  在 [記事本] 中，開啟同義字檔案。  
  
2.  如果是第一次編輯同義字檔案，則請分別移除檔案開頭及結尾處的下列註解行：  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  加入、修改或刪除取代集或展開集。  
  
4.  儲存檔案並關閉記事本。  
  
5.  使用 [sp_fulltext_load_thesaurus_file](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)，將同義字檔案的內容載入 tempdb，並指定對應至同義字檔案語言的地區設定識別碼 (LCID)。 例如，英文同義字檔案 tsenu.xml 的對應 LCID 就是 1033。  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
 [&#91;回到頁首&#93;](#Top)  
  
## 另請參閱  
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [全文檢索搜尋](../../relational-databases/search/full-text-search.md)  
  
  