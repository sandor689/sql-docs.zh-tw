---
title: "SQLRowCount （資料指標程式庫） |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9460f4f4bbc522fc421b7e40b261fe17a8410a09
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount （資料指標程式庫）
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 Microsoft 建議使用驅動程式的資料指標功能。  
  
 本主題討論使用**SQLRowCount**資料指標程式庫中的函式。 如需一般資訊**SQLRowCount**，請參閱[SQLRowCount 函數](../../../odbc/reference/syntax/sqlrowcount-function.md)。  
  
 當應用程式呼叫**SQLRowCount**資料指標程式庫會傳回資料指標相關聯的陳述式，它已從驅動程式所擷取的資料列數目。  
  
 當應用程式呼叫**SQLRowCount**定位的 update 或 delete 陳述式相關聯的陳述式，資料指標程式庫傳回的陳述式所影響的資料列數目。  
  
 當應用程式呼叫**SQLRowCount**之後**選取**陳述式，資料指標程式庫會傳回-1。