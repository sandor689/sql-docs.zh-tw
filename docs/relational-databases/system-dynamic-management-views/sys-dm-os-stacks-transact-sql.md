---
title: "sys.dm_os_stacks (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_stacks
- dm_os_stacks_TSQL
- sys.dm_os_stacks
- sys.dm_os_stacks_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_stacks dynamic management view
ms.assetid: a69b06c4-28f0-4535-8fa1-9f132db4d916
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e3e292fbafbee9586d377f133af7f9d3ee520d5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  這份動態管理檢視可供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在內部使用，以執行下列動作：  
  
-   追蹤偵錯資料，例如未完成的配置。  
  
-   在元件假設發出特定呼叫之處，假設或驗證 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件使用的邏輯。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary （8)**|這項堆疊配置的唯一位址。 不可為 Null。|  
|**frame_index**|**int**|每一列代表函式呼叫，以遞增順序排序的特定的框架索引時**stack_address**，傳回的完整呼叫堆疊。 不可為 Null。|  
|**frame_address**|**varbinary （8)**|函數呼叫的位址。 不可為 Null。|  
  
## <a name="remarks"></a>備註  
 **sys.dm_os_stacks**要求伺服器與其他元件的符號必須出現在伺服器上正確顯示的資訊。  
  
## <a name="permissions"></a>Permissions  
在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]Premium 層需要`VIEW DATABASE STATE`資料庫的權限。 在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]標準和基本層，需要**伺服器管理員**或**Azure Active Directory 系統管理員**帳戶。  
  

## <a name="see-also"></a>請參閱＜  
  [SQL Server 作業系統相關的動態管理檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  