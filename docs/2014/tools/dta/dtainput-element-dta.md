---
title: DTAInput 元素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a754e81ea8fe094bb840cb57851685b3b6626521
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37179015"
---
# <a name="dtainput-element-dta"></a>DTAInput 元素 (DTA)
  包含 Database Engine Tuning Advisor 的 XML 輸入定義。  
  
## <a name="syntax"></a>語法  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|---------------------|-----------------|  
|**資料類型和長度**|無。|  
|**預設值**|無。|  
|**出現次數**|每個 **DTAXML** 元素可以選擇性地使用這個元素一次。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[DTAXML 元素&#40;DTA&#41;](dtaxml-element-dta.md)|  
|**子元素**|[伺服器項目&#40;DTA&#41;](server-element-dta.md)<br /><br /> [Workload 元素&#40;DTA&#41;](workload-element-dta.md)<br /><br /> [TuningOptions 元素&#40;DTA&#41;](tuningoptions-element-dta.md)<br /><br /> [組態項目&#40;DTA&#41;](configuration-element-dta.md)|  
  
## <a name="remarks"></a>備註  
 這個元素是 Database Engine Tuning Advisor 輸入結構描述階層的根。 Database Engine Tuning Advisor 的輸入可以是指定資料庫需要微調之伺服器、工作負載、微調選項或使用者指定組態的引數。  
  
## <a name="example"></a>範例  
 如需 **DTAInput** 元素的使用範例，請參閱[簡單 XML 輸入檔範例 &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 輸入檔參考 &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
