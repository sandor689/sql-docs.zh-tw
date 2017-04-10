---
title: "複寫類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "複寫 [SQL Server], 類型"
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# 複寫類型
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供下列類型的分散式應用程式中使用的複寫︰  
  
-   異動複寫。 如需詳細資訊，請參閱 [異動複寫](../../relational-databases/replication/transactional/transactional-replication.md)。  
  
-   合併式複寫。 如需詳細資訊，請參閱 [合併式複寫](../../relational-databases/replication/merge/merge-replication.md)。  
  
-   快照式複寫。 如需詳細資訊，請參閱 [快照式複寫](../../relational-databases/replication/snapshot-replication.md)。  
  
 為應用程式選擇的複寫類型取決於許多因素，包括實體複寫環境、要複寫的資料類型和數量，以及資料是否在「訂閱者」端更新。 實體環境包括複寫所涉及的電腦數量和位置，以及這些電腦是用戶端 (工作站、膝上型電腦或手持式裝置) 還是伺服器。  
  
 各種類型的複寫通常會先對「發行者」和「訂閱者」之間的發行物件進行初始同步處理。 此初步同步處理可以執行複寫與 *快照*, ，這是所有的物件和指定的發行集資料的複本。 快照集建立後會傳遞到「訂閱者」。 對於某些應用程式，只需執行快照式複寫即可。 對於其他類型的應用程式，有必要讓後續的資料變更累加地流動至「訂閱者」。 某些應用程式還要求「訂閱者」端的變更流回「發行者」端。 異動複寫與合併式複寫可為這些類型的應用程式提供選項。  
  
 系統不會追蹤快照集複寫中的資料變更；每次套用快照集時，快照集會完全覆寫現有資料。 異動複寫透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 交易記錄檔追蹤變更，合併式複寫則透過觸發程序和中繼資料資料表追蹤變更。  
  
## 另請參閱  
 [複寫代理程式概觀](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  