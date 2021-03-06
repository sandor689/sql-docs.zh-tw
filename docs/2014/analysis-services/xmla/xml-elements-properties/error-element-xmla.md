---
title: Error 元素 (XMLA) |Microsoft Docs
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
- Error Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.error
- http://schemas.microsoft.com/analysisservices/2003/engine#Error
- urn:schemas-microsoft-com:xml-analysis#Error
helpviewer_keywords:
- Error element
ms.assetid: add670cb-cab2-42be-91a3-d0c385f29d16
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 55b63c016f9f2c61cc83563e697a49a0c4970cae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273734"
---
# <a name="error-element-xmla"></a>Error 元素 (XMLA)
  包含的執行個體所傳回之錯誤的相關資訊[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Message>  
   <Error   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
<!-- or -->  
<Cell><!-- or row -->  
   <!-- A child element -->  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception"  
         < ErrorCode>...</ErrorCode>  
         < Description>...</Description>  
         < Source>...</Source>  
         < HelpFile>...</HelpFile>  
      </Error>  
   <!-- /A child element -- >  
</Cell>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|資料類型和長度|無|  
|預設值|無|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[Message](message-element-xmla.md)|  
  
## <a name="child-elements"></a>子元素  
  
|Ancestor|子元素|  
|--------------|--------------------|  
|[Message](message-element-xmla.md)|無|  
|[儲存格](cell-element-mddataset-xmla.md)，[資料列](description-element-xmla.md)， [ErrorCode](errorcode-element-xmla.md)， [HelpFile](file-element-xmla.md)，[來源](source-element-error-xmla.md)|  
  
## <a name="attributes"></a>屬性  
  
|attribute|描述|  
|---------------|-----------------|  
|ErrorCode|所需`UnsignedInt`屬性 (只有當`Message`是父項目。)包含錯誤的數值傳回碼。|  
|Severity|選擇性`String`屬性 (只有當`Message`是父項目。)包含錯誤的嚴重性。|  
|描述|選擇性`String`屬性 (只有當`Message`是父項目。)包含錯誤的描述性文字。|  
|來源|選擇性`String`屬性 (只有當`Message`是父項目。)包含產生錯誤之元件的名稱。|  
|HelpFile|選擇性`String`屬性 (只有當`Message`是父項目。)包含描述錯誤之說明檔或主題的路徑或 URL。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [Warning 元素&#40;XMLA&#41;](warning-element-xmla.md)   
 [屬性&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
