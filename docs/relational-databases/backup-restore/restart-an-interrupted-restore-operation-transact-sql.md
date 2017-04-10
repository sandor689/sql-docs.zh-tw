---
title: "重新啟動中斷的還原作業 (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中斷的還原作業"
  - "還原資料庫 [SQL Server], 重新啟動中斷的作業"
  - "備份後重設已變更的選項"
  - "資料庫還原 [SQL Server], 重新啟動中斷的作業"
  - "重新啟動中斷的還原作業"
  - "還原中斷的作業 [SQL Server]"
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# 重新啟動中斷的還原作業 (Transact-SQL)
  此主題說明如何重新啟動被中斷的還原作業。  
  
### 若要重新啟動被中斷的還原作業  
  
1.  再執行一次被中斷的 RESTORE 陳述式，並指定下列項目：  
  
    -   與原始 RESTORE 陳述式相同的子句。  
  
    -   RESTART 子句。  
  
## 範例  
 此範例會重新啟動被中斷的還原作業。  
  
```tsql  
-- Restore a full database backup of the AdventureWorks database.  
RESTORE DATABASE AdventureWorks  
   FROM DISK = 'C:\AdventureWorks.bck'  
GO  
-- The restore operation halted prematurely.  
-- Repeat the original RESTORE statement specifying WITH RESTART.  
RESTORE DATABASE AdventureWorks   
   FROM DISK = 'C:\AdventureWorks.bck'  
   WITH RESTART  
GO  
```  
  
## 另請參閱  
 [完整的資料庫還原 &#40;完整復原模式&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [完整資料庫還原 &#40;簡單復原模式&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  