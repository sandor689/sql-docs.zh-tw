---
title: "變更 SQL Server 受管理的執行個體上之公用程式收集組的 Proxy 帳戶 (SQL Server 公用程式) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# 變更 SQL Server 受管理的執行個體上之公用程式收集組的 Proxy 帳戶 (SQL Server 公用程式)
  此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中變更 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 受管理的執行個體上公用程式收集組的 Proxy 帳戶。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### 若要變更 SQL Server 受管理的執行個體上之公用程式收集組的 Proxy 帳戶  
  
1.  從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的受管理的執行個體。  
  
    -   在 SSMS 內的 [公用程式總管] 中，按一下 [受管理的執行個體] 節點。  
  
    -   在 [公用程式總管] 清單檢視中，以滑鼠右鍵按一下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱，然後選取 [移除受管理的執行個體]。 如需詳細資訊，請參閱[從 SQL Server 公用程式中移除 SQL Server 執行個體](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md)。  
  
2.  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內再次註冊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。  
  
    -   在 SSMS 內的 [公用程式總管] 中，以滑鼠右鍵按一下 [受管理的執行個體] 節點，然後選取 [新增受管理的執行個體]。  
  
    -   依照提示完成精靈，指定新的 Proxy 帳戶。  
  
## 另請參閱  
 [SQL Server 公用程式的功能與工作](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [疑難排解 SQL Server 公用程式](../Topic/Troubleshoot%20the%20SQL%20Server%20Utility.md)  
  
  