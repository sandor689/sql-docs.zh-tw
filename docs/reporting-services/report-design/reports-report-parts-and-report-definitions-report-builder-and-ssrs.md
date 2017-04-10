---
title: "報表、報表組件和報表定義 (報表產生器及 SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "報表定義"
  - "報表"
ms.assetid: 2d746550-f8cc-4e97-8a06-d0f03cffc18d
caps.latest.revision: 26
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 26
---
# 報表、報表組件和報表定義 (報表產生器及 SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 會使用各種詞彙來描述不同狀態的分頁報表，這些狀態包括初始定義、已發行的報表以及使用者檢視的報表。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 報表定義 (.rdl) 檔案  
 報表定義是您在報表產生器或報表設計師中建立的檔案。 它提供資料來源連接、用於擷取資料之查詢、運算式、參數、影像、文字方塊、資料表，以及您可能包含在報表中之其他任何設計階段元素的完整描述。 雖然報表定義可以很複雜，不過它至少會指定查詢和其他報表內容、報表屬性，以及報表配置。  
  
 報表定義會在執行階段轉譯成已處理的報表。 這時候，系統會從資料來源中擷取資料，並且根據報表定義中的指示格式化這項資料。 您可以直接從電腦執行報表定義並儲存在本機，也可以將它發行到報表伺服器，讓其他人執行。  
  
 報表定義是以符合 XML 文法 (稱為報表定義語言 (RDL)) 的 XML 所撰寫。 RDL 描述 XML 元素，包含報表可能出現的所有可能變化。  
  
## 用戶端報表定義 (.rdlc) 檔案  
 Visual Studio 報表設計師會產生可搭配 ReportViewer 控制項使用的用戶端報表定義 (.rdlc) 檔案。 這些 .rdlc 檔案可轉換成 .rdl 檔案，以搭配 Reporting Services 報表設計師使用。  
  
## 報表組件檔 (.rsc)  
 報表組件是指儲存在報表伺服器上的獨立報表項目，而且可以包含在其他報表中。 使用報表產生器來瀏覽並從 [報表組件庫] 中選取要加入至報表的組件。 您可以使用報表設計師或報表產生器來儲存報表組件，以便用於報表組件庫。  
  
 報表組件定義是報表定義檔的 XML 片段。 您可藉由建立報表定義，然後選取報表中的報表項目個別發行為報表組件，藉此建立報表組件。 報表組件包括資料區、矩形與其包含的項目，以及影像。 您可以將報表組件與其相依的資料集和共用資料來源參考一併儲存，以便於其他報表中重複使用。  
  
 如需詳細資訊，請參閱[報表組件 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/report-parts-report-builder-and-ssrs.md) 和[報表設計師中的報表組件 &#40;SSRS&#41;](../../reporting-services/report-design/report-parts-in-report-designer-ssrs.md)。  
  
## 已發行的報表  
 建立 .rdl 檔案之後，您就可以將它儲存在本機，也可以將它儲存至報表伺服器上的個人資料夾 (例如 [我的報表] 資料夾)。 報表可供其他人查看時，可以將它從報表產生器儲存到報表伺服器上的公用資料夾，然後透過 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web 入口網站上傳或是從報表設計師部署報表專案方案的方式來發行該報表。 已發行的報表是儲存在報表伺服器資料庫中，並在報表伺服器或 SharePoint 網站上管理的項目。  
  
 已發行的報表會透過使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以角色為基礎之安全性模型的角色指派來維護其安全。 您可以透過 URL、SharePoint Web 組件或 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web 入口網站存取已發行的報表，也可以在報表產生器中巡覽並開啟它們。  
  
### 報表快照集  
 您也可以將報表當做快照集來發行 (其中包含報表一開始執行時的配置資訊和資料)。 報表快照集不會以特定轉譯格式儲存。 而是只有在使用者或應用程式要求它時，報表快照集才以最後的檢視格式轉譯 (例如 HTML)。 如需詳細資訊，請參閱[在報表管理員中尋找及檢視報表 &#40;報表產生器及 SSRS&#41;](https://msdn.microsoft.com/library/dd255286.aspx)。  
  
## 已轉譯的報表  
 已轉譯的報表是一種完全處理的報表，其中包含採用適合檢視之格式 (例如 HTML) 的資料與配置資訊。 報表要等到轉譯成輸出格式後，才能夠檢視。 您可以執行下列任一種動作來轉譯報表：  
  
-   在報表產生器或報表設計師中建立或開啟報表並且執行它。  
  
-   在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web 入口網站中尋找並執行報表。  
  
-   在與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器整合的 SharePoint 網站上尋找並執行報表。  
  
-   訂閱報表，訂閱的報表會以您指定的輸出格式傳遞到電子郵件收件匣或檔案共用。  
  
 訂閱報表，訂閱的報表會以您指定的輸出格式傳遞到電子郵件收件匣或檔案共用。 報表的預設轉譯格式為 HTML 4.0。 除了 HTML 以外，報表還可以使用許多輸出格式轉譯，包括 Excel、Word、XML、PDF、TIFF 與 CSV。 如同已發行的報表一樣，已轉譯的報表也無法編輯或回存到報表伺服器。 如需詳細資訊，請參閱[匯出報表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)。  
  
## 請參閱＜  
 [報表撰寫概念 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/report-authoring-concepts-report-builder-and-ssrs.md)   
 [SQL Server 2016 的報表產生器](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
 [尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [匯出報表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)  
  
  