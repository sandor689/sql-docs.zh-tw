---
title: 支援的查詢類型 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Delete query
- queries [SQL Server], types
- Update query
- Query Designer [SQL Server], query types
- Criteria pane
- Insert Values query
- Select query
- Make Table query
- Insert Results query
- Diagram pane [Visual Database Tools]
- View Designer, query types
ms.assetid: 72b9116c-c128-4078-a78d-257a2955a3f6
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 865bdf79fa72817ed3f3855be855c908d669dd10
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299418"
---
# <a name="supported-query-types-visual-database-tools"></a>支援的查詢類型 (Visual Database Tools)
  在[查詢和檢視表設計工具](visual-database-tools.md)的 [圖表] 和 [準則] 窗格 (圖形窗格) 中，您可以建立下列查詢類型：  
  
-   **選取查詢** ：從一或多個資料表或檢視擷取資料。 此類查詢將建立 SQL SELECT 陳述式。  
  
-   **插入結果** ：將一個資料表的現有資料列複製到另一個資料表，或複製到同一個資料表中做為新的資料列，以建立新的資料列。 此類查詢將建立 SQL INSERT INTO...SELECT 陳述式。  
  
-   **插入值** ：建立新資料列，並將新值插入至指定的資料行。 此類查詢將建立 SQL INSERT INTO...VALUES 陳述式。  
  
-   **更新查詢** ：變更資料表中一或多個現有資料列中的個別資料行值。 此類查詢將建立 SQL UPDATE…SET 陳述式。  
  
-   **刪除查詢** ：從資料表移除一或多個資料列。 這類查詢將建立 SQL DELETE 陳述式。  
  
    > [!NOTE]  
    >  [刪除查詢] 會刪除資料表中的整個資料列。 如果您要刪除個別的資料欄值，請使用 UPDATE 查詢。  
  
-   **製成資料表查詢** ：建立新資料表，並且將查詢結果複製到該新資料表中來建立資料列。 此類查詢將建立 SQL SELECT...INTO 陳述式。  
  
 除了使用圖形窗格來建立查詢外，您可以將任何 SQL 陳述式輸入 SQL 窗格，如聯合查詢 (Union Query)。  
  
 當您使用 SQL 陳述式建立的查詢無法在圖形窗格顯示時，查詢和檢視設計師將使這些窗格變成暗灰色，表示他們無法反映您所建立的查詢。 但這些暗灰色的窗格仍處於作用中狀態，而且在許多情況下，您可以在這些窗格中變更查詢。 如果您的變更使得圖形窗格可以顯示查詢，這些窗格就不再是暗灰色了。  
  
## <a name="see-also"></a>另請參閱  
 [設計查詢和檢視表的使用說明主題&#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [查詢的類型 &#40;Visual Database Tools&#41;](types-of-queries-visual-database-tools.md)  
  
  
