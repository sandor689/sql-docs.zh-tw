---
title: "MSSQL_ENG021330 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG021330 錯誤"
ms.assetid: e2bb2e21-62a7-4689-b68b-bdfba3fdd985
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG021330
    
## 訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|21330|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|無法在複寫工作目錄下建立子目錄。(%ls)|  
  
## 說明  
 手動初始化訂閱時可能發生此錯誤，同時建立用於儲存複寫指令碼的目錄時會出現問題。 錯誤可能是權限問題所造成：當訂閱沒有使用快照集初始化，在發行者端執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶，就必須要有散發者端之快照集資料夾的寫入權限。  
  
## 使用者動作  
 請確定指定的快照集資料夾路徑正確，而且在發行者端執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶具有足夠的權限。  
  
## 另請參閱  
 [指定預設快照集位置 & #40。SQL Server Management Studio & #41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [錯誤和事件參考 & #40。複寫 & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [不使用快照集初始化交易式訂閱](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  