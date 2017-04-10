---
title: "設定 two digit year cutoff 伺服器組態選項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "two digit year cutoff 選項"
  - "四位數年份 [SQL Server]"
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# 設定 two digit year cutoff 伺服器組態選項
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] two digit year cutoff [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。 [兩位數年份的截止] 選項會指定從 1753 到 9999 之間的整數，以代表將兩位數年份解譯為四位數年份時的截止年份 (Cutoff Year)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設時間範圍為 1950-2049，代表截止年份為 2049。 這表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會自動把兩位數字年份 49 解譯為 2049，兩位數字年份 50 解譯為 1950，兩位數字年份 99 解譯為 1999。 若要維持回溯相容性，請保留預設值。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [建議](#Recommendations)  
  
     [安全性](#Security)  
  
-   **使用下列方法設定 two digit year cutoff 選項：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **待處理**  [設定 two digit year cutoff 選項之後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Recommendations"></a> 建議  
  
-   這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。  
  
-   OLE Automation 物件使用 2030 年做為兩位數截止年份。 您可以使用 **two digit year cutoff** 選項在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和用戶端應用程式之間提供一致的日期值。 但為避免模稜兩可的日期，資料中應使用四位數的年份。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 依預設，所有使用者都會取得不含參數或只含第一個參數之 **sp_configure** 的執行權限。 若要執行同時設定了兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式，使用者必須取得 ALTER SETTINGS 伺服器層級權限。 **系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### 若要設定 two digit year cutoff 選項  
  
1.  在 [物件總管] 中，以滑鼠右鍵按一下伺服器，然後選取 [屬性]。  
  
2.  按一下 **[其他伺服器設定]** 節點。  
  
3.  在 [Two digit year support (兩位數年份支援)] 下的 [當輸入兩位數年份時，解譯為下列之間的年份] 方塊中，輸入或選取一個值作為時間範圍的結束年份。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### 若要設定 two digit year cutoff 選項  
  
1.  連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。 此範例示範如何使用 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) 將 `two digit year cutoff`選項的值設定為 `2030`。  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 如需詳細資訊，請參閱[伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)。  
  
##  <a name="FollowUp"></a> 待處理：設定 two digit year cutoff 選項之後  
 設定會立即生效，不需要重新啟動伺服器。  
  
## 另請參閱  
 [伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  