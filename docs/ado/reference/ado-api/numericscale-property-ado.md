---
title: NumericScale 屬性 (ADO) |Microsoft 文件
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
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ad1cceb73749530faf08e96eecef235905971e5
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279927"
---
# <a name="numericscale-property-ado"></a>NumericScale 屬性 (ADO)
表示中的數值小數位數[參數](../../../ado/reference/ado-api/parameter-object.md)或[欄位](../../../ado/reference/ado-api/field-object.md)物件。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回**位元組**指出哪一個數值小數位數的值將會是已解決。  
  
## <a name="remarks"></a>備註  
 使用**NumericScale**屬性來判斷要在小數點右邊的數字位數會用來代表數字的值**參數**或**欄位**物件。  
  
 如**參數**物件**NumericScale**屬性是讀取/寫入。  
  
 如**欄位**物件**NumericScale**是通常是唯讀。 不過，對於新**欄位**已附加至的物件[欄位](../../../ado/reference/ado-api/fields-collection-ado.md)集合[記錄](../../../ado/reference/ado-api/record-object-ado.md)， **NumericScale**是讀取/寫入之後才[值](../../../ado/reference/ado-api/value-property-ado.md)屬性**欄位**已指定與此資料提供者已成功地加入新**欄位**藉由呼叫[更新](../../../ado/reference/ado-api/update-method.md)方法[欄位](../../../ado/reference/ado-api/fields-collection-ado.md)集合。  
  
## <a name="applies-to"></a>適用於  
  
|||  
|-|-|  
|[Parameter 物件](../../../ado/reference/ado-api/parameter-object.md)|[Field 物件](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>另請參閱  
 [NumericScale 和有效位數屬性範例 (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale 和有效位數屬性範例 （VC + +）](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Precision 屬性 (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)
