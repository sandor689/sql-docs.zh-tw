---
title: 儲存變更指令碼對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 531a7b9a4ae7405ef58cba9c5605c3f41c60df79
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274214"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>儲存變更指令碼對話方塊 (Visual Database Tools)
  此對話方塊顯示從上次儲存資料表以來您所做變更的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。 這也可以讓您在選擇的位置將指令碼儲存至文字檔。  
  
 您在 [資料表設計師] 中對資料表進行了尚未儲存的變更之後，即可存取這個對話方塊。 在 [資料表設計工具] 功能表中，按一下 [產生變更指令碼]。  
  
> [!NOTE]  
>  Visual Database Tools 提供的變更指令碼未包含錯誤處理。 這些指令碼會假設資料庫物件在工具開啟之後並未變更，而且因此不會發生變更相關的問題。 在執行變更指令碼之前，應先加入適當的錯誤處理陳述式。  
  
## <a name="options"></a>選項。  
 **於每一次儲存時，自動產生變更指令碼**  
 如果核取，[儲存變更指令碼] 對話方塊會在您將變更儲存至資料表時出現。  
  
 **是**  
 顯示 [儲存] 對話方塊，以便您選擇文字檔的位置。  
  
 **否**  
 取消建立變更指令碼。  
  
  
