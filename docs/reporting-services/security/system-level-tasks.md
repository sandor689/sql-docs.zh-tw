---
title: "系統層級工作 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "系統層級工作 [Reporting Services]"
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
caps.latest.revision: 36
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# 系統層級工作
  系統層級工作是權限的集合，而這些權限與套用至報表伺服器站台整體的作業相關。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 亦包含套用至特定項目的項目層級工作。 如需詳細資訊，請參閱[項目層級工作](../../reporting-services/security/item-level-tasks.md)。 如需工作和權限的一般詳細資訊，請參閱[工作和權限](../../reporting-services/security/tasks-and-permissions.md)。  
  
> [!NOTE]  
>  如果是藉由程式設計來使用這些工作，必須使用支援系統層級工作的方法。 如需詳細資訊，請參閱 <xref:ReportService2010.ReportingService2010.ListTasks%2A> 和 <xref:ReportService2010.ReportingService2010.ListRoles%2A>。  
  
## 系統層級工作中的權限  
 下表識別每一個系統工作的權限集合。 列出的權限僅供參考之用，提供每一個工作可用之功能的更正確說明。  
  
|工作|Permissions|  
|----------|-----------------|  
|執行報表定義|執行報表定義 (權限與工作名稱相同)|  
|產生事件|產生事件|  
|管理作業|讀取系統屬性<br /><br /> 更新系統屬性|  
|管理報表伺服器屬性|讀取系統屬性<br /><br /> 更新系統屬性|  
|管理角色|建立角色<br /><br /> 刪除角色<br /><br /> 讀取角色屬性<br /><br /> 更新角色屬性|  
|管理共用排程|建立排程|  
|管理報表伺服器安全性|讀取系統安全性原則<br /><br /> 更新系統安全性原則|  
|檢視報表伺服器屬性|讀取系統屬性|  
|檢視共用排程|讀取排程|  
  
## 請參閱＜  
 [在原生模式報表伺服器上授與權限](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  