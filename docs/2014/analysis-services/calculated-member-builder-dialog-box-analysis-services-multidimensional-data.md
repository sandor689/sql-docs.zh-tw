---
title: 導出成員產生器對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.calculatedmemberbuilderdialog.f1
ms.assetid: 73b89a9f-f403-4ab8-99f7-e3ceb870c260
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8b2df3f9bdb11a344d332a50580a992680118afa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220498"
---
# <a name="calculated-member-builder-dialog-box-analysis-services---multidimensional-data"></a>導出成員產生器對話方塊 (Analysis Services - 多維度資料)
  使用 **中的** [導出成員產生器] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 對話方塊，即可建立導出成員。  
  
## <a name="options"></a>選項。  
  
|詞彙|定義|  
|----------|----------------|  
|**名稱**|鍵入導出成員的名稱。|  
|**父階層**|選取導出成員建立所在的階層。|  
|**父成員**|如果您選取的父階層，會啟用此選項 (而非`Measures`維度) 具有一個以上層級。 按一下省略符號 (**…**) 按鈕可選取父成員。 此父成員會決定導出成員在維度結構內的位置。|  
|**運算式**|輸入將要使用的 MDX 運算式。|  
|**檢查**|按一下 **[檢查]** 即可測試 **[運算式]** 中所定義的 MDX 運算式。|  
|**中繼資料**|顯示目前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的中繼資料，這可以包含在 **[運算式]** 中所定義的 MDX 運算式內。<br /><br /> 以滑鼠右鍵按一下選取的項目，並選取 [複製]，或是將選取的項目拖曳至 [運算式]，即可複製該項目的 MDX 語法。|  
|**函數**|顯示目前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體可用的 MDX 函數。 列出的項目擷取自 MDSCHEMA_FUNCTIONS 結構描述資料列集。<br /><br /> 以滑鼠右鍵按一下選取的項目，並選取 [複製]，或是將選取的項目拖曳至 [運算式]，即可複製該項目的 MDX 語法。|  
  
## <a name="see-also"></a>另請參閱  
 [多維度運算式&#40;MDX&#41;參考](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  