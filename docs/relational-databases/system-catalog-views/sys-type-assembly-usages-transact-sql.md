---
title: sys.type_assembly_usages (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.type_assembly_usages
- sys.type_assembly_usages_TSQL
- type_assembly_usages_TSQL
- type_assembly_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.type_assembly_usages catalog view
ms.assetid: 79b8bf25-6e4e-4a07-ae93-7a4e44f65171
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 957820cc4bb5ee5e4a2f0f403f054fba7b205d78
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219879"
---
# <a name="systypeassemblyusages-transact-sql"></a>sys.type_assembly_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對每個組件參考類型，各包含一個資料列。  
  

  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**user_type_id**|**int**|類型的識別碼。<br /><br /> 若要傳回的型別名稱，加入[sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)目錄檢視這個資料行。|  
|**assembly_id**|**int**|組件的識別碼|  
  
## <a name="permissions"></a>Permissions  
 需要 **public** 角色中的成員資格。 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [純量類型目錄檢視&#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;。TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
