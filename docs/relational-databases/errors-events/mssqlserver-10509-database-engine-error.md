---
title: MSSQLSERVER_10509 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cf371bbc4a9a80608c5171be9bd9891c71cde1a6
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
ms.locfileid: "34321989"
---
# <a name="mssqlserver10509"></a>MSSQLSERVER_10509
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|10509|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|PG_INVALID_STMT|  
|訊息文字|無法建立計畫指南 '%.\*ls'，因為 **@stmt** 或 **@statement_start_offset** 所指定的陳述式中含有語法錯誤或不適用於計畫指南。 請提供單一有效 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，或批次中陳述式的有效開始位置。 若要取得有效開始位置，請查詢 sys.dm_exec_query_stats 動態管理函數中的 statement_start_offset 資料行。|  
  
## <a name="explanation"></a>說明  
**@stmt** 或 **@statement_start_offset** 所指定的陳述式中含有語法錯誤或不適用於計畫指南。  
  
## <a name="user-action"></a>使用者動作  
請提供單一有效 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，或批次中陳述式的有效開始位置。 若要取得有效開始位置，請查詢 sys.dm_exec_query_stats 動態管理函數中的 statement_start_offset 資料行。  
  
## <a name="see-also"></a>另請參閱  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[計畫指南](~/relational-databases/performance/plan-guides.md)  
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
