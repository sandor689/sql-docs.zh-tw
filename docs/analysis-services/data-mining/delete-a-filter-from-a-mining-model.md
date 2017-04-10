---
title: "從採礦模型刪除篩選 | Microsoft Docs"
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
  - "篩選 [Analysis Services]"
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 13
---
# 從採礦模型刪除篩選
  當您建立採礦模型的篩選時，您可以在資料來源檢視中的資料子集上建立模型。 篩選對於測試原始資料子集上之模型的精確度也非常實用。  
  
 不過，如果想要再次檢視完整的案例集，則必須刪除篩選。 此程序描述如何移除篩選的條件，或完全刪除篩選。  
  
### 若要從採礦模型的篩選刪除條件  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的 [方案總管] 中，按一下包含要篩選的採礦模型的採礦結構。  
  
2.  按一下 **[採礦模型]** 索引標籤。  
  
3.  選擇模型，然後以滑鼠右鍵按一下，開啟快速鍵功能表。  
  
     -或-  
  
     選取此模型。 在 **[採礦模型]** 功能表上，選取 **[設定模型篩選器]**。  
  
4.  在 [模組篩選器] 對話方塊中，以滑鼠右鍵在方格中按一下包含所要刪除之條件的資料列。  
  
5.  選取 **[刪除]**。  
  
### 若要在篩選編輯器對話方塊中清除採礦模型上的篩選  
  
-   在 [篩選編輯器] 對話方塊中，以滑鼠右鍵在方格中按一下任何資料列，然後選取 [全部刪除]。  
  
## 利用屬性視窗使用模型篩選  
 如果想要刪除整個篩選，就不需要開啟篩選編輯器對話方塊。 您建立的篩選條件可用於採礦模型的 **Filter** 屬性。  
  
> [!NOTE]  
>  您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中檢視採礦模型的屬性，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中則不能。  
  
#### 若要在方案總管中清除採礦模型上的篩選  
  
1.  在 [方案總管] 中，按一下包含篩選的採礦模型。  
  
2.  在 [屬性] 視窗中，以滑鼠右鍵按一下 **Filter** 屬性中的篩選文字，然後選取 [全選]。  
  
3.  按退格鍵或 Delete 鍵。  
  
## 請參閱＜  
 [鑽研採礦模型的案例資料](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)   
 [採礦模型工作和使用說明](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [採礦模型的篩選 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  