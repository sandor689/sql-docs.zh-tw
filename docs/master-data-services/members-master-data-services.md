---
title: "成員 (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分葉成員 [Master Data Services]"
  - "合併成員 [Master Data Services]"
  - "合併成員 [Master Data Services], 關於合併成員"
  - "成員 [Master Data Services], 關於成員"
  - "分葉成員 [Master Data Services], 關於分葉成員"
  - "成員 [Master Data Services]"
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
caps.latest.revision: 16
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 14
---
# 成員 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，成員是指實體主要資料。 例如，成員可以是 Product 實體中的 Road-150 bike，或是 Customer 實體中的特定客戶。  
  
## 成員如何與其他的模型物件相關聯  
 您可以將成員視為資料表中的資料列。 相關成員包含在一個實體中，而且每個成員都由屬性值定義。  
  
 在此範例中，資料表代表實體、資料表中的資料列代表成員，而資料表中的資料行則代表屬性。 每個資料格代表特定成員的屬性值。  
  
 ![以資料表表示的 Master Data Services 實體](../master-data-services/media/mds-conc-entity-table.gif "以資料表表示的 Master Data Services 實體")  
  
## 成員類型  
 有三種類型的成員：分葉成員、合併成員和集合成員。  
  
 分葉成員是實體中的預設成員。  
  
-   在衍生階層中，分葉成員是唯一的成員類型。 某個實體的分葉成員會做為另一個實體之分葉成員的父系。  
  
-   在明確階層中，分葉成員是最低層級，沒有子系。  
  
 只有在啟用實體的明確階層和集合時，合併成員才會存在。  
  
-   衍生階層不包含合併成員。  
  
-   在明確階層中，合併成員可以是階層中其他成員的父系，也可以是子系。  
  
## 使用階層與集合來組織成員  
 階層和集合可以用來為成員分組，以進行報告或分析。 如需詳細資訊，請參閱[階層 &#40;Master Data Services&#41;](../master-data-services/hierarchies-master-data-services.md) 和[集合 &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)。  
  
## 成員範例  
 在下列範例中，每個成員是由 Name、Code、Subcategory、StandardCost、ListPrice 和 FilePhoto 屬性值所組成。  
  
 ![自行車產品實體資料表](../master-data-services/media/mds-conc-entity-table-w-data.gif "自行車產品實體資料表")  
  
## 相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|建立新分葉成員。|[建立分葉成員 &#40;Master Data Services&#41;](../master-data-services/create-a-leaf-member-master-data-services.md)|  
|建立新合併成員。|[建立合併成員 &#40;Master Data Services&#41;](../master-data-services/create-a-consolidated-member-master-data-services.md)|  
|刪除現有的成員或集合。|[刪除成員或集合 &#40;Master Data Services&#41;](../master-data-services/delete-a-member-or-collection-master-data-services.md)|  
|重新啟用刪除的成員或集合。|[重新啟用成員或集合 &#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)|  
|更新成員的屬性值。|[變更屬性類型 &#40;適用於 Excel 的 MDS 增益集&#41;](../master-data-services/microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|  
|在階層中移動成員。|[在階層中移動成員 &#40;Master Data Services&#41;](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|修正合併衝突。|[合併衝突 &#40;Master Data Services&#41;](../master-data-services/merge-conflicts-master-data-services.md)|  
  
## 相關內容  
  
-   [Master Data Services 概觀 &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
-   [實體 &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
-   [屬性 &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
-   [階層 &#40;Master Data Services&#41;](../master-data-services/hierarchies-master-data-services.md)  
  
-   [集合 &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)  
  
-   [分葉權限 &#40;Master Data Services&#41;](../master-data-services/leaf-permissions-master-data-services.md)  
  
-   [合併的權限 &#40;Master Data Services&#41;](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)  
  
-   [篩選運算子 &#40;Master Data Services&#41;](../master-data-services/filter-operators-master-data-services.md)  
  
  