---
title: MSSQLSERVER_17066 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 17066 (Database Engine error)
ms.assetid: 7d650bbf-c583-4af8-9e22-993ee2880d95
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bbc60689321b8e952838264464b72cc1a30a2986
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432037"
---
# <a name="mssqlserver17066"></a>MSSQLSERVER_17066
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|17066|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SQLASSERT_ONLY|  
|訊息文字|SQL Server 判斷提示: 檔案: \<%s>，行 = %d 失敗的判斷提示 = '%s'。 此錯誤可能與時間有關。 如果重新執行陳述式之後仍然發生此錯誤，請使用 DBCC CHECKDB 來檢查資料庫的結構完整性，或重新啟動伺服器以確定記憶體中的資料結構並未損毀。|  
  
## <a name="explanation"></a>說明  
 這項錯誤可能是由暫時性的時間相關錯誤所造成，或由記憶體中或磁碟內存的資料損毀所造成。  
  
## <a name="user-action"></a>使用者動作  
 請重新執行導致引發此例外狀況的陳述式。 如果此錯誤是由時間相關的事件所造成，此錯誤可能不會再次發生。 如果持續發生此問題，請執行 DBCC CHECKDB 來檢查是否有磁碟內存的損毀。 重新啟動伺服器，以便確保記憶體中的資料結構並未損毀。  
  
## <a name="see-also"></a>另請參閱  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
