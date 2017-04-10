---
title: "MSSQL_REPL027056 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL027056 錯誤"
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027056
    
## 訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|27056|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|合併處理無法變更生成集記錄 '%1'。 執行疑難排解時，以詳細資訊記錄重新啟動同步處理，並指定要寫入的輸出檔案。|  
  
## 說明  
 這個錯誤通常由成長過大之合併式複寫系統資料表中的競爭問題引起。 大型系統資料表通常是由較長的發行集保留期限所引起，因為在達到保留期限之前，中繼資料必須儲存於這些資料表中。  
  
## 使用者動作  
 **若要解決這個問題：**  
  
1.  減少的值-**DownloadGenerationsPerBatch** 和 **-UploadGenerationsPerBatch** 參數合併代理程式以便處理繼續進行，同時您在解決基礎問題造成此錯誤。 可於代理程式設定檔和命令列中指定代理程式參數。 如需詳細資訊，請參閱：  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [檢視及修改複寫代理程式命令提示字元參數 & #40。SQL Server Management Studio & #41;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [複寫代理程式可執行檔概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)。  
  
2.  為發行集保留期限指定儘可能低的設定。 如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)。  
  
3.  合併式複寫維護的一部分，偶爾會檢查與合併式複寫相關的系統資料表的成長︰ **MSmerge_contents**, ，**MSmerge_genhistory**, ，和 **MSmerge_tombstone**, ，**MSmerge_current_partition_mappings**, ，和 **MSmerge_past_partition_mappings**。 定期重新整理資料表的索引。 如需詳細資訊，請參閱 [重新組織與重建索引](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)。  
  
## 另請參閱  
 [錯誤和事件參考 & #40。複寫 & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  