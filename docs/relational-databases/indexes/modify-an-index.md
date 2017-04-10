---
title: "修改索引 | Microsoft Docs"
ms.custom: ""
ms.date: "02/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "索引 [SQL Server], 修改"
  - "修改索引"
  - "索引變更 [SQL Server]"
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# 修改索引
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，修改 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的索引。  
  
> [!IMPORTANT]  
>  因 PRIMARY KEY 或 UNIQUE 條件約束而建立的索引將無法使用此方法來修改。 必須修改條件約束。  
  
 **本主題內容**  
  
-   **若要修改索引，使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### 若要修改索引  
  
1.  在 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。  
  
2.  展開 **[資料庫]**，展開資料表所在的資料庫，然後展開 **[資料表]**。  
  
3.  展開索引所在的資料表，然後展開 **[索引]**。  
  
4.  以滑鼠右鍵按一下您要修改的索引，然後按一下 [屬性]。  
  
5.  在 **[索引屬性]** 對話方塊中，進行所需的變更。 例如，您可以在索引鍵中加入或移除資料行，或是變更索引選項的設定。  
  
#### 若要修改索引資料行  
  
1.  若要加入、移除或變更索引資料行的位置，請選取 **[索引屬性]** 對話方塊中的 **[一般]** 頁面。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### 若要修改索引  
  
1.  連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。 此範例會利用 `ProductID` 選項，在 `Production.WorkOrder` 資料表的 `DROP_EXISTING` 資料行上卸除及重新建立現有的索引。 也會設定 `FILLFACTOR` 和 `PAD_INDEX` 選項。  
  
     [!code-sql[IndexDDL#CreateIndex4](../../relational-databases/indexes/codesnippet/tsql/modify-an-index_1.sql)]  
  
     下列範例會使用 ALTER INDEX 設定 `AK_SalesOrderHeader_SalesOrderNumber`索引的幾個選項。  
  
     [!code-sql[IndexDDL#AlterIndex4](../../relational-databases/indexes/codesnippet/tsql/modify-an-index_2.sql)]  
  
#### 若要修改索引資料行  
  
1.  若要加入、移除或變更索引資料行的位置，您必須卸除索引，再重新建立該索引。  
  
## 另請參閱  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [設定索引選項](../../relational-databases/indexes/set-index-options.md)   
 [重新命名索引](../../relational-databases/indexes/rename-indexes.md)  
  
  