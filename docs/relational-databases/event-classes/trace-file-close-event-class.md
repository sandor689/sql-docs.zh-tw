---
title: "Trace File Close 事件類別 | Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Trace File Close event class
ms.assetid: 128b7bac-cb64-43e7-ae9b-87b7d2ebb4ef
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6ce196fb683057e914891ca2a58f7db9b813f74b
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="trace-file-close-event-class"></a>Trace File Close 事件類別
  **Trace File Close** 事件類別表示已在追蹤檔案換用期間關閉追蹤檔案。  
  
## <a name="trace-file-close-event-class-data-columns"></a>Trace File Close 事件類別資料行  
  
|資料行名稱|資料類型|描述|資料行識別碼|可篩選|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|事件類別 = 150。|27|否|  
|**EventSequence**|**int**|此追蹤中觸發這個事件的唯一時間戳記。 所觸發的每個事件都會使這個數字逐一遞增。|51|否|  
|**FileName**|**nvarchar**|要關閉之追蹤檔案的邏輯名稱。|36|是|  
|**IsSystem**|**int**|指出事件是發生在系統處理序或使用者處理序。 1 = 系統，NULL = 使用者。 此事件類別的值永遠為 1。|60|是|  
|**LoginName**|**nvarchar**|使用者登入的名稱 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性登入或 DOMAIN\username 格式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登入認證)。 此事件類別的值永遠為 "sa"。|11|是|  
|**Exchange Spill**|**int**|由系統指派給追蹤的識別碼。|22|是|  
|**ServerName**|**nvarchar**|正在追蹤之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。|26|否|  
|**SessionLoginName**|**nvarchar**|引發工作階段之使用者的登入名稱。 例如，如果您使用 Login1 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，並以 Login2 執行陳述式，則 **SessionLoginName** 將顯示 Login1 而 **LoginName** 則顯示 Login2。 此資料行將同時顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 登入。|64|是|  
|**SPID**|**int**|事件發生所在之工作階段的識別碼。|12|是|  
|**StartTime**|**datetime**|事件啟動的時間 (如果有的話)。|14|是|  
  
## <a name="see-also"></a>另請參閱  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  