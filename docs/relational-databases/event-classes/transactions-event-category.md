---
title: "Transaction 事件類別目錄 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server 事件類別, Transactions 事件類別目錄"
  - "事件類別 [SQL Server], Transactions 事件類別目錄"
  - "Transaction 事件類別目錄 [SQL Server]"
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# Transaction 事件類別目錄
  **Transactions** 事件類別可以用來監視交易狀態。 以 **TM:** 作為前置詞的事件類別名稱是用來追蹤與交易相關的作業，這些作業是透過交易管理介面來傳送。  
  
## 本節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[DTCTransaction 事件類別](../../relational-databases/event-classes/dtctransaction-event-class.md)|追蹤 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散式交易協調器 (MS DTC) 所協調的交易。 這些是散發於 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的二或多個資料庫或執行個體之間的交易。|  
|[SQLTransaction 事件類別](../../relational-databases/event-classes/sqltransaction-event-class.md)|追蹤 [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN、COMMIT TRAN、SAVE TRAN 與 ROLLBACK TRAN 陳述式。|  
|[TM: Begin Tran Completed 事件類別](../../relational-databases/event-classes/tm-begin-tran-completed-event-class.md)|表示已完成 BEGIN TRANSACTION 要求。|  
|[TM: Begin Tran Starting 事件類別](../../relational-databases/event-classes/tm-begin-tran-starting-event-class.md)|表示正在啟動 BEGIN TRANSACTION 要求。|  
|[TM: Commit Tran Completed 事件類別](../../relational-databases/event-classes/tm-commit-tran-completed-event-class.md)|表示已完成 COMMIT TRANSACTION 要求。|  
|[TM: Commit Tran Starting 事件類別](../../relational-databases/event-classes/tm-commit-tran-starting-event-class.md)|表示正在啟動 COMMIT TRANSACTION 要求。|  
|[TM: Promote Tran Completed 事件類別](../../relational-databases/event-classes/tm-promote-tran-completed-event-class.md)|表示已完成 PROMOTE TRANSACTION 要求。|  
|[TM: Promote Tran Starting 事件類別](../../relational-databases/event-classes/tm-promote-tran-starting-event-class.md)|表示正在啟動 PROMOTE TRANSACTION 要求。|  
|[TM: Rollback Tran Completed 事件類別](../../relational-databases/event-classes/tm-rollback-tran-completed-event-class.md)|表示已完成 ROLLBACK TRANSACTION 要求。|  
|[TM: Rollback Tran Starting 事件類別](../../relational-databases/event-classes/tm-rollback-tran-starting-event-class.md)|表示正在啟動 ROLLBACK TRANSACTION 要求。|  
|[TM: Save Tran Completed 事件類別](../../relational-databases/event-classes/tm-save-tran-completed-event-class.md)|表示已完成 SAVE TRANSACTION 要求。|  
|[TM: Save Tran Starting 事件類別](../../relational-databases/event-classes/tm-save-tran-starting-event-class.md)|表示正在啟動 SAVE TRANSACTION 要求。|  
|[TransactionLog 事件類別](../../relational-databases/event-classes/transactionlog-event-class.md)|追蹤交易何時寫入資料庫交易記錄檔。|  
  
  