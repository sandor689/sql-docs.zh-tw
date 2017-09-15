---
title: "Exception 元素 (XMLA) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Exception Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Exception
- urn:schemas-microsoft-com:xml-analysis#Exception
- microsoft.xml.analysis.exception
helpviewer_keywords:
- Exception element
ms.assetid: 0be4cc2f-c03e-490a-a6f7-8b1ede5d09ba
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0c83900d85d698c5f9b2c0bdca2c197ab4ce05b1
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="exception-element-xmla"></a>Exception 元素 (XMLA)
  表示例外狀況傳回從[探索](../../../analysis-services/xmla/xml-elements-methods-discover.md)或[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)方法呼叫。  
  
 **命名空間**`http://schemas.microsoft.com/analysisservices/2003/exception`  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[根](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 如果在執行期間發生錯誤**探索**方法呼叫或單一 XMLA 命令中**Execute**方法呼叫不會將方法或命令完成後，**根**該方法或命令元素包含**例外狀況**項目和**訊息**項目。 **例外狀況**項目表示，就會發生錯誤，導致方法或命令無法順利執行，而**訊息**元素包含錯誤或警告訊息的清單與錯誤相關。  
  
## <a name="see-also"></a>另請參閱  
 [Messages 元素 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [屬性 &#40;XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  