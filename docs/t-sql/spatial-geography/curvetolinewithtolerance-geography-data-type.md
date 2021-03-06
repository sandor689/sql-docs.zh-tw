---
title: CurveToLineWithTolerance (geography 資料型別) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CurveToLineWithTolerance_TSQL
- CurveToLineWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- CurveToLineWithTolerance method (geography)
ms.assetid: 74369c76-2cf6-42ae-b9cc-e7a051db2767
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e9f0f517bb9685c308999e8f3dca719cc145ed24
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38019746"
---
# <a name="curvetolinewithtolerance-geography-data-type"></a>CurveToLineWithTolerance (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  傳回包含圓弧線段之 **geography** 執行個體的多邊形近似值。  
  
## <a name="syntax"></a>語法  
  
```  
  
.CurveToLineWithTolerance( tolerance, relative )  
```  
  
## <a name="arguments"></a>引數  
 *tolerance*  
 這是 **double** 運算式，用來定義原始圓弧線段與其線性近似值之間的最大誤差。  
  
 *relative*  
 這是 **bool** 運算式，指出是否要使用偏差的相對最大值。 如果 relative 設為 false (0)，則會設定線性近似值的偏差絕對最大值。  如果 relative 設為 true (1)，則會以容錯參數與空間物件週框方塊之直徑的乘積來計算容錯。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geography**  
  
 CLR 傳回類型：**SqlGeography**  
  
## <a name="exceptions"></a>例外狀況  
 設定容錯 <= 0 會擲回 **ArgumentOutOfRange** 例外狀況。  
  
## <a name="remarks"></a>Remarks  
 這個方法允許為結果 **LineString** 指定容錯量。  
  
 **CurveToLineWithTolerance** 方法將針對 **CircularString** 或 **CompoundCurve** 執行個體傳回 **LineString** 執行個體，而針對 **CurvePolygon** 執行個體傳回 **Polygon** 執行個體。  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-different-tolerance-values-on-a-circularstring-instance"></a>A. 在 CircularString 執行個體上使用不同的容錯值  
 下列範例示範設定容錯如何影響從 `CircularString` 執行個體傳回的 `LineString` 執行個體：  
  
 ```
 DECLARE @g geography;  
 SET @g = geography::Parse('CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.01, 0).STNumPoints();
```  
  
### <a name="b-using-the-method-on-a-multilinestring-instance-containing-one-linestring"></a>B. 在包含一個 LineString 的 MultiLineString 執行個體上使用此方法  
 下列範例示範從只包含一個 `MultiLineString` 執行個體的 `LineString` 執行個體傳回的資料：  
  
 ```
 DECLARE @g geography;  
 SET @g = geography::Parse('MULTILINESTRING((-122.358 47.653, -122.348 47.649))');  
 SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
 ```  
  
### <a name="c-using-the-method-on-a-multilinestring-instance-containing-multiple-linestrings"></a>C. 在包含多個 LineString 的 MultiLineString 執行個體上使用此方法  
 下列範例示範從包含多個 `MultiLineString` 執行個體的 `LineString` 執行個體傳回的資料：  
  
 ```
 DECLARE @g geography;  
 SET @g = geography::Parse('MULTILINESTRING((-122.358 47.653, -122.348 47.649),(-123.358 47.653, -123.348 47.649))');  
 SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
 ```  
  
### <a name="d-setting-relative-to-true-for-an-invoking-curvepolygon-instance"></a>D. 為叫用 CurvePolygon 執行個體，將 relative 設為 true  
 下列範例使用 `CurvePolygon` 執行個體，在 *relative* 設為 true 時呼叫 `CurveToLineWithTolerance()`：  
  
 ```
 DECLARE @g geography = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658), (-122.348 47.658, -122.358 47.658, -122.358 47.653)))';  
 SELECT @g.CurveToLineWithTolerance(.5,1).ToString();
 ```  
  
## <a name="see-also"></a>另請參閱  
 [地理例項上擴充的方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
