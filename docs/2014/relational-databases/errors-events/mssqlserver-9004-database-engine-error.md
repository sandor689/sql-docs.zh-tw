---
title: MSSQLSERVER_9004 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c80678bc5463f3cf17d8442afb36c30dcc69534c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429407"
---
# <a name="mssqlserver9004"></a>MSSQLSERVER_9004
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|9004|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|LOG_CORRUPT|  
|訊息文字|在處理資料庫 '%.*ls' 的記錄檔時，發生錯誤。  If possible, restore from backup. 若備份無法使用，可能需要重建記錄檔。|  
  
## <a name="explanation"></a>說明  
 在回復、復原或複寫期間處理記錄檔時發生錯誤。 這可能代表作業系統偵測到的錯誤，或是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 偵測到的內部一致性錯誤。  
  
## <a name="user-action"></a>使用者動作  
 您可以執行下列其中一項動作來更正此錯誤：  
  
-   從備份進行還原。  
  
-   重建記錄檔。  
  
 此外，請檢查系統事件和錯誤記錄檔，以找出可能造成問題的系統內部問題。  
  
  
