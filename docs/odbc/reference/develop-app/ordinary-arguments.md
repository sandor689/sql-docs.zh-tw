---
title: 一般引數 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ecdcf5e697bcf3235cadbe3d8f3f8f981406575
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911643"
---
# <a name="ordinary-arguments"></a>一般引數
目錄函式的字串引數時的一般引數，則會視為常值字串。 一般的引數會接受字串的搜尋模式都值的清單。 一般的引數的情況下會很可觀，並在字串中的引號字元字面。 這些引數會被視為一般引數如果 SQL_ATTR_METADATA_ID 陳述式屬性設定為 SQL_FALSE。它們會被視為識別碼引數而如果此屬性設定為 SQL_TRUE。  
  
 如果一般引數設定為 null 指標，而且引數是必要的引數，函數會傳回 SQL_ERROR 並 SQLSTATE HY009 （使用無效的 null 指標）。 如果設定的一般引數為 null 指標，而且引數不是必要的引數，引數的行為會是驅動程式而定。 必要的引數會在下表中列出。  
  
|函數|必要的引數|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*， *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|
