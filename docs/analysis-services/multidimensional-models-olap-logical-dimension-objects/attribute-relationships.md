---
title: 屬性關聯性 |Microsoft 文件
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9035cc2c0d3308848b570ae6c157c9d70cd77cc9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022345"
---
# <a name="attribute-relationships"></a>中，使用 [維度設計師] 的
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  在[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，維度內的屬性會一律直接或間接與相關的索引鍵屬性。 當您根據所有維度屬性都是衍生自相同關聯式資料表的星狀結構描述來定義維度時，便會在索引鍵屬性和維度的每個非索引鍵屬性之間，自動定義屬性關聯性。 而根據維度屬性是衍生自多個相關資料表的雪花式結構描述來定義維度時，便會自動定義下列的屬性關聯性：  
  
-   索引鍵屬性和繫結到主維度資料表之資料行的每個非索引鍵屬性之間。  
  
-   索引鍵屬性和繫結到連結基礎維度資料表之次要資料表的外部索引鍵屬性之間。  
  
-   在繫結到次要資料表之外部索引鍵的屬性和繫結到次要資料表中之資料行的非索引鍵屬性之間。  
  
 然而，您可能會需要變更這些預設的屬性關聯性。 例如，您可能會想要定義自然階層、自訂排序順序或依據非索引鍵屬性的維度資料粒度。 如需詳細資訊，請參閱[Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)。  
  
> [!NOTE]  
>  在多維度運算式 (MDX) 中，屬性關聯性就是所謂的成員屬性。  
  
## <a name="natural-hierarchy-relationships"></a>自然階層關聯性  
 當使用者自訂階層中所含的每一個屬性有一對多的關聯性，而且底下緊接著該屬性時，此階層就是自然階層。 例如，假設客戶維度所依據的關聯式來源資料表中有八個資料行：  
  
-   CustomerKey  
  
-   CustomerName  
  
-   Age  
  
-   Gender  
  
-   EMail  
  
-   City  
  
-   Country  
  
-   Region  
  
 對應的 Analysis Services 維度有七個屬性：  
  
-   客戶 (根據 CustomerKey，使用 CustomerName 提供成員名稱)  
  
-   年齡、性別、電子郵件、城市、區域、國家 (地區)  
  
 代表自然階層之關聯性的強制執行方式，是在某層級的屬性以及該層級底下之層級的屬性之間建立屬性關聯性。 若是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，這樣會指定自然關聯性與潛在彙總。 在客戶維度中，國家 (地區)、區域、城市和客戶等屬性都存在著自然階層。 `{Country, Region, City, Customer}` 的自然階層，會藉由加入下列屬性關聯性來描述：  
  
-   國家 (地區) 屬性與區域屬性之間的屬性關聯性。  
  
-   區域屬性與城市屬性之間的屬性關聯性。  
  
-   城市屬性與客戶屬性之間的屬性關聯性。  
  
 瀏覽 cube 中的資料，您也可以建立使用者定義的階層不代表自然階層中的資料 (稱為*臨機操作*或*reporting*階層)。 例如，您可以根據 `{Age, Gender}` 建立使用者自訂階層。 雖然自然階層可以利用彙總和索引結構獲得好處，其中含有來源資料中的自然關聯性，但使用者對於這兩個階層的行為並不會察覺到任何差異，因為這對於使用者是隱藏。  
  
 **SourceAttribute**層級的屬性會決定哪一個屬性用來描述層級。 **KeyColumns**屬性的屬性上指定的資料行，提供成員資料來源檢視中。 **NameColumn**屬性的屬性上的成員可以指定不同的名稱資料行。  
  
 若要使用的使用者定義階層中定義層級[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、**維度設計師**可讓您從資料來源檢視中包含的相關資料表中選取維度屬性、 維度資料表中的資料行或資料行在 cube 中。 如需有關如何建立使用者定義階層的詳細資訊，請參閱[Create User-Defined 階層](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)。  
  
 在 Analysis Services 中，通常會對成員的內容進行假設。 分葉成員並沒有下階，且包含衍生自基礎資料來源的資料。 非分葉成員具有下階，且包含衍生自在子成員上執行之彙總的資料。 在彙總層級中，成員是以從屬層級的彙總為基礎。 因此，當**IsAggregatable**屬性設定為**False**層級之來源屬性，在沒有任何彙總屬性應加入作為其上層級。  
  
## <a name="defining-an-attribute-relationship"></a>定義屬性關聯性  
 當您建立屬性關聯性時，其主要條件約束是要確定屬性關聯性所參考的屬性，在屬性關聯性所屬的屬性中，任何成員只有一個值。 例如，如果您在城市屬性與省份屬性間定義關聯性，每個城市就只能和單一省份相關。  
  
## <a name="attribute-relationship-queries"></a>屬性關聯性查詢  
 您可以使用 MDX 查詢擷取資料的成員屬性形式屬性關聯性，從**屬性**MDX 關鍵字**選取**陳述式。 如需如何使用 MDX 來擷取成員屬性的詳細資訊，請參閱[使用成員屬性&#40;MDX&#41;](../../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [屬性和屬性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [維度屬性 （Property） 參考](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)   
 [使用者階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [使用者階層屬性](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
