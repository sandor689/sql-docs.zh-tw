---
title: 第 4 課： 標記為日期資料表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5a2a6ce44a66fbb1e9045116580acc726f648df9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265744"
---
# <a name="lesson-4-mark-as-date-table"></a>第 4 課：標記為日期資料表
  在「第 2 課：加入資料」中，您已匯入了名為 DimDate 的維度資料表。 接著您在「第 3 課：重新命名資料行」中，將 DimDate 資料表重新命名為簡化的 Date。 當模型中的此資料表已命名為 Date 時，也可以稱作「日期資料表」，並會在其中包含日期及時間資料。  
  
 每當您在計算中使用時間智慧函數時，就像您稍後建立量值時一樣，必須指定日期資料表屬性，其中包含「日期資料表」，以及該資料表中的唯一識別碼「日期資料行」。 接著您就可以在其他資料表與此 Date 資料表之間建立有效的關聯性；這對於使用 DAX 時間智慧函數進行計算為必要步驟。  
  
 在這一課，您將標記所匯入並重新命名的 Date 資料表為「日期資料表」，而 Date 資料行 (包含在 Date 資料表中) 則會標記為「日期資料行」(唯一識別碼)。 所有 Date (日期) 名稱在使用上可能讓人感到混淆，但很快您就會理解這種概念。  
  
 完成本課程的估計時間： **3 分鐘**  
  
## <a name="prerequisites"></a>先決條件  
 本主題是表格式模型教學課程的一部分，必須依序完成。 在執行本課中的工作之前，您應已完成上一課： [第 3 課：重新命名資料行](rename-columns.md)。  
  
### <a name="to-set-mark-as-date-table"></a>設定標記為日期資料表  
  
1.  在模型設計師中，按一下 [Date] 資料表 (索引標籤)。  
  
2.  依序按一下 [資料表] 功能表、[日期] 和 [標記為日期資料表]。  
  
3.  在 [標記為日期資料表] 對話方塊的 [日期] 清單方塊中，選取 [日期] 資料行當作唯一識別碼。  
  
## <a name="next-steps"></a>後續步驟  
 若要繼續進行本教學課程，請前往下一課： [第 5 課：建立關聯性](lesson-4-create-relationships.md)。  
  
  
