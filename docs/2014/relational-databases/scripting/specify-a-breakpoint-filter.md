---
title: 指定中斷點篩選條件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.contraints
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9bf7e4f7a162bf172812ed555463c061611237e0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37191778"
---
# <a name="specify-a-breakpoint-filter"></a>指定中斷點篩選條件
  中斷點篩選條件會限制中斷點只能在指定的電腦、作業系統處理序和執行緒上運作。 中斷點篩選條件通常是在偵錯平行應用程式時使用。  
  
##  <a name="BKMK_ActionConsiderations"></a> 篩選考量  
 中斷點篩選條件通常不會搭配 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具使用，因為 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼和預存程序不是平行應用程式。  
  
#### <a name="to-specify-a-breakpoint-filter"></a>若要指定中斷點篩選條件  
  
1.  在編輯器視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [篩選]。  
  
     -或-  
  
     在 [中斷點] 視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [篩選]。  
  
2.  在 [中斷點篩選條件] 對話方塊中，使用 [篩選] 方塊來指定電腦 (依名稱) 或作業系統處理序和執行緒 (依名稱或識別碼)：  
  
    -   `MachineName` 是執行 Database Engine 執行個體的電腦。  
  
    -   `ProcessID`與`ProcessName`是執行 Database Engine 執行個體的作業系統處理序。  
  
    -   `ThreadID` 並`ThreadName`會執行的作業系統執行緒[!INCLUDE[tsql](../../includes/tsql-md.md)]批次、 程序或 Database engine 執行個體中的函式。  
  
3.  按一下 **[確定]** 實作變更，或按一下 **[取消]** 結束而不套用變更。  
  
## <a name="see-also"></a>另請參閱  
 [指定中斷點條件](specify-a-breakpoint-condition.md)   
 [指定叫用計數](specify-a-hit-count.md)   
 [指定中斷點動作](specify-a-breakpoint-action.md)  
  
  
