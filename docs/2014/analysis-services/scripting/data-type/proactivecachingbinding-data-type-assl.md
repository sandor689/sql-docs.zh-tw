---
title: ProactiveCachingBinding 資料類型 (ASSL) |Microsoft Docs
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
- ProactiveCachingBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingBinding data type
ms.assetid: 02e6ff2f-2f18-4607-9198-bb46f113f9ac
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d440911eefa33981ef435240c4e440378da34a4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189095"
---
# <a name="proactivecachingbinding-data-type-assl"></a>ProactiveCachingBinding 資料類型 (ASSL)
  定義抽象的衍生的資料類型，表示資訊[ProactiveCaching](../objects/proactivecaching-element-assl.md)有關需要重建快取中的資料來源變更或重建處理序狀態的項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<ProactiveCachingBinding>  
   <!-- ProactiveCachingBinding is an abstract base class with no child elements -->  
</ProactiveCachingBinding>  
```  
  
## <a name="data-type-characteristics"></a>資料類型特性  
  
|特性|描述|  
|--------------------|-----------------|  
|基底資料類型|[繫結](binding-data-type-assl.md)|  
|衍生資料類型|[ProactiveCachingIncrementalProcessingBinding](proactivecachingincrementalprocessingbinding-data-type-assl.md)， [ProactiveCachingObjectNotificationBinding](proactivecachingobjectnotificationbinding-data-type-assl.md)， [ProactiveCachingQueryBinding](querybinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>資料類型關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|無|  
|子元素|無|  
|衍生的元素|無|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊`Binding`型別，包括之 Analysis Services 指令碼語言 (ASSL) 物件的資料表`Binding`型別和繼承階層`Binding`類型，請參閱[繫結資料類型 &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 如需 ASSL 中資料繫結的概觀，請參閱 <<c0> [ 資料來源和繫結&#40;SSAS 多維度&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)。</c0>  
  
 在 「 分析管理物件 (AMO) 物件模型的對應元素是<xref:Microsoft.AnalysisServices.ProactiveCachingBinding>。  
  
## <a name="inheritance-hierarchy-of-proactivecachingbinding-types"></a>ProactiveCachingBinding 類型的繼承階層  
 下列階層會顯示 `ProactiveCachingBinding` 類型的繼承。  
  
 [繫結](binding-data-type-assl.md)項目  
  
 `ProactiveCachingBinding` 元素  
  
 [ProactiveCachingObjectNotificationBinding](proactivecachingobjectnotificationbinding-data-type-assl.md)項目  
  
 [ProactiveCachingInheritedBinding](inheritedbinding-data-type-assl.md)項目  
  
 [ProactiveCachingTablesBinding](proactivecachingtablesbinding-data-type-assl.md)項目  
  
 [ProactiveCachingQueryBinding](querybinding-data-type-assl.md)項目  
  
 [ProactiveCachingIncrementalProcessingBinding](proactivecachingincrementalprocessingbinding-data-type-assl.md)項目  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services 指令碼語言 XML 資料類型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
