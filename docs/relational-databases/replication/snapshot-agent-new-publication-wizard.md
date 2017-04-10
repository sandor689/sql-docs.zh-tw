---
title: "快照集代理程式 (新增發行集精靈) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.configuresnapshotagent.f1"
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# 快照集代理程式 (新增發行集精靈)
  快照集代理程式會建立檔案，檔案中包含用來初始化新訂閱的發行集結構描述和資料。 依預設，在新增發行集精靈中建立發行集之後，會立即執行快照集代理程式。 此後，代理程式就根據您指定的排程來執行。 代理程式每次執行時是否建立新的快照集檔案，視選擇的複寫類型和選項而定。 如需詳細資訊，請參閱 [建立並套用快照集](../../relational-databases/replication/create-and-apply-the-snapshot.md)。  
  
 對於使用參數化篩選的合併式發行集，在完成發行集快照集之後，您必須為資料的每一個資料分割建立快照集。 如需詳細資訊，請參閱 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)。  
  
## 選項  
 **立即建立快照集** （合併式複寫） 或 **立即建立快照集，並保留快照集可用來初始化訂閱** （交易式複寫）  
 選取此核取方塊即可在完成新增發行集精靈之後立即建立快照集。 如果您想要在產生快照集之後變更 **[發行集屬性]** 對話方塊中的快照集屬性，或要初始化不具有快照集的訂閱者，請清除此核取方塊。 如需詳細資訊，請參閱 [初始化交易式訂閱不使用快照集](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)。  
  
> [!NOTE]  
>  精靈可能會提示散發者的連接，以便為散發者代理程式或合併代理程式啟動適當的作業。  
  
 **排程快照集代理程式在下列時間執行**  
 接受執行快照集代理程式的預設排程，或按一下 **變更** 以指定的排程。  
  
## 另請參閱  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [建立和套用初始快照集](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [檢視及修改發行集屬性](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [使用快照集初始化訂閱](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [發行資料和資料庫物件](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [複寫代理程式概觀](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  