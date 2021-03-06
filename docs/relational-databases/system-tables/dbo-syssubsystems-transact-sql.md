---
title: dbo.syssubsystems (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.syssubsystems
- syssubsystems
- syssubsystems_TSQL
- dbo.syssubsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syssubsystems system table
ms.assetid: 114b3d55-1ad6-4777-b868-8ef0c86ba596
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: abe7c8fa687a5868bae73b9590ea39a30fc90ee2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254828"
---
# <a name="dbosyssubsystems-transact-sql"></a>dbo.syssubsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  包含所有可用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy 子系統的相關資訊。 **Syssubsystems**資料表儲存在**msdb**資料庫。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|子系統的識別碼。|  
|**subsystem**|**nvarchar(40)**|子系統的名稱。|  
|**description_id**|**int**|訊息中的資料列識別碼**sys.messages**目錄包含子系統描述的檢視。|  
|**subsystem_dll**|**nvarchar(255)**|子系統 DLL 的位置。|  
|**agent_exe**|**nvarchar(255)**|使用子系統的可執行檔的完整路徑。|  
|**start_entry_point**|**nvarchar(30)**|初始化子系統時所呼叫的函數。|  
|**event_entry_point**|**nvarchar(30)**|執行子系統步驟時所呼叫的函數。|  
|**stop_entry_point**|**nvarchar(30)**|子系統執行完成時所呼叫的函數。|  
|**max_worker_threads**|**int**|給定子系統的最大並行步驟數。|  
  
## <a name="remarks"></a>備註  
 只有成員**sysadmin**固定的伺服器角色可以存取這份資料表。  
  
## <a name="see-also"></a>另請參閱  
 [dbo.sysproxysubsystem &#40;Transact SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.sysproxies &#40;Transact SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)   
 [sys.messages &#40;TRANSACT-SQL& #41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)  
  
  
