---
title: 訂閱者屬性 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
caps.latest.revision: 22
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a38b712b520584f69acea3d065d226578097e059
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37350351"
---
# <a name="subscriber-properties"></a>訂閱者屬性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [訂閱者屬性] 對話方塊包含執行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本訂閱者的相關資訊。  
  
## <a name="options"></a>選項。  
 **代理程式至訂閱者的連接**  
 散發代理程式和合併代理程式從散發者連接至訂閱者所用的內容。這個選項只適用於 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以前的版本。  
  
 選取 **[模擬代理程式處理帳戶]** ，即可使用散發者端之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 帳戶的內容與訂閱者建立連接，或指定 **[SQL Server 驗證]**，然後輸入 **[登入]** 和 **[密碼]** 的值。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 建議您選取 **[模擬代理程式處理帳戶]**。  
  
 若為 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本，每個訂閱的連接資訊會在「新增訂閱精靈」中指定，而且可在 **[訂閱屬性]** 對話方塊中進行變更。  
  
 **預設代理程式排程**  
 執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以前 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]版本的訂閱者在「新增訂閱精靈」中使用的預設排程。  
  
 **其他**  
 包含訂閱者和訂閱者類型上的資訊。  
  
## <a name="see-also"></a>另請參閱  
 [檢視及修改散發者和發行者屬性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [屬性參考 &#40;複寫&#41;](../../relational-databases/replication/properties-reference-replication.md)   
 [訂閱發行集](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
