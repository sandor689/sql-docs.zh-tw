---
title: PendingValue 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- PendingValue Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PendingValue
helpviewer_keywords:
- PendingValue element
ms.assetid: 386b2ec6-3d83-42d2-b83a-83e375fbdcbd
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ef24ae229f879adc15fa9f2ecfd8cb10a19d09ff
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263394"
---
# <a name="pendingvalue-element-assl"></a>PendingValue 元素 (ASSL)
  包含唯讀暫止值相關聯[ServerProperty](../objects/serverproperty-element-assl.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<ServerProperty>  
   ...  
   <PendingValue>...</PendingValue>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|任何 simpleType|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[ServerProperty](../objects/serverproperty-element-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 這個項目包含的值`ServerProperty`，將會使用在下一次的目前執行個體[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]已啟動。 這個值通常是從儲存伺服器屬性值的任何位置擷取，包括初始化檔案、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 登錄或另一個儲存機制。  
  
 對應至父系的元素`PendingValue`在 「 分析管理物件 (AMO) 物件模型是<xref:Microsoft.AnalysisServices.ServerProperty>。  
  
## <a name="see-also"></a>另請參閱  
 [ServerProperties 元素&#40;ASSL&#41;](../collections/serverproperties-element-assl.md)   
 [伺服器項目&#40;ASSL&#41;](../objects/server-element-assl.md)   
 [屬性&#40;ASSL&#41;](properties-assl.md)  
  
  
