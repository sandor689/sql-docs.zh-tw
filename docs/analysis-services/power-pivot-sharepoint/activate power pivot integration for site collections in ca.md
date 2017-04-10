---
title: "在管理中心為網站集合啟用 Power Pivot 功能整合 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# 在管理中心為網站集合啟用 Power Pivot 功能整合
  如果您使用 [現有的伺服陣列] 安裝選項來安裝 SQL Server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint，就需要為特定的網站集合啟用 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 功能整合。 如果您已使用 [新的伺服器] 選項來安裝 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint，您可以略過這項工作，因為 SQL Server 安裝程式已經在設定部署時，針對根網站集合啟用 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 功能整合。  
  
 網站集合層級的功能啟用對於將應用程式頁面和範本提供給網站使用 (包括排程資料重新整理的組態頁面，以及 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 圖庫和資料摘要文件庫的應用程式頁面) 是必要的。  
  
 您必須為每個支援 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 查詢處理的網站集合啟用 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 整合。  
  
## 必要條件  
 您必須是網站集合管理員。  
  
## 啟動 Power Pivot 功能  
  
1.  按一下 SharePoint 網站上的 [網站動作]。  
  
     根據預設，SharePoint Web 應用程式會經由通訊埠 80 進行存取。 這表示您通常可以藉由輸入 http://\<電腦名稱> 來存取 SharePoint 網站，以開啟根網站集合。  
  
2.  按一下 **[站台設定]**。  
  
3.  按一下 [網站集合管理] 中的 [網站集合功能]。  
  
4.  向下捲動頁面，直到您找到 [[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 整合網站集合功能]。  
  
5.  按一下 **[啟用]**。  
  
6.  開啟每個網站並按一下 [網站動作]，為其他網站集合重複執行。  
  
## 請參閱＜  
 [管理中心的 PowerPivot 伺服器管理和組態](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [初始組態 (Power Pivot for SharePoint)](http://msdn.microsoft.com/zh-tw/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)   
 [Power Pivot for SharePoint 2010 安裝](http://msdn.microsoft.com/zh-tw/8d47dde7-c941-4280-a934-e2fe3f9a938f)  
  
  