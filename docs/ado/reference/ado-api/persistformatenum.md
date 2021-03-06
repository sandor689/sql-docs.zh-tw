---
title: PersistFormatEnum |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9aa6ce5a4341c85f7763d407b0d39599b24d9441
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280607"
---
# <a name="persistformatenum"></a>PersistFormatEnum
指定用來儲存格式[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)。  
  
|常數|ReplTest1|描述|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|表示 Microsoft 進階資料 TableGram (ADTG) 格式。|  
|**adPersistADO**|@shouldalert|表示將會使用 ADO 自己可延伸標記語言 (XML) 格式。 這個值是 adPersistXML 相同，而且是為了回溯相容性。|  
|**adPersistXML**|@shouldalert|表示可延伸標記語言 (XML) 格式。|  
|**adPersistProviderSpecific**|2|表示提供者將保存**資料錄集**使用自己的格式。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>適用於  
 [Save 方法](../../../ado/reference/ado-api/save-method.md)
