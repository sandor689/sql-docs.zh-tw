---
title: syscollector_collection_sets (TRANSACT-SQL) |Microsoft 文件
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
- syscollector_collection_sets_TSQL
- syscollector_collection_sets
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_collection_sets view
ms.assetid: db0def92-f25b-45da-9709-eab972b33800
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7407828836e4831e313e982111df7f61bd110e8e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33221139"
---
# <a name="syscollectorcollectionsets-transact-sql"></a>syscollector_collection_sets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  提供收集組的相關資訊，包括排程、收集模式及其狀態。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|collection_set_id|**int**|收集組的本機識別碼。 不可為 Null。|  
|collection_set_uid|**uniqueidentifier**|收集組的全域唯一識別碼。 不可為 Null。|  
|name|**nvarchar(4000)**|收集組的名稱。 可為 Null。|  
|target|**nvarchar(max)**|識別收集組的目標。 可為 Null。|  
|is_system|**bit**|開啟 (1) 表示收集組是由資料收集器提供，而關閉 (0) 則表示之後由 dc_admin 加入。 這可能是本廠開發或由協力廠商開發的自訂收集組。 不可為 Null。|  
|is_running|**bit**|指出收集組是否正在執行。 不可為 Null。|  
|collection_mode|**smallint**|指定收集組的收集模式。 不可為 Null。<br /><br /> 收集模式是下列其中一種模式：<br /><br /> 0 - 快取模式。 資料收集和上傳會依照不同的排程。<br /><br /> 1 - 非快取模式。 資料收集和上傳會依照相同的排程。|  
|proxy_id|**int**|識別用來執行收集組作業步驟的 Proxy。 可為 Null。|  
|schedule_uid|**uniqueidentifier**|提供指向收集組排程的指標。 可為 Null。|  
|collection_job_id|**uniqueidentifier**|識別收集作業。 可為 Null。|  
|upload_job_id|**uniqueidentifier**|識別收集上傳作業。 可為 Null。|  
|logging_level|**smallint**|指定記錄層次 (0、1 或 2)。 不可為 Null。|  
|days_until_expiration|**smallint**|這是已收集之資料儲存在管理資料倉儲中的天數。 不可為 Null。|  
|description|**nvarchar(4000)**|描述收集組。 可為 Null。|  
|dump_on_any_error|**bit**|開啟 (1) 或關閉 (0) 來指出是否要建立[!INCLUDE[ssIS](../../includes/ssis-md.md)]傾印檔案，在發生任何錯誤。 不可為 Null。|  
|dump_on_codes|**nvarchar(max)**|包含用來觸發傾印檔案的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 錯誤碼清單。 可為 Null。|  
  
## <a name="permissions"></a>Permissions  
 需要 dc_operator 或 dc_proxy 的 SELECT。  
  
## <a name="remarks"></a>備註  
 資料收集器 API 僅允許您變更或刪除您所建立的收集組。 系統所提供的收集組無法加以修改或刪除。 但是，您仍然可以啟用或停用系統收集組，並變更它的組態。  
  
## <a name="see-also"></a>另請參閱  
 [資料收集器預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [資料收集器檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [[資料收集]](../../relational-databases/data-collection/data-collection.md)  
  
  
