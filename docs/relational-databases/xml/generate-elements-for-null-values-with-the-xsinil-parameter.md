---
title: "使用 XSINIL 參數為 NULL 值產生元素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR XML 子句, null 值"
  - "null 值 [SQL Server], XML"
  - "ELEMENTS 指示詞"
  - "XSINIL 參數"
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# 使用 XSINIL 參數為 NULL 值產生元素
  **ELEMENTS** 指示詞可建構 XML，在其中每個資料行值都對應到 XML 中的元素。 若資料行值為 NULL，則不會加入任何元素。 若在 ELEMENTS 指示詞上指定選擇性的 **XSINIL** 參數，您可以要求也為 NULL 值建立元素。 在此情況下，對於每個 NULL 資料行值，會傳回一個 **xsi:nil** 屬性設定成 TRUE 的元素。  
  
## 另請參閱  
 [使用 FOR XML 的 RAW 模式](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  