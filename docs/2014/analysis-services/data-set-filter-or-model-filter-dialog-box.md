---
title: 資料集篩選器或模型篩選器對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a9602174-b7e2-4e16-8ded-dfd8eb9264d7
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 34cb8f45c8380cffdfd58c99078f05fd5c8bd2e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187315"
---
# <a name="data-set-filter-or-model-filter-dialog-box"></a>資料集篩選器或模型篩選器對話方塊
  這個對話方塊可協助您建立能套用至資料集的篩選器。  資料集可以是用於字串的外部資料集，或採礦模型的案例資料。 對話方塊的名稱會根據篩選器是用於外部資料集或採礦模型而變更。  
  
 如果是將篩選器套用至新的資料集，則僅會使用資料集中符合條件的案例來評估資料採礦模型。 如果是將篩選器套用至採礦模型本身，則僅會使用現有測試資料集中符合篩選準則的案例來培訓及測試模型。  
  
-   [資料集篩選器] 對話方塊可從 [採礦精確度圖表] 設計師的 [輸入選擇] 索引標籤中存取。  
  
-   [模型篩選器] 對話方塊可從資料採礦設計師的 [採礦模型] 索引標籤中存取。  
  
-   您可在 [條件] 方格包含的資料行中指定資料表或資料行名稱、運算子和目標值。 基本上，您可以藉由使用此方格來建立 WHERE 子句。  
  
> [!TIP]  
>  若要測試原始定型資料子集的精確度，您可以加入曾用來將定型集定義為外部測試資料的資料來源檢視，然後在 [資料集篩選器] 方格中加入條件。  
  
 **如需詳細資訊，請參閱**：[測試和驗證 &#40;資料採礦&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>選項。  
 **條件**  
 顯示資料表名稱，後面跟著資料行名稱及條件。  
  
|值|描述|  
|-----------|-----------------|  
|**及/或**|選擇運算子來聯結多個條件。|  
|**採礦結構資料行**|按一下以選取資料來源，然後再按一下方格中的連續行來從資料來源新增資料行。<br /><br /> 方格中的第一行會指定資料來源檢視。 在選取資料來源檢視之後，[採礦結構資料行] 會顯示資料表圖示，而 [值] 欄位則顯示已為此資料來源所定義之所有準則的組合。<br /><br /> 在選取資料來源之後，[採礦結構資料行] 方塊會提供資料來源中個別資料行的下拉式清單。|  
|**[運算子]**|從清單選取運算子。|  
|**ReplTest1**|對於資料表而言，[值] 欄位會顯示套用至資料來源的所有篩選組合。 您也可以按一下文字方塊右側的建立按鈕 **(…)**，以開啟 [篩選] 對話方塊並建立條件。|  
  
 **運算式**  
 顯示您使用方格所建立的準則集。  
  
 **編輯查詢**  
 變更篩選編輯模式，使您可以直接在 [運算式] 文字方塊中輸入篩選運算式。  
  
> [!NOTE]  
>  對篩選運算式進行手動變更後，您將無法返回方格編輯模式，即使在 [輸入選擇] 索引標籤的 [篩選運算式] 方塊中儲存該運算式後也是如此。如果想要使用方格建立運算式，則必須刪除現有的篩選運算式，然後重新開始。  
  
 **還原查詢編輯**  
 將方格還原至先前的狀態，並取消對篩選運算式所做的任何變更。  
  
## <a name="see-also"></a>另請參閱  
 [測試及驗證工作與操作方法&#40;資料採礦&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [採礦精確度圖表設計師&#40;資料採礦&#41;](mining-accuracy-chart-designer-data-mining.md)  
  
  
