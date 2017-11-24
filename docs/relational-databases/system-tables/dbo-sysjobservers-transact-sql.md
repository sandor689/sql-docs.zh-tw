---
title: "dbo.sysjobservers (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a706c537f4f983563dacb1f137314680824dd30
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  儲存特定作業與一或多部目標伺服器的關聯或關係。此資料表會儲存在 msdb 資料庫中。  
  
||  
|-|  
|**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|作業識別碼。|  
|server_id|**int**|伺服器識別碼。|  
|last_run_outcome|**tinyint**|作業上次執行的結果：<br /><br /> **0** = 失敗<br /><br /> **1** = 成功<br /><br /> **3** = 取消|  
|last_outcome_ 訊息|**nvarchar （1024)**|關聯的訊息 (如果有的話)，包含 last_run_outcome 資料行。|  
|last_run_date|**int**|上次執行作業的日期。|  
|last_run_time|**int**|前次執行作業的時間。|  
|last_run_duration|**int**|此作業執行的持續時間 (以時、分和秒為單位)。 使用以下公式來計算: (*小時*\*10000) + (*分鐘*\*100) +*秒*。|  
  
## <a name="see-also"></a>請參閱＜  
 [SQL Server Agent 資料表 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  