---
title: Flush 方法 (ADO) |Microsoft 文件
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
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 931d8a2546c9a4d5c41d6b2348a7db5d9ad312ef
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278767"
---
# <a name="flush-method-ado"></a>Flush 方法 (ADO)
強制內容[資料流](../../../ado/reference/ado-api/stream-object-ado.md)基礎物件與其 ADO 緩衝區中剩餘**資料流**相關聯。  
  
## <a name="syntax"></a>語法  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>備註  
 這個方法可用來將資料流緩衝區的內容傳送至基礎物件： 例如，節點或檔案的來源 URL 表示**資料流**物件。 當您想要確保所有的變更，應該呼叫這個方法所做的內容**資料流**已寫入。 不過，搭配 ADO 它通常不需要呼叫**排清**，如 ADO 持續排清其在背景中最大的緩衝區。 變更的內容為**資料流**都會自動進行，不會快取直到**排清**呼叫。  
  
 關閉**資料流**與[關閉](../../../ado/reference/ado-api/close-method-ado.md)方法的內容清除**資料流**自動; 有不是需要明確地呼叫**排清**之前**關閉**。  
  
## <a name="applies-to"></a>適用於  
 [Stream 物件 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
