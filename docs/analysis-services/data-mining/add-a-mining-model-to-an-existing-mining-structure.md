---
title: "將採礦模型加入至現有的採礦結構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "採礦模型 [Analysis Services], 加入"
  - "採礦結構 [Analysis Services], 採礦模型"
  - "加入採礦模型"
ms.assetid: fcf72300-0674-4e73-a826-9b8eeffefbb5
caps.latest.revision: 24
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 24
---
# 將採礦模型加入至現有的採礦結構
  在加入初始模型之後，您就可以將更多採礦模型加入至採礦結構中。 每一個模型必須包含存在於結構中的資料行，但您可以為每一個採礦模型定義不同的資料行使用方式。 如需如何定義採礦模型資料行的詳細資訊，請參閱[採礦模型資料行](../../analysis-services/data-mining/mining-model-columns.md)。  
  
### 若要將採礦模型加入至結構  
  
1.  從 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 [採礦模型] 功能表項目中，選取 [新增採礦模型]。  
  
     就會開啟 [新增採礦模型] 對話方塊。  
  
2.  在 [模型名稱] 之下，輸入新採礦模型的名稱。  
  
3.  在 [演算法名稱] 之下，選取用來建立採礦模型的演算法。  
  
4.  按一下 **[確定]**。  
  
 新的採礦模型就會出現在 [採礦模型] 索引標籤中。 模型會使用已存在於結構中的預設資料行。 如需如何修改資料行的相關資訊，請參閱[變更採礦模型的屬性](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)。  
  
## 請參閱＜  
 [採礦模型工作和使用說明](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  