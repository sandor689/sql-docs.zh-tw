---
title: 預設 C 資料類型 |Microsoft 文件
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
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec05e58cd651497b07e131d4c3dcfe2e70baa04f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906413"
---
# <a name="default-c-data-types"></a>預設 C 資料類型
如果應用程式指定 SQL_C_DEFAULT 中的**SQLBindCol**， **SQLGetData**，或**SQLBindParameter**，驅動程式會假設 C 資料類型的輸出或輸入的緩衝區對應至 SQL 資料類型之資料行的緩衝區繫結的參數。  
  
> [!IMPORTANT]  
>  互通的應用程式不應該使用 SQL_C_DEFAULT。 相反地，它們應該一律指定它們使用之緩衝區的 C 類型。 這是因為驅動程式一定會正確地無法判斷預設的 C 類型，原因如下：  
  
-   如果 DBMS 會升級 SQL 資料型別之資料行或參數，此驅動程式無法判斷原始的 SQL 資料類型的資料行或參數。 因此，它無法判斷與對應的預設 C 資料類型。  
  
-   如果驅動程式無法判斷是否已簽署的特定資料行或參數，為一般的情況是當這是由 DBMS，驅動程式無法判斷對應的預設 C 資料類型是否應該簽署或不帶正負號。  
  
     因為方便程式設計只提供 SQL_C_DEFAULT，應用程式不會遺失任何功能時，它會指定實際的 C 資料類型。  
  
 顯示每個 SQL 資料類型的預設 C 資料類型的資料表包含在[轉換資料從 SQL 到 C 資料類型](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)稍後在本附錄中。
