---
title: 維度元素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 63b9043b3ba88200a060a8b333ff53cf95340df3
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036576"
---
# <a name="dimension-element-xmla"></a>Dimension 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  識別父元素所代表的 cube 維度[物件](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md)項目。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Object>  
   ...  
   <Dimension>...</Dimension>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>項目特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|String|  
|預設值|無|  
|基數|1-1：只出現一次的必要元素。|  
  
## <a name="element-relationships"></a>項目關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[物件](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 **維度**項目是物件識別碼，其中包含所代表之 cube 維度名稱**物件**項目。  
  
## <a name="see-also"></a>另請參閱
 [資料庫項目&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)   
 [Dimension 元素 (XMLA)](../../../analysis-services/xmla/xml-elements-properties/dimension-element-xmla.md)   
 [屬性&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
