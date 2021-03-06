---
title: ConnectionTimeout 屬性 (ADO) |Microsoft 文件
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
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1f90890b8f48a4a00fe9469ed978d42d3f6a86a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277007"
---
# <a name="connectiontimeout-property-ado"></a>ConnectionTimeout 屬性 (ADO)
表示在終止嘗試並產生錯誤之前，建立連接時要等待的時間。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回**長**表示，以秒為單位，時間等待連接開啟的值。 預設值為 15。  
  
## <a name="remarks"></a>備註  
 使用**ConnectionTimeout**屬性[連接](../../../ado/reference/ado-api/connection-object-ado.md)如果從網路流量或大量使用伺服器的延遲，導致放棄嘗試連線的物件。 如果從時間**ConnectionTimeout**屬性設定在之前就超過開啟連接，發生錯誤，和 ADO 取消嘗試。 如果您將屬性設為零，ADO 會等候直到開啟連接。 請確定您撰寫程式碼的提供者支援**ConnectionTimeout**功能。  
  
 **ConnectionTimeout**屬性是讀取/寫入，當連接已關閉，且為唯讀模式開啟時。  
  
## <a name="applies-to"></a>適用於  
 [Connection 物件 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [ConnectionString、 ConnectionTimeout 和 State 屬性範例 (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、 ConnectionTimeout 和 State 屬性範例 （VC + +）](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [CommandTimeout 屬性 (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
