---
title: sys.sysdatabases (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdatabases_TSQL
- sys.sysdatabases_TSQL
- sys.sysdatabases
- sysdatabases
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdatabases compatibility view
- sysdatabases system table
ms.assetid: 60a93880-62f1-4eda-a886-f046706ba90c
caps.latest.revision: 35
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 561af4e645f757880a3b5319f437e21e9e97a526
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39549178"
---
# <a name="syssysdatabases-transact-sql"></a>sys.sysdatabases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  包含每個資料庫的執行個體中的一個資料列[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 當[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]第一次安裝**sysdatabases**包含的項目**master**，**模型**， **msdb**，及**tempdb**資料庫。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|資料庫名稱|  
|**dbid**|**smallint**|資料庫識別碼|  
|**sid**|**varbinary(85)**|資料庫建立者的系統識別碼。|  
|**模式**|**smallint**|用於內部，在建立資料庫時鎖定它。|  
|**status**|**int**|狀態位元，可以透過設定其中有些[ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md)所示：<br /><br /> 1 = **autoclose** (ALTER DATABASE)<br /><br /> 4 =**選取為 / bulkcopy** (使用 ALTER DATABASE SET RECOVERY)<br /><br /> 8 = **trunc.log 上 chkpt** (使用 ALTER DATABASE SET RECOVERY)<br /><br /> 16 =**損毀頁偵測**(ALTER DATABASE)<br /><br /> 32 =**載入**<br /><br /> 64 =**還原前**<br /><br /> 128 =**復原**<br /><br /> 256 =**未復原**<br /><br /> 512 =**離線**(ALTER DATABASE)<br /><br /> 1024 =**唯讀**(ALTER DATABASE)<br /><br /> 2048 =**僅限 dbo 使用**(使用 ALTER DATABASE SET restricted_user 來執行)<br /><br /> 4096=select**單一使用者**(ALTER DATABASE)<br /><br /> 32768 =**緊急模式**<br /><br /> 65536 =**總和檢查碼**(ALTER DATABASE)<br /><br /> 4194304 = **autoshrink** (ALTER DATABASE)<br /><br /> 1073741824 =**正常關機**<br /><br /> 多位元可以同時設為 ON。|  
|**status2**|**int**|16384 = **ANSI null 預設值**(ALTER DATABASE)<br /><br /> 65536 =**串連 null 產生 null** (ALTER DATABASE)<br /><br /> 131072 =**遞迴觸發程序**(ALTER DATABASE)<br /><br /> 1048576 =**預設為本機資料指標**(ALTER DATABASE)<br /><br /> 8388608 =**引號識別項**(ALTER DATABASE)<br /><br /> 33554432 =**資料指標在認可時關閉**(ALTER DATABASE)<br /><br /> 67108864 = **ANSI nulls** (ALTER DATABASE)<br /><br /> 268435456 = **ANSI warnings** (ALTER DATABASE)<br /><br /> 536870912 =**全文檢索已啟用**(透過設定**sp_fulltext_database**)|  
|**crdate**|**datetime**|建立日期。|  
|**保留**|**datetime**|保留供日後使用。|  
|**category**|**int**|包含複寫所用資訊的點陣圖：<br /><br /> 1 = 針對快照集或異動複寫而發行。<br /><br /> 2 = 訂閱快照式或交易式發行集。<br /><br /> 4 = 針對合併式複寫而發行。<br /><br /> 8 = 訂閱合併式發行集。<br /><br /> 16 = 散發資料庫。|  
|**cmptlevel**|**tinyint**|資料庫的相容性層級。 如需詳細資訊，請參閱 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)。|  
|**filename**|**nvarchar(260)**|資料庫主要檔案的作業系統路徑和名稱。<br /><br /> **檔名**看見**dbcreator**， **sysadmin**、 CREATE ANY DATABASE 權限，或擁有下列權限的被授與者的資料庫擁有者： ALTER ANY DATABASE建立任何資料庫中，檢視任何定義。 若要傳回的路徑和檔案名稱，請查詢[sys.sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md)相容性 檢視中，或有[sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)檢視。|  
|**version**|**smallint**|建立資料庫所用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 程式碼的內部版本號碼。 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>另請參閱  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [將系統資料表對應至系統檢視表&#40;Transact SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [相容性檢視 &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
