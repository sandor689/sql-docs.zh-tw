---
title: ConnectComplete 並中斷連線事件 (ADO) |Microsoft 文件
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
- Disconnect
- Connection::ConnectComplete
- ConnectComplete
- Connection::Disconnect
helpviewer_keywords:
- Disconnect event [ADO]
- ConnectComplete event [ADO]
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ac6301a8ed8ab0c84f26225e20c2bfd971ff761
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276837"
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>ConnectComplete 並中斷連線事件 (ADO)
**ConnectComplete**連接啟動之後，會呼叫事件。 **中斷連線**連線結束後，會呼叫事件。  
  
## <a name="syntax"></a>語法  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>參數  
 *pError*  
 [錯誤](../../../ado/reference/ado-api/error-object.md)物件。 它描述如果發生之錯誤的值*adStatus*是**adStatusErrorsOccurred**; 否則它不會設定。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)值也永遠傳回**adStatusOK**。  
  
 當**ConnectComplete**是呼叫，此參數設為**adStatusCancel**如果**WillConnect**事件已經要求取消暫止的連接。  
  
 其中一個事件會傳回之前，請將此參數設定為**adStatusUnwantedEvent**以避免後續的通知。 不過，關閉並重新開啟[連接](../../../ado/reference/ado-api/connection-object-ado.md)會引發這些事件，會發生一次。  
  
 *pConnection*  
 **連接**套用此事件的物件。  
  
## <a name="see-also"></a>另請參閱  
 [ADO 事件模型範例 （VC + +）](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO 事件處理常式摘要](../../../ado/guide/data/ado-event-handler-summary.md)
