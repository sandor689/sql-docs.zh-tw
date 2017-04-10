---
title: "MultiPolygon | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MultiPolygon geometry 子類型 [SQL Server]"
  - "geometry 子類型 [SQL Server]"
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# MultiPolygon
  **MultiPolygon** 執行個體是零或多個 **Polygon** 執行個體的集合。  
  
## 多邊形執行個體  
 下圖顯示 **MultiPolygon** 執行個體的範例。  
  
 ![幾何 MultiPolygon 執行個體的範例](../../relational-databases/spatial/media/multipolygon.png "幾何 MultiPolygon 執行個體的範例")  
  
 如本圖所示：  
  
-   圖 1 是具有兩個 **Polygon** 元素的 **MultiPolygon** 執行個體。 界限是由兩個外部環形和三個內部環形所定義。  
  
-   圖 2 是具有兩個 **MultiPolygon** 元素的 **Polygon** 執行個體。 界限是由兩個外部環形和三個內部環形所定義。 這兩個 **Polygon** 元素會在正切點相交。  
  
### 已接受的執行個體  
 如果下列其中一個條件成立，則接受 **MultiPolygon** 執行個體。  
  
-   它是空的 **MultiPolygon** 執行個體。  
  
-   組成 **MultiPolygon** 執行個體的所有執行個體都是可接受的 **Polygon** 執行個體。 如需可接受的 **Polygon** 執行個體的詳細資訊，請參閱＜ [Polygon](../../relational-databases/spatial/polygon.md)＞。  
  
 下列範例會顯示可接受的 **MultiPolygon** 執行個體。  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
```  
  
 下列範例示範會擲出 `System.FormatException`的 MultiPolygon 執行個體。  
  
```  
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';  
```  
  
 MultiPolygon 中的第二個執行個體是 LineString 執行個體，不是可接受的 Polygon 執行個體。  
  
### 有效的執行個體  
 如果 **MultiPolygon** 執行個體是空的 **MultiPolygon** 執行個體或符合下列準則，則為有效的執行個體。  
  
1.  組成 **MultiPolygon** 執行個體的所有執行個體都是有效的 **Polygon** 執行個體。 如需有效的 **Polygon** 執行個體，請參閱＜ [Polygon](../../relational-databases/spatial/polygon.md)＞。  
  
2.  組成 **Polygon** 執行個體的所有 **MultiPolygon** 執行個體彼此不會重疊。  
  
 下列範例示範兩個有效的 **MultiPolygon** 執行個體和一個無效的 **MultiPolygon** 執行個體。  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g2` 有效，因為這兩個 **Polygon** 執行個體只在一個相切點接觸。 `@g3` 無效，因為這兩個 **Polygon** 執行個體的內部互相重疊。  
  
## 範例  
 下列範例示範 `geometry``MultiPolygon` 執行個體的建立作業，並傳回第二個元件的 Well-Known Text (WKT)。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');  
SELECT @g.STGeometryN(2).STAsText();  
```  
  
 此範例會具現化空的 `MultiPolygon` 執行個體。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');  
```  
  
## 另請參閱  
 [多邊形](../../relational-databases/spatial/polygon.md)   
 [STArea &#40;geometry Data Type&#41;](../../t-sql/spatial-geometry/starea-geometry-data-type.md)   
 [STCentroid &#40;geometry Data Type&#41;](../../t-sql/spatial-geometry/stcentroid-geometry-data-type.md)   
 [STPointOnSurface &#40;geometry Data Type&#41;](../../t-sql/spatial-geometry/stpointonsurface-geometry-data-type.md)   
 [空間資料 &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  