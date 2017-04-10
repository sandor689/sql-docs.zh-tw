---
title: "升級 SQL Server 管理工具 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "管理工具, 升級"
ms.assetid: 1dab50b9-d16c-49a1-9ecc-af72adb6c378
caps.latest.revision: 19
author: "stevestein"
ms.author: "sstein"
manager: "jhubbard"
caps.handback.revision: 19
---
# 升級 SQL Server 管理工具
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 支援從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 及更新版本升級。 本主題說明升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理工具和管理元件 (如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent、Database Mail、維護計畫、XPStar 和 XPWeb) 的支援與行為。  
  
> [!IMPORTANT]  
>  若是本機安裝，您必須以管理員身分執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式。 如果您是從遠端共用位置執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式，則必須使用對遠端共用位置具有讀取和執行權限的網域帳戶。  
  
## 已知的升級問題  
 在您升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之前，請先考慮以下問題：  
  
### 如果是全部升級狀況：  
  
-   在升級 MSX 伺服器之前，應該要升級所有的 TSX 伺服器。 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中 MSX/TSX 的詳細資訊，請參閱[將整個企業的管理自動化](../../ssms/agent/automated-administration-across-an-enterprise.md)。  
  
-   您必須同時升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的所有元件。 在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體內， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]元件的版本號碼都必須相同。  
  
-   當您升級到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，可以將元件加入到現有的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝。 如需詳細資訊，請參閱[使用安裝精靈升級為 SQL Server 2016 &#40;安裝程式&#41;](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md)。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端工具 (例如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor、sqlcmd 和 osql) 不會升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。 用戶端工具改為使用舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的工具進行並存執行。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 支援從舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端工具匯入設定。  
  
-   在升級期間，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的驗證將會更新為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證到 Windows 驗證。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中不支援 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]驗證。  
  
-   在升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的期間，將會保留作業與警示的資料。  
  
-   如果要升級的執行個體上有使用 SQLMail，關聯的 XP 將會在升級之後受到支援並啟用。 否則會將其關閉。  
  
-   Database Mail (也稱為 SQLiMail) 將會與 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]元件一起升級。 根據預設，Database Mail 將會在升級之後關閉。 任何結構描述更新都應該在升級之後與更新指令碼一致。  
  
## 另請參閱  
 [支援的版本與版本升級](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [回溯相容性_已刪除](../Topic/Backward%20Compatibility_deleted.md)   
 [使用安裝精靈升級為 SQL Server 2016 &#40;安裝程式&#41;](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md)  
  
  