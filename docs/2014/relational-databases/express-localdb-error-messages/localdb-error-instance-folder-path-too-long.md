---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 96b4deb3bf0c7d660779781f9d76aac785ca12ca
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415127"
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|260|  
|事件來源|SQL Server 本機資料庫執行階段 12.0|  
|元件|本機資料庫執行階段 API|  
|訊息文字|本機資料庫執行個體資料夾的完整路徑長度比 MAX_PATH 還長。 執行個體必須存放在資料夾中： SQL Server 本機 DB\Instances %%LOCALAPPDATA%%\Microsoft\Microsoft\\< 執行個體名稱\>。|  
  
## <a name="explanation"></a>說明  
 應儲存執行個體的路徑長度超過 MAX_PATH。  
  
## <a name="user-action"></a>使用者動作  
 請建立長度短於 MAX_PATH 的新路徑。  
  
  
