---
title: IsolationLevel 屬性 |Microsoft 文件
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
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e6de8da487352fe0a26d3524317ced061370771
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279207"
---
# <a name="isolationlevel-property"></a>IsolationLevel 屬性
表示層級的隔離[連接](../../../ado/reference/ado-api/connection-object-ado.md)物件。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)值。 預設值是**adXactReadCommitted**。  
  
## <a name="remarks"></a>備註  
 使用**IsolationLevel**屬性來設定隔離層級**連接**物件。 設定不會不會生效，直到您呼叫在下一次[BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)方法。 如果您要求的隔離層級無法使用，提供者可能會傳回下一個更高的隔離等級而未更新**IsolationLevel**屬性。  
  
 **IsolationLevel**屬性是讀取/寫入。  
  
> [!NOTE]
>  **遠端資料服務使用量**使用用戶端時**連接**物件**IsolationLevel**屬性可以設為**adXactUnspecified**。 因為使用者正在使用已中斷連線**資料錄集**物件上的用戶端快取中，可能有多位使用者的問題。 比方說，當兩個不同的使用者嘗試更新相同的記錄時，遠端資料服務只會允許使用者第一次更新記錄，到"win"。 第二個使用者的更新要求會失敗，發生錯誤。  
  
## <a name="applies-to"></a>適用於  
 [Connection 物件 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [IsolationLevel 和模式屬性範例 (VB)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel 和模式屬性範例 （VC + +）](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
