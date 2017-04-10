---
title: "MSSQL_ENG020572 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG020572 錯誤"
ms.assetid: 636566db-ffcf-4109-8c11-15b8c7cb9cd9
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# MSSQL_ENG020572
    
## 訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|20572|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|訂閱者 '%s' 訂閱的發行項 '%s' (在發行集 '%s' 中)，已經在驗證失敗後重新初始化。|  
  
## 說明  
 訂閱者端的資料是依據發行者端的資料進行驗證，而資料不相符，因此驗證失敗。 在指定應該執行驗證時，您選取了如果驗證失敗則訂閱應該重新初始化的選項。 重新初始化訂閱涉及了在訂閱者端套用新的快照集。 如需有關驗證的詳細資訊，請參閱 [驗證複寫資料](../../relational-databases/replication/validate-replicated-data.md)。  
  
## 使用者動作  
 在訂閱者端套用新快照集之後，發行者端和訂閱者端的資料將會相符。  
  
## 另請參閱  
 [錯誤和事件參考 & #40。複寫 & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  