---
title: 角色定義 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- roles [Reporting Services], security
- security [Reporting Services], role definitions
- role-based security [Reporting Services], role definitions
ms.assetid: d1b8dbf0-4462-402e-92dd-0e4835002b6e
caps.latest.revision: 43
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 03d3bc951a76b6ff3fdf088999777d80f699f690
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282664"
---
# <a name="role-definitions"></a>角色定義
  在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中，*角色**定義*是一個具名的工作集合，這些工作會定義可在報表伺服器上執行的作業。 角色定義會提供報表伺服器用來強制執行安全性的規則。 當使用者嘗試執行工作 (例如發行報表) 時，報表伺服器就會檢查使用者的角色指派，以便判斷工作是否包含在其角色定義中。 如果工作包括在角色定義中，便會提交要求。  
  
## <a name="using-roles-to-authorize-access-to-a-report-server"></a>使用角色來授權報表伺服器的存取權  
 當角色用於角色指派時，角色才成為可以作業。 如需有關角色如何提供安全性的詳細資訊，請參閱 <<c0> [ 角色指派](role-assignments.md)。  
  
## <a name="types-of-role-definitions"></a>角色定義的類型  
 角色定義是項目層級或系統層級定義。 「項目層級角色定義」會描述與報表伺服器上儲存和管理之項目 (例如報表、資料夾和模型) 相關的工作。 管理報表、檢視資料夾和管理個別訂閱都是您可以包含在項目層級角色定義中的工作範例。 「系統角色定義」包含套用至整個網站的工作。 檢視報表伺服器屬性是您可能會包含在系統角色中的工作範例。  
  
## <a name="predefined-roles"></a>Predefined Roles  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 包括一些對應至不同使用者互動層級的預先定義角色。 下列清單含有您可以使用的預先定義角色：  
  
-   「內容管理員」、「發行者」、「瀏覽者」、「報表產生器」和「我的報表」都是您可以在建立存取報表伺服器內容之角色指派時使用的項目層級角色定義。  
  
-   「系統管理員」和「系統使用者」是您可以用來授權站台作業存取權的系統層級角色定義。  
  
 如需詳細資訊，請參閱 <<c0> [ 預先定義的角色](role-definitions-predefined-roles.md)。  
  
## <a name="creating-a-role-definition"></a>建立角色定義  
 若要建立角色，請使用 Management Studio 來指定名稱以及它所包含的工作。 您必須針對項目和系統工作建立不同的角色定義。 角色可以包含項目層級工作或系統層級工作，但是不能同時包含兩者。 建立角色定義包括提供一個名稱，以及選擇一組定義的工作。 若要建立角色定義，您必須要有相關的權限。 「設定個別項目的安全性」工作會提供這些權限。 依預設，指派至預先定義之 **內容管理員** 角色的使用者和管理員，可以執行此工作。  
  
 角色必須有唯一的名稱。 有效的角色定義，至少必須包含一項工作。 如需詳細資訊，請參閱 <<c0> [ 工作和權限](tasks-and-permissions.md)。  
  
 若要建立角色定義，請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 建立、 刪除或修改角色&#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md)。</c0>  
  
 建立角色定義之後，您可以在角色指派中選取該定義，藉以使用它。 如需詳細資訊，請參閱[將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](grant-user-access-to-a-report-server.md)。  
  
## <a name="customize-or-delete-a-role-definition"></a>自訂或刪除角色定義  
 您可以修改預先定義的角色，也可以使用自訂角色來取代它們。 若要修改角色，請在角色定義中加入或移除工作。 但是，您無法重新命名角色。 您所做的任何變更都會立即套用至包含該角色定義的所有角色指派。  
  
 如果您不要再使用某個角色定義，就可以刪除它。 只要已啟用 [我的報表] 功能，便無法刪除為 [我的報表] 功能選取的角色定義。 在刪除用於 [我的報表] 的角色定義之前，您必須先停用該功能，或者選取其他角色定義。  
  
## <a name="see-also"></a>另請參閱  
 [工作和權限](tasks-and-permissions.md)   
 [在原生模式報表伺服器上授與權限](granting-permissions-on-a-native-mode-report-server.md)   
 [建立、刪除或修改角色 &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md)   
 [將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](grant-user-access-to-a-report-server.md)   
 [修改或刪除角色指派 &#40;報表管理員&#41;](role-assignments-modify-or-delete.md)   
 [設定 SharePoint 網站上的報表伺服器項目的權限&#40;Reporting Services SharePoint 整合模式&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md)  
  
  
