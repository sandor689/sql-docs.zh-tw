---
title: "保護共用資料來源項目的安全 | Microsoft Docs"
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
  - "共用資料來源 [Reporting Services]"
  - "資料來源 [Reporting Services], 共用"
  - "安全性 [Reporting Services], 資料來源"
ms.assetid: 7299e498-0a1a-4821-a22a-5199bb773ce0
caps.latest.revision: 35
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 35
---
# 保護共用資料來源項目的安全
  您可以在共用資料來源項目上設定安全性，以啟用或停用它的存取權。  
  
 對共用資料來源有最小存取權的使用者 (例如，透過「瀏覽者」角色授與的存取權)，只要也得到檢視報表本身的授權，就可以檢視使用項目的報表清單。  
  
 擁有更多存取權 (例如，透過「內容管理員」角色授與) 的使用者，可以檢視和設定共用資料來源的屬性。  
  
 若要設定安全性，您可以建立角色指派來指定哪些使用者或群組帳戶可以存取共用資料來源。 擁有共用資料項目之存取權的使用者可以變更它的名稱、描述、連接字串或認證資訊。  
  
## 工作與項目的存取  
 建立角色指派時，使用擁有這些工作的角色，以指定適當的權限給使用者和群組。  
  
|選取的工作|授與的權限|  
|----------------------|---------------------------------|  
|檢視資料來源|檢視資料夾階層中的共用資料來源項目。 如果沒有此工作，使用者看不到項目，也許不知道有資料來源可以使用。|  
|管理資料來源|檢視指定名稱、描述和連接資訊的屬性。 此工作也會用來顯示資料夾階層中的共用資料來源項目。 如果您選擇此工作，可以省略「檢視資料來源」工作。|  
|設定項目安全性|建立和修改控制共用資料來源之存取權的角色指派。 此工作必須用於「檢視資料來源」或「管理資料來源」工作。 如果不是，則因為使用者無法選取項目，而沒有作用。|  
  
## 請參閱＜  
 [管理報表資料來源](../../reporting-services/report-data/manage-report-data-sources.md)   
 [保護資料夾的安全](../../reporting-services/security/secure-folders.md)   
 [保護報表和資源的安全](../../reporting-services/security/secure-reports-and-resources.md)   
 [在原生模式報表伺服器上授與權限](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Store Credentials in a Reporting Services Data Source](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md)  
  
  