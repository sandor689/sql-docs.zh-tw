---
title: Hierarchize (MDX) |Microsoft 文件
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4478fb9657ef4577bcae8b5641f53154b2a0486c
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740917"
---
# <a name="hierarchize-mdx"></a>Hierarchize (MDX)


  以階層式架構排列集合成員。  
  
## <a name="syntax"></a>語法  
  
```  
  
Hierarchize(Set_Expression [ , POST ] )  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 **Hierarchize**函式會將指定集合的成員組織成階層式順序。 此函數永遠會保留重複項。  
  
-   如果**POST**未指定，此函式會排序它們的自然順序中的層級中的成員。 未指定其他排序條件時，它們的自然順序就是階層中成員的預設順序。 子成員會直接跟隨在父成員後面。  
  
-   如果**POST**指定，則**Hierarchize**函數會使用自訂的順序的層級中的成員來排序。 換言之，子成員會在其父系之前。  
  
## <a name="example"></a>範例  
 下列範例會在 Canada 成員向上鑽研。 **Hierarchize**函式用來組織指定的集合成員以階層順序，所需的**DrillUpMember**函式。  
  
```  
SELECT DrillUpMember   
   (  
      Hierarchize  
         (  
            {[Geography].[Geography].[Country].[Canada]  
            ,[Geography].[Geography].[Country].[United States]  
            ,[Geography].[Geography].[State-Province].[Alberta]  
            ,[Geography].[Geography].[State-Province].[Brunswick]  
            ,[Geography].[Geography].[State-Province].[Colorado]   
            }  
         ), {[Geography].[Geography].[Country].[United States]}  
   )  
ON 0  
FROM [Adventure Works]  
```  
  
 下列範例會傳回的 sum`Measures.[Order Quantity]`成員進行彙總前 9 個月中含括之 2003年`Date`維度中，從**Adventure Works** cube。 **PeriodsToDate**函式定義的彙總函式可用於在集合中的 tuple。 **Hierarchize**函式會將組織指定的集合成員以階層順序的 [產品] 維度的成員。  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS Count  
   (Filter  
      (Existing  
         (Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] <   
               ([Measures].[Reseller Sales Amount],[Date].Calendar.PrevMember)  
        )  
    )  
MEMBER [Geography].[State-Province].x AS Aggregate   
( {[Geography].[State-Province].&[WA]&[US],   
   [Geography].[State-Province].&[OR]&[US] }   
)  
SELECT NON EMPTY HIERARCHIZE   
   (AddCalculatedMembers   
      ({DrillDownLevel  
         ({[Product].[All Products]})}  
        )  
    ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
   [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
   [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
