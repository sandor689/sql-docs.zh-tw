---
title: "教學課程的必要條件 (報表產生器) | Microsoft Docs"
ms.custom: ""
ms.date: "06/15/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: 11
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# 教學課程的必要條件 (報表產生器)
若要執行報表產生器教學課程，您需要能夠在報表伺服器或與報表伺服器整合的 SharePoint 網站上檢視和儲存 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 分頁報表。 針對資料，所有教學課程都使用必須由 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 處理的常值查詢。  
  
如果您沒有報表伺服器或網站或是資料來源的存取權，可以透過建立離線報表來了解報表產生器。 請參閱[教學課程：離線建立快速圖表報表 &#40;報表產生器&#41;](../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md)。  
  
## 需求  
您必須擁有下列必要元件，才能完成報表產生器教學課程：  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 報表產生器的存取權。 您可以從 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] 報表伺服器，或是 SharePoint 整合模式中的 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] 報表伺服器上，執行報表產生器。 只有第一個步驟「如何開啟報表產生器」在不同伺服器上會不同。  
  
    在報表伺服器上，選取 [新增] > [分頁報表]。
  
    在 SharePoint 整合模式的報表伺服器中，於 [文件] 索引標籤上，選取 [新增文件]，然後從下拉式清單中選取 [報表產生器報表]。 例如，`http://<servername>/sites/mySite/reports`。 SharePoint 管理員必須啟用每一個文件庫的 [報表產生器報表] 功能。  
  
-   [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] 報表伺服器或是與 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] 報表伺服器整合之 SharePoint 網站的 URL。 您必須具有權限，才能儲存和檢視報表、共用資料來源、共用資料集、報表組件和模型。 根據預設，報表伺服器的 URL 是 `http://<servername>/reportserver`。 根據預設，SharePoint 網站的 URL 是 `http://<sitename>` 或 `http://<server>/site`。  
  
-   [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 執行個體的名稱，和能夠以唯讀方式存取任何資料庫的認證。 教學課程中的資料集查詢會使用常值資料，但是每一個查詢都必須經過 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 執行個體處理，才能傳回報表資料集所需的中繼資料。 例如，下列連接字串僅指定伺服器：`data source=<servername>`。 您必須由授與您存取此伺服器之權限的系統管理員，指派具有預設資料庫的讀取存取權。 您也可以指定資料庫，如下列連接字串所示：`data source=<servername>;initial catalog=<database>`。  
  
-   針對[地圖報表](Tutorial:%20Map%20Report%20\(Report%20Builder\).md)教學課程，報表伺服器必須設定為支援 Bing Maps 作為背景。 如需詳細資訊，請參閱[對應報表支援規劃](http://msdn.microsoft.com/zh-tw/5ddc97a7-7ee5-475d-bc49-3b814dce7e19)。   

-   [建立鑽研及主報表](Tutorial:%20Creating%20Drillthrough%20and%20Main%20Reports%20\(Report%20Builder\).md)教學課程需要能夠存取 Contoso Sales Cube。 如需詳細資訊，請參閱教學課程。 
  
報表伺服器管理員必須授與您報表伺服器的必要權限、設定 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] 資料夾位置，以及設定報表產生器的預設選項。 如需詳細資訊，請參閱[安裝和解除安裝報表產生器](../Topic/Install%20and%20Uninstall%20Report%20Builder.md)。  
  
## 另請參閱  
[報表產生器教學課程](../reporting-services/report-builder-tutorials.md)  
  