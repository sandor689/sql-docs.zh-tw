---
title: XTP 儲存體 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
caps.latest.revision: 3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b2f18eb1db7ef854b4d982d18374b174ecf65641
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37156439"
---
# <a name="xtp-storage"></a>XTP 儲存體
  XTP Storage 效能物件包含與 XTP 儲存體中相關的計數器[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
 下表描述**XTP 儲存體**計數器。  
  
|計數器|描述|  
|-------------|-----------------|  
|**Checkpoints Closed**|線上代理程式已關閉的檢查點計數。|  
|**Checkpoints Completed**|離線檢查點執行緒已處理的檢查點計數。|  
|**Core Merges Completed**|合併工作者執行緒已完成的核心合併數目。 這些合併仍然需要予以安裝。|  
|**Merge Policy Evaluations**|自伺服器啟動後的合併原則評估數目。|  
|**Merge Requests Outstanding**|自伺服器啟動後之未處理的合併要求數目。|  
|**Merges Abandoned**|由於失敗而放棄的合併數目。|  
|**Merges Installed**|已成功安裝的合併數目。|  
|**Total Files Merged**|已合併的來源檔案總數。 此計數可用來尋找合併中的平均來源檔案數目。|  
  
## <a name="see-also"></a>另請參閱  
 [XTP&#40;記憶體內部 OLTP&#41;效能計數器](../../integration-services/performance/performance-counters.md)  
  
  
