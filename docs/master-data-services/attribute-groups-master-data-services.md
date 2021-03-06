---
title: 屬性群組 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services]
- attribute groups [Master Data Services], about attribute groups
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 28160712fc1574f0f8359fca3ef3fa239117f509
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2018
ms.locfileid: "35328112"
---
# <a name="attribute-groups-master-data-services"></a>屬性群組 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，屬性群組有助於組織實體中的屬性。 當實體包含多個屬性時，屬性群組可改善實體在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中顯示的方式。  
  
## <a name="how-attribute-groups-change-the-display"></a>屬性群組如何變更顯示  
 屬性群組會以方格上方的索引標籤形式顯示在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的 [總管] 功能區域。  
  
 如果實體有大量屬性，當您在 [總管] 的方格中檢視該實體時，必須捲動至右方，才能檢視所有屬性。 若要避免此捲動，您可以建立屬性群組。  
  
-   屬性群組永遠包含 Name 和 Code 屬性。  
  
-   實體的每個屬性可以屬於一個或多個屬性群組。  
  
-   所有屬性都會自動包含在 [總管] 的 [所有屬性] 索引標籤上。  
  
-   沒有方法可以隱藏 [所有屬性] 索引標籤。  
  
 屬性群組是在[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]的 [系統管理] 功能區域中管理的。  
  
## <a name="show-or-hide-attribute-groups"></a>顯示或隱藏屬性群組  
 當您建立屬性群組時，它會自動隱藏起來不讓所有使用者看到，除了建立它的使用者以外。 如需如何顯示此群組的詳細資訊，請參閱 [讓使用者看到屬性群組 &#40;Master Data Services&#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)。  
  
 如果您想要隱藏群組中的特定屬性，您可以將 **拒絕** 權限指派給此屬性。 如需詳細資訊，請參閱[分葉權限 &#40;Master Data Services&#41;](../master-data-services/leaf-permissions-master-data-services.md)。  
  
## <a name="related-tasks"></a>相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|建立新的屬性群組並加入屬性。|[建立屬性群組 &#40;Master Data Services&#41;](../master-data-services/create-an-attribute-group-master-data-services.md)|  
|讓使用者看到屬性群組。|[讓使用者看到屬性群組 &#40;Master Data Services&#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)|  
|變更現有屬性群組的名稱。|[變更屬性群組名稱 &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|刪除現有屬性群組。|[刪除屬性群組 &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## <a name="related-content"></a>相關內容  
  
-   [屬性 &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  
