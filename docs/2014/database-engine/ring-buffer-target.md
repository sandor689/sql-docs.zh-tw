---
title: 信號緩衝區目標 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events], ring buffer target
- ring buffer target [SQL Server extended events]
ms.assetid: 54494e11-b56b-43b7-aa5e-c8724e56b251
caps.latest.revision: 12
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b60f4e3c5ca8d207d3eac23047c8cdefc99d9f66
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273074"
---
# <a name="ring-buffer-target"></a>環緩衝區目標
  信號緩衝區目標會短暫地將事件資料保留在記憶體中， 此目標可以在兩個模式的其中一個之下管理事件。  
  
-   第一個模式是嚴格的先進先出 (FIFO)，當使用配置給目標的所有記憶體時，將會捨棄最舊的事件。 在此模式中 (預設值)，occurrence_number 選項設定為 0。  
  
-   第二個模式是依事件的 FIFO，將會保留每一個類型之事件的指定數目。 在此模式中，當使用配置給目標的所有記憶體時，將會捨棄每一個類型的最舊事件。 您可以設定 occurrence_number 選項，以指定要保留之每一個類型的事件數目。  
  
 下表說明用來設定信號緩衝區目標的可用選項。  
  
|選項|允許的值|描述|  
|------------|--------------------|-----------------|  
|max_memory|任何 32 位元整數。 此為選擇性的值。|要使用的最大記憶體數量 (以 KB 為單位)。 根據先達到的限制，卸除現有事件：max_event_limit 或 max_memory。|  
|max_event_limit|任何 32 位元整數。 此為選擇性的值。|保留在 ring_buffer 中的最大事件數目。 根據先達到的限制，卸除現有事件：max_event_limit 或 max_memory。 預設值 = 1000。|  
|occurrence_number|為下列其中一個值：<br /><br /> 0 (預設值) = 當使用配置給目標的所有記憶體時，將會捨棄最舊的事件。<br /><br /> 任何 32 位元整數 = 在根據每一個事件的 FIFO 規則來捨棄之前，所要保留之每一個類型的事件數目。<br /><br /> <br /><br /> 此為選擇性的值。|要使用的 FIFO 模式，如果設定為大於 0 的值，則為要保留在緩衝區內之每一個類型的慣用事件數目。|
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="adding-the-target-to-a-session"></a>將目標加入至工作階段  
 若要將信號緩衝區目標加入至擴充事件工作階段，您必須在建立或更改事件工作階段時，加入下列陳述式：  
  
```sql
ADD TARGET package0.ring_buffer  
```  
  
## <a name="reviewing-the-target-output"></a>檢閱目標輸出  
 若要檢閱信號緩衝區目標的輸出，您可以使用下列查詢，並將 *session_name* 取代成事件工作階段的名稱。  
  
```sql
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 下列範例顯示信號緩衝區目標輸出格式。  
  
```  
<RingBufferTarget eventsPerSec="" processingTime="" totalEventsProcessed="" eventCount="" droppedCount="" memoryUsed="">  
 <event name="" package="" id="" version="" timestamp="">  
    <data name="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </data>  
    <action name="" package="">  
      <type name="" package="" />  
      <value></value>  
      <text></text>  
    </action>  
  </event>  
</RingBufferTarget>  
```


## <a name="see-also"></a>另請參閱

- [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md)
- [sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql?view=sql-server-2016)
- [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql?view=sql-server-2016)
- [ALTER EVENT SESSION &#40;Transact-SQL&#41;](https://docs.microsoft.com/sql/t-sql/statements/alter-event-session-transact-sql?view=sql-server-2016)

