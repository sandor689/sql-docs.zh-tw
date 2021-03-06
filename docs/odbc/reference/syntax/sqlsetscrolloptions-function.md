---
title: SQLSetScrollOptions 函式 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5cebcb3c31234d24971e4a2a0226110a653ce256
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917013"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions 函式
**一致性**  
 版本引進了： ODBC 1.0 標準相容性： 已被取代  
  
 **摘要**  
 在 ODBC 3 *.x*，ODBC 2.0 函式**SQLSetScrollOptions**已由呼叫取代**SQLGetInfo**和**SQLSetStmtAttr**。  
  
> [!NOTE]  
>  如需有關什麼驅動程式管理員會對應到此函式時 ODBC 2 *.x*應用程式使用 ODBC 3 *.x*驅動程式，請參閱[對應已被取代的函式](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)中附錄 g： 驅動程式的指導方針回溯相容性。  
  
> [!NOTE]  
>  當驅動程式管理員會將對應**SQLSetScrollOptions**應用程式使用 ODBC 3 *.x*不支援的驅動程式**SQLSetScrollOptions**，驅動程式管理員設定 SQL_ROWSET_SIZE 陳述式選項，而不將 SQL_ATTR_ROW_ARRAY_SIZE 陳述式屬性， *RowsetSize*引數中的**SQLSetScrollOption**。 如此一來， **SQLSetScrollOptions**不可由應用程式在呼叫提取多個資料列時， **SQLFetch**或**SQLFetchScroll**。 它可以用於擷取多個資料列呼叫時，只有**SQLExtendedFetch**。  
  
## <a name="remarks"></a>備註  
 如果您的應用程式會在 64 位元作業系統上執行，請參閱[ODBC 64 位元資訊](../../../odbc/reference/odbc-64-bit-information.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 應用程式開發介面參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)
