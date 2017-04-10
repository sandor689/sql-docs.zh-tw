---
title: "變更採礦結構的屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "採礦結構 [Analysis Services]，屬性"
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 28
---
# 變更採礦結構的屬性
  採礦結構有兩種屬性，這兩種屬性都可以修改：  
  
-   影響整個採礦結構的採礦結構屬性  
  
-   採礦結構中個別資料行的屬性  
  
 請注意，某些屬性相依於其他屬性設定值。 例如，在您將資料行的資料類型設定為 **Discretized** 之前，無法設定控制收納行為的屬性 (例如 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 或 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>)。  
  
 如需採礦結構屬性的詳細資訊，請參閱 [Mining Structure Columns](../../analysis-services/data-mining/mining-structure-columns.md) (採礦結構資料行)。  
  
### 若要變更採礦結構的屬性  
  
1.  在資料採礦設計師的 [採礦結構] 索引標籤上，以滑鼠右鍵按一下採礦結構或採礦結構中的資料行，然後選取 [屬性]。  
  
     如果 **[屬性]** 視窗還沒有出現，則它會在螢幕的右邊開啟。  
  
2.  在 **[屬性]** 視窗中，選取對應到您要變更之屬性的值，然後輸入新值。  
  
     您在設計師中選取其他元素時，新值就會生效。  
  
## 請參閱＜  
 [採礦結構工作和使用說明](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  