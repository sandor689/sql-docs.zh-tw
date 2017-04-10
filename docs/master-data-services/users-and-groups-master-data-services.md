---
title: "使用者和群組 (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "使用者 [Master Data Services]"
  - "群組 [Master Data Services]"
  - "使用者 [Master Data Services], 關於使用者"
  - "群組 [Master Data Services], 關於群組"
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# 使用者和群組 (Master Data Services)
  若要存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式，使用者必須擁有 Windows 網域帳戶或安裝 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 之伺服器電腦上的帳戶。 若要授與 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]存取權，您可以執行下列其中一項作業：  
  
-   將使用者帳戶新增至網域或本機群組，然後將群組新增至 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的群組清單。  
  
-   將使用者帳戶新增至 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的使用者清單。  
  
    > [!NOTE]  
    >  如果使用者屬於可存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的群組，則在第一次存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 或 MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 時，使用者的名稱會自動新增至使用者清單。  
  
 若要在 UI 的 [總管] 功能區域內執行動作，群組或使用者必須獲得指派 [總管] 功能區域存取權以及模型物件權限。  
  
 如果使用者或群組需要存取其他功能區域，使用者或群組必須獲得指派取得特定功能區域的存取權。  
  
## 最佳作法  
 若要簡化管理，請建立群組，然後指派每個群組的功能區域和模型物件權限。 您即可在群組中新增及移除使用者，而不需存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] UI。  
  
 請勿指派其他權限給個別使用者，也不要在具有 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]存取權的多個群組中加入使用者。 此外，除非您希望群組擁有特定成員的受限存取權，否則請勿使用階層成員權限。  
  
## 另請參閱  
 [新增使用者 &#40;Master Data Services&#41;](../master-data-services/add-a-user-master-data-services.md)   
 [新增群組 &#40;Master Data Services&#41;](../master-data-services/add-a-group-master-data-services.md)   
 [刪除使用者或群組 &#40;Master Data Services&#41;](../master-data-services/delete-users-or-groups-master-data-services.md)   
 [測試使用者的權限 &#40;Master Data Services&#41;](../master-data-services/test-a-user-s-permissions-master-data-services.md)  
  
  