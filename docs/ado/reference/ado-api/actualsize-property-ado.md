---
title: ActualSize 屬性 (ADO) |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f71de5881975eb9ba38b2d21ef8f1590aae95d90
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275097"
---
# <a name="actualsize-property-ado"></a>ActualSize 屬性 (ADO)
表示欄位的值，以位元組為單位的實際長度。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 傳回**長**值。  
  
## <a name="remarks"></a>備註  
 使用**ActualSize**屬性傳回的實際長度[欄位](../../../ado/reference/ado-api/field-object.md)物件的值。 針對所有欄位， **ActualSize**屬性是唯讀的。 如果 ADO 無法判斷長度的**欄位**物件的值**ActualSize**屬性會傳回**adUnknown**。  
  
 **ActualSize**和[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)屬性都不同，如下列範例所示。 A**欄位**物件宣告類型為**adVarChar**並傳回最大長度為 50 個字元**DefinedSize**屬性值為 50，但**ActualSize**它所傳回的屬性值是目前記錄的欄位中儲存之資料的長度。 **欄位**與**DefinedSize**大於 255 個位元組會被視為可變長度資料行。  
  
## <a name="applies-to"></a>適用於  
 [Field 物件](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>另請參閱  
 [ActualSize 和 DefinedSize 屬性範例 (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize 和 DefinedSize 屬性範例 （VC + +）](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize 屬性](../../../ado/reference/ado-api/definedsize-property.md)
