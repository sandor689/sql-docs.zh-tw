---
title: 更新、 刪除或依書籤提取 |Microsoft 文件
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
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9b919d30d604410a30ae4c844471c1557b6a2a9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914853"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>更新、 刪除或讀取書籤
書籤可以用來識別要更新結果集中，刪除從結果集，或從結果集的資料列集的緩衝區中提取的資料。 這些作業都是透過呼叫**SQLBulkOperations**與*選項*SQL_UPDATE_BY_BOOKMARK、 SQL_DELETE_BY_BOOKMARK 或 SQL_FETCH_BY_BOOKMARK 的引數。 這些作業中使用這些書籤會儲存在緩衝區資料列集的資料行 0。 在更新的書籤時，結果集資料行的資料會更新為會從資料列集的緩衝區。 如需詳細資訊，請參閱[更新的資料與 SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)。
