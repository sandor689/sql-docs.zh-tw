---
title: "保護發行者 | Microsoft Docs"
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
  - "登入 [SQL Server 複寫], 發行集存取清單"
  - "發行集 [SQL Server 複寫], 發行集存取清單"
  - "發行集存取清單 (PAL)"
  - "PAL (發行集存取清單)"
  - "發行者 [SQL Server 複寫], 安全性"
  - "發行集 [SQL Server 複寫], 安全性"
ms.assetid: 4513a18d-dd6e-407a-b009-49dc9432ec7e
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 48
---
# 保護發行者
  下列複寫代理程式連接到發行者：  
  
-   記錄讀取器代理程式  
  
-   快照集代理程式  
  
-   佇列讀取器代理程式  
  
-   合併代理程式  
  
 我們建議您為這些代理程式提供適當的登入，遵循授與所需最小權限的原則，並保護所有密碼的儲存。 如需有關各代理程式需要的權限資訊，請參閱＜ [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)＞。  
  
 除了適當地管理登入和密碼以外，您還必須了解發行集存取清單 (PAL) 的角色。 PAL 是用來啟用登入以存取發行集資料，並同時限制在發行者端進行的資料庫特定存取。  
  
## 發行集存取清單  
 PAL 是在發行者端保護發行集安全的主要機制。 PAL 功能類似於 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 存取控制清單。 建立發行集之後，複寫便會建立此發行集的 PAL。 PAL 可進行設定，使其包含已授與了對發行集存取權的登入與群組清單。 當代理程式連接到「發行者」或「散發者」並要求存取發行集時，便會將 PAL 上的驗證資訊與代理程式提供的「發行者」登入進行比較。 這項處理序藉由防止用戶端工具使用「發行者」與「散發者」登入在「發行者」上直接進行修改，為「發行者」提供了額外的安全性。  
  
> [!NOTE]  
>  複寫會在「發行者」上為每個發行集建立角色，以強制賦予 PAL 成員資格。 該角色具有名稱形式 **Msmerge_***\< PublicationID>* 合併式複寫和 **MSReplPAL_***\< PublicationDatabaseID>***_***\< PublicationID>* 交易式與快照式複寫。  
  
 根據預設，下列登入包含在 PAL 內：建立發行集時的 **sysadmin** (系統管理員) 固定伺服器角色成員，以及用來建立發行集的登入。 根據預設，所有的登入是成員的 **sysadmin** 固定的伺服器角色或 **db_owner** 發行集資料庫上的固定的資料庫角色可以訂閱發行集而不需要明確加入 PAL。  
  
 使用 PAL 時，請考慮下列指導方針：  
  
-   您必須先將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入關聯到發行集資料庫中的資料庫使用者，才能夠將該登入加入 PAL 中。  
  
-   遵循最小權限原則，僅授與 PAL 中登入執行複寫工作所需的權限。 請勿將登入加入任何不要求複寫的固定資料庫角色或伺服器角色中。 如需有關所需權限的詳細資訊，請參閱＜ [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) ＞和＜ [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)＞。  
  
-   如果使用遠端散發者，則 PAL 中的帳戶在發行者和散發者兩端都必須是可以使用的。 該帳戶必須是在兩部伺服器都已定義的網域帳戶或本機帳戶。 與兩個登入相關聯的密碼必須是一樣的。  
  
-   如果 PAL 包含 Windows 帳戶且網域使用 Active Directory，則執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的帳戶必須擁有從 Active Directory 進行讀取的權限。 如果您遇到 Windows 帳戶問題，請確定執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的帳戶擁有足夠的權限。 如需詳細資訊，請參閱 Windows 文件集。  
  
 若要管理 PAL，請參閱 [管理發行集存取清單中的登入](../../../relational-databases/replication/security/manage-logins-in-the-publication-access-list.md)。  
  
## 快照集代理程式  
 每個發行集都有一個「快照集代理程式」。 如需詳細資訊，請參閱 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)。  
  
## FTP 快照集傳遞  
 如果您將快照集指定為應該透過 FTP 共用而不是 UNC 共用來使用，則在設定 FTP 存取時必須指定登入和密碼。 如需詳細資訊，請參閱 [Deliver a Snapshot Through FTP](../../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)。  
  
## 記錄讀取器代理程式  
 每個為異動複寫發行的資料庫，都會有一個記錄讀取器代理程式。 如需詳細資訊，請參閱 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)。  
  
## 佇列讀取器代理程式  
 所有與給定「散發者」相關聯的「發行者」和發行集 (允許佇列更新訂閱) 都有一個「佇列讀取器代理程式」。 如需詳細資訊，請參閱 [啟用更新訂閱交易式發行集](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)。  
  
## 另請參閱  
 [啟用加密的連接 Database Engine & #40。SQL Server 組態管理員 & #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [複寫安全性最佳做法](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [安全性和保護 & #40。複寫 & #41;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  