---
title: MultiPoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dbbe51251adf9a681a817aa5e402a23f3b5dde2e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201138"
---
# <a name="multipoint"></a>MultiPoint
  A`MultiPoint`是零或多個點的集合。 `MultiPoint` 執行個體的界限是空的。  
  
## <a name="examples"></a>範例  
 下列範例會建立具有 SRID 23 和兩個點的 `geometry MultiPoint` 執行個體：一個點的座標為 (2, 3)，另一個點的座標為 (7, 8)，而 Z 值為 9.5。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 也可以使用 `MultiPoint` 來表示這個 `STMPointFromText()` 執行個體，如下所示。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 下列範例使用 `STGeometryN()` 方法來擷取集合中第一個點的描述。  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a>另請參閱  
 [點](point.md)   
 [空間資料 &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
