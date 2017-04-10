---
title: "啟動 SQL Server Management Studio | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# 啟動 SQL Server Management Studio
在開始這個教學課程之前，我們先看一下 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。  
  
## 開啟 SQL Server Management Studio  
  
#### 開啟 SQL Server Management Studio  
  
1.  啟動 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] (SSMS) 的方式依據您的作業系統而定。  
* 若是含有 [起始頁] 的較新版本 Windows，請在 [起始頁] 中輸入 **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**，程式隨即出現。 按一下程式以開啟 SSMS。 您可以在程式上按一下滑鼠右鍵，將它釘選到 [起始頁]。   
* 若是舊版 Windows，請在 [開始] 功能表上依序指向 [所有程式] 和 [[!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]，然後按一下 [SQL Server Management Studio]。 或者，您可以在 [執行] 對話方塊中，輸入 **SSMS.exe**，然後按一下 [確定]。  
  
    > [!NOTE]  
    >  如果沒有出現 SSMS，則可能未成功安裝 SSMS。 您可透過[下載中心](https://msdn.microsoft.com/library/mt238290.aspx)來安裝 SSMS。 SSMS 不會與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 一起自動安裝。 若要存取所有功能，請使用最新版本。  
  
2.  在下一個步驟中，您會使用 SSMS 的**物件總管**元件，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如果未顯示物件總管窗格，請在 [檢視] 功能表上，按一下**物件總管**。 在物件總管功能表上，按一下 [連接] 按鈕，再按一下 [Database Engine]。 此時會出現 [連接到伺服器] 對話方塊  (如果您先前已安裝 SSMS，其中的使用者設定可能會讓 [連接到伺服器] 對話方塊自動出現)。  
  
3.  在 [連接到伺服器] 對話方塊中，填妥 [伺服器名稱] 方塊。 您可以連接到三種類型的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 每種類型的 [伺服器名稱] 方塊格式稍微有點不同。 請選擇下列其中一個格式：  
--  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設執行個體：**當您在電腦上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，您可以指定將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體 (未命名的執行個體) 或具名執行個體設為預設值。 如果您要連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設執行個體，請插入電腦的名稱。 例如，如果您在名為 Accounting 的電腦上執行 SSMS，並要連接至安裝在該電腦上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設執行個體，請在 [伺服器名稱] 方塊中輸入 **Accounting**。  
--  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的具名執行個體：**在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間，您可以指定執行個體；例如，在名為 Accounting 的電腦上，您可以指定將具名執行個體命名為 **Receivables**。 若要連接至具名執行個體，請在 [伺服器名稱] 方塊中，輸入電腦名稱、反斜線與執行個體名稱，例如 **Accounting\Receivables**。  
--  **Azure SQL 資料庫︰**SQL 資料庫的伺服器名稱格式是 SQL_Server_name.database.windows.net，例如 **mydb2.database.windows.net**。 如果您無法判斷伺服器名稱，請前往 Azure 入口網站，以了解建立連接字串的說明。  
  
4. 在 [驗證] 區域中  
  
## Management Studio 元件  
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 在特定資訊類型專用的視窗中呈現資訊。 資料庫資訊是顯示在「物件總管」和文件視窗中。  
  
-   物件總管是含有伺服器中所有資料庫物件的樹狀檢視。 其中可包括 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的資料庫。 物件總管含有它所連接的所有伺服器的資訊。 當您開啟 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 時，系統會提示您將物件總管連接到上次使用的設定。 您可以在 [已註冊的伺服器] 元件中，按兩下任何伺服器來連接它，但您不需要註冊要連接的伺服器。  
  
-   文件視窗是 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 最大的部分。 文件視窗可包含查詢編輯器和瀏覽器視窗。 預設會顯示目前電腦中 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體所連接的 [摘要] 頁面。  
  
## 顯示其他視窗  
  
#### 顯示 [已註冊的伺服器] 視窗  
  
1.  在 [檢視] 功能表上，按一下 [已註冊的伺服器]。  
  
    [已註冊的伺服器] 視窗會出現在物件總管的上方或旁邊。 您可以拖曳該視窗，並將它固定至不同的位置。 [已註冊的伺服器] 會列出您經常管理的伺服器。 您可以在這份清單中，新增和移除伺服器。 列出的伺服器只包括您執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之電腦中的 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 執行個體。  
  
2.  如果您的伺服器沒有出現，請在 [已註冊的伺服器] 中，以滑鼠右鍵按一下 [Database Engine]，然後依序按一下 [工作] 和 [更新本機伺服器註冊]。 若要新增其他 SQL Server 或 SQL 資料庫，請在 [已註冊的伺服器] 中的任意位置按一下滑鼠右鍵，然後按一下 [新增伺服器註冊]。 依照之前填妥 [連接到伺服器] 對話方塊的方式，填妥 [登入] 區域。  
  
## 本課程的下一項工作  
[連接已註冊的伺服器和物件總管](../../tools/sql-server-management-studio/connect-with-registered-servers-and-object-explorer.md)  
  