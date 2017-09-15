---
title: "如何決定權限 (Master Data Services) |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [Master Data Services], determining permissions
ms.assetid: 1dc0b43a-d023-4e7d-b027-8b1459fd058c
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b31073cdf3c4b925bbf3687e3b70e3384ac90cce
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="how-permissions-are-determined-master-data-services"></a>如何決定權限 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，若要以最簡單的方式來設定安全性，可將模型物件權限指派給群組 (使用者為其中的成員)。  
  
 在下列情況中，安全性會變得較複雜：  
  
-   同時指派了模型物件和階層成員權限。  
  
-   使用者屬於群組，而權限同時指派給使用者和群組。  
  
-   使用者屬於群組，而權限指派給多個群組。  
  
## <a name="permissions-assigned-to-a-single-group-or-user"></a>指派給單一群組或使用者的權限  
 如果您將權限指派給單一群組或使用者，系統就會根據下列工作流程決定權限。  
  
 ![mds_conc_security_no_overlap](../master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")  
  
### <a name="step-1-effective-attribute-permissions-are-determined"></a>步驟 1：決定有效屬性權限。  
 下列清單描述的是如何決定有效屬性權限：  
  
-   指派給模型物件的權限會決定使用者可存取的屬性。  
  
-   所有模型物件都會自動從模型結構中較高層級的最接近物件繼承權限。  
  
-   隱含拒絕與實體位於相同層級的任何物件。  
  
-   位於較高層級的任何物件會獲得推斷讀取權限。 如需推斷讀取權限的詳細資訊，請參閱 [導覽存取權 &#40;Master Data Services&#41;](../master-data-services/navigational-access-master-data-services.md)。  
  
 在此範例中，**讀取**權限會指派給實體，而且其屬性 (位於模型結構中較低層級) 會繼承該權限。 模型會提供推斷讀取權限給此實體及其屬性。 模型中的其他實體沒有被指派任何明確權限，而且沒有繼承任何權限，因此會隱含拒絕此實體。  
  
 ![mds_conc_inheritance_model](../master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
### <a name="step-2-if-hierarchy-member-permissions-are-assigned-effective-member-permissions-are-determined"></a>步驟 2：如果已指派階層成員權限，就會決定有效成員權限。  
 下列清單描述的是如何決定有效階層成員權限：  
  
-   指派給階層節點的權限會決定使用者可存取的成員。  
  
-   階層中的所有節點都會自動從階層結構中較高層級的最接近物件繼承權限。  
  
-   隱含拒絕位於相同層級的任何節點。  
  
-   隱含拒絕沒有被指派權限而且位於較高層級的任何節點。  
  
 在此範例中， **讀取** 權限會指派給階層的某個節點，而且位於階層結構中較低層級的節點會繼承該權限。 根目錄沒有被指派權限，因此會隱含拒絕此根目錄。 階層結構中的其他節點沒有被指派任何明確權限，而且沒有繼承任何權限，因此會隱含拒絕此節點。  
  
 ![mds_conc_inheritance_hierarchy](../master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")  
  
### <a name="step-3-the-intersection-of-attribute-and-member-permissions-is-determined"></a>步驟 3：決定屬性與成員權限的交集。  
 如果有效屬性權限與有效成員權限不同，就必須針對每個個別屬性值決定權限。 如需詳細資訊，請參閱 [重疊的模型和成員的權限 &#40;Master Data Services&#41;](../master-data-services/overlapping-model-and-member-permissions-master-data-services.md)。  
  
## <a name="permissions-assigned-to-multiple-groups"></a>指派給多個群組的權限  
 如果使用者屬於一個或多個群組，而且權限同時指派給使用者和群組，則工作流程會變得較複雜。  
  
 ![mds_conc_security_group_overlap](../master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")  
  
 在此情況下，您必須先解析重疊的使用者和群組權限，然後才能比較模型物件與階層成員權限。 如需詳細資訊，請參閱 [重疊的使用者和群組的權限 &#40;Master Data Services&#41;](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 [重疊的使用者和群組的權限 &#40;Master Data Services&#41;](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md)   
 [重疊的模型和成員的權限 &#40;Master Data services&#41;](../master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  