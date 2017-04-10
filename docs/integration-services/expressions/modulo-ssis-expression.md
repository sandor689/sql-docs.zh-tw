---
title: "(模數) (SSIS 運算式) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "% (模數運算子)"
  - "除法運算的餘數"
  - "模數運算子 (%)"
ms.assetid: e2920821-2f5b-4c76-8db8-8b9eddf4606f
caps.latest.revision: 34
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 34
---
# (模數) (SSIS 運算式)
  提供第一個數值運算式除以第二個數值運算式之後的整數餘數。  
  
## 語法  
  
```  
  
dividend % divisor  
  
```  
  
## 引數  
 *dividend*  
 要執行除法的數值運算式。 *dividend* 可以是任何有效的數值運算式。 如需詳細資訊，請參閱 [Integration Services 資料類型](../../integration-services/data-flow/integration-services-data-types.md)  
  
 *divisor*  
 要除以被除數的數值運算式。 *divisor* 可以是任何有效的數值運算式 (零除外)。  
  
## 結果類型  
 由兩個引數的資料類型決定。 如需相關資訊，請參閱 [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md)。  
  
## 備註  
 這兩個運算式都須評估為帶正負號或不帶正負號的整數資料類型。  
  
 如果任一個運算元為 Null，則結果為 Null。  
  
 模數零不合法。  
  
## 運算式範例  
 此範例會計算來自兩個數值常值的模數。 結果為 3。  
  
```  
42 % 13  
```  
  
 此範例會計算來自 **SalesQuota** 資料行和數值常數的模數。  
  
```  
SalesQuota % 12  
```  
  
 此範例會計算來自 **Sales$** 和 **Month**這兩個數值變數的模數。 **Sales$** 變數必須加上方括號，因為名稱包含 $ 字元。 如需詳細資訊，請參閱[識別碼 &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md)。  
  
```  
@[Sales$] % @Month  
```  
  
 此範例使用模數運算子判斷 **Value** 變數的值為偶數或奇數，並使用條件運算子傳回描述結果的字串。 如需詳細資訊，請參閱 [? : &#40;條件式&#41; &#40;SSIS 運算式&#41;](../../integration-services/expressions/conditional-ssis-expression.md)。  
  
```  
@Value % 2 == 0? "even":"odd"  
```  
  
## 請參閱＜  
 [運算子優先順序與關聯性](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [運算子 &#40;SSIS 運算式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  