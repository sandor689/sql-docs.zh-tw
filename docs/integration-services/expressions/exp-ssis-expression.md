---
title: "EXP (SSIS 運算式) | Microsoft Docs"
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
  - "指數函數"
  - "EXP 函數"
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
caps.latest.revision: 34
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 34
---
# EXP (SSIS 運算式)
  傳回做為數值運算式中 e 之基底的指數。 EXP 函數會補充 LN 函數的動作，有時亦稱為反對數 (Antilogarithm)。  
  
## 語法  
  
```  
  
EXP(numeric_expression)  
```  
  
## 引數  
 *numeric_expression*  
 有效的數值運算式。  
  
## 結果類型  
 DT_R8  
  
## 備註  
 numeric expression 會在計算指數之前轉換成 DT_R8 資料類型。 如需詳細資訊，請參閱＜ [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)＞。  
  
 傳回結果永遠為正數。  
  
## 運算式範例  
 這些範例會將 EXP 函數套用至正值、負值和零值。  
  
```  
EXP(74)  
```  
  
 傳回 1.373382979540176E+32。  
  
```  
EXP(-27)  
```  
  
 傳回 1.879528816539083E-12。  
  
```  
EXP(0)  
```  
  
 傳回 1。  
  
## 請參閱＜  
 [LOG &#40;SSIS 運算式&#41;](../../integration-services/expressions/log-ssis-expression.md)   
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  