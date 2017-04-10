---
title: "偵測及解決合併式複寫衝突 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "合併式複寫衝突解決 [SQL Server 複寫], 關於衝突解決"
  - "預設 Conflict Resolver"
  - "衝突解決 [SQL Server 複寫]"
  - "檢視合併式複寫衝突"
  - "解決合併式複寫衝突"
  - "發行項 [SQL Server 複寫], 衝突解決"
  - "合併式複寫衝突解決 [SQL Server 複寫]"
  - "衝突解決 [SQL Server 複寫], 合併式複寫"
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# 偵測及解決合併式複寫衝突
  發行者與訂閱者連接並進行同步處理時，合併代理程式會偵測是否有任何衝突。 如果偵測到衝突，「合併代理程式」會使用衝突解決器來決定要接受並傳播到其他網站的資料。  
  
> [!NOTE]  
>  雖然訂閱者會與發行者同步，不過衝突通常是在不同訂閱者端所做的更新之間發生，而不是發生在訂閱者端和發行者端的更新。  
  
 合併複寫提供各種不同的方法用來偵測及解決衝突。 針對大部份的應用程式，預設方法即已適用：  
  
-   如果是在「發行者」和「訂閱者」之間發生衝突，則會保留「發行者」變更而放棄「訂閱者」變更。  
  
-   如果是在兩個使用客訂閱 (提取訂閱的預設類型) 的「訂閱者」之間發生衝突，則會保留第一個訂閱者為了與「發行者」保持同步所做的變更，而放棄第二個「訂閱者」的變更。 指定用戶端和伺服器訂閱的相關資訊，請參閱 [指定合併訂閱類型和衝突解決優先權 & #40。SQL Server Management Studio & #41;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md)。  
  
-   如果是在兩個使用主訂閱 (發送訂閱的預設類型) 的「訂閱者」之間發生衝突，則會保留具備最高優先權值的訂閱者的變更，而放棄另一個「訂閱者」的變更。 如果優先權的值相同，則會保留第一個「訂閱者」為了與「發行者」保持同步所做的變更。  
  
 如需合併複寫的衝突偵測與解決的詳細資訊，請參閱＜ [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)＞。  
  
## 另請參閱  
 [合併式複寫的發行項選項](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [訂閱發行集](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  