---
title: XTP （記憶體中 OLTP） 效能計數器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 988cdbba429420c25a3b091ba062bb68a1c61435
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285054"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a>XTP (記憶體中 OLTP) 效能計數器
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供物件和計數器，可供效能監視器用來監視記憶體中 OLTP 活動。  
  
##  <a name="SQLServerPOs"></a> XTP (記憶體中 OLTP) 效能物件  
 下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件。  
  
|效能物件|描述|  
|------------------------|-----------------|  
|[XTP 資料指標](../cursors.md)|XTP 資料指標效能物件包含與內部 XTP 引擎資料指標相關的計數器。 低層級的建置組塊 XTP 引擎用來處理資料指標是[!INCLUDE[tsql](../../includes/tsql-md.md)]查詢。 因此，您通常不會有這些指標的直接控制權。|  
|[XTP 記憶體回收](sql-server-xtp-garbage-collection.md)|XTP 記憶體回收效能物件包含與 XTP 引擎記憶體回收行程相關的計數器。|  
|[XTP 虛設處理器](sql-server-xtp-phantom-processor.md)|XTP 虛設處理器效能物件包含與 XTP 引擎的虛設處理子系統相關的計數器。 此元件負責偵測在 SERIALIZABLE 隔離等級執行之交易中的虛設項目列。|  
|[XTP 儲存體](sql-server-xtp-storage.md)|XTP Storage 效能物件包含與 XTP 儲存體中相關的計數器[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。|  
|[XTP 交易記錄](sql-server-xtp-transaction-log.md)|XTP Transaction Log 效能物件包含與 XTP 交易記錄相關的計數器[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。|  
|[XTP 交易](sql-server-xtp-transactions.md)|XTP Transactions 效能物件包含與 XTP 引擎交易相關的計數器[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。|  
  
  
