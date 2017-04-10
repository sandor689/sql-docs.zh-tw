---
title: "ROUND (SSIS 運算式) | Microsoft Docs"
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
  - "捨入運算式"
  - "ROUND 函數 [SSIS]"
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# ROUND (SSIS 運算式)
  傳回已經進位到指定長度或有效位數的數值運算式。 length 參數必須評估為整數。  
  
## 語法  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## 引數  
 *numeric_expression*  
 是有效數值類型的運算式。 如需詳細資訊，請參閱＜ [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)＞。  
  
 *長度*  
 是整數運算式。 它是 *numeric_expression* 進位到的有效位數。  
  
## 結果類型  
 與 *numeric*_*expression* 相同的類型。  
  
## 備註  
 *length* 引數必須評估為正整數或零。  
  
 如果引數為 Null，則 ROUND 會傳回 Null 結果。  
  
## 運算式範例  
 這些範例會將數值常值進位到長度 3。 第一個傳回結果為 137.1570，第二個為 137.1580。  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## 請參閱＜  
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  