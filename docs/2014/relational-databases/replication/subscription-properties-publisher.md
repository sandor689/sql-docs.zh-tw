---
title: 訂閱屬性 - 發行者 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subproperties.publisher.f1
helpviewer_keywords:
- Subscription Properties dialog box
ms.assetid: d4b2bc8b-0431-4331-8305-8992c96d0d34
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 33bf497f637c85730c4a9276b728b17c115f75ec
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219128"
---
# <a name="subscription-properties---publisher"></a>訂閱屬性 - 發行者
  在發行者端的 **[訂閱屬性]** 對話方塊，可以讓您檢視和設定發送訂閱的屬性。 您也可以檢視提取訂閱的某些屬性，但在訂閱者端的 **[訂閱屬性]** 對話方塊，會顯示其他屬性並允許修改屬性。  
  
 **[訂閱屬性]** 對話方塊中的每個屬性包含一個描述。 按一下某個屬性，即可查看其在對話方塊底部顯示的描述。 此主題提供了關於一些屬性的其他資訊，其中大多數屬性僅會針對發行者端的發送訂閱顯示。 屬性會依下列類別目錄分組：  
  
-   套用至所有訂閱的屬性。  
  
-   套用至交易式訂閱的屬性。  
  
-   套用至合併訂閱的屬性。  
  
 如果選項顯示為唯讀，則只有在建立訂閱時才能設定。 如果想要設定新增訂閱精靈中無法使用的選項，請以預存程序建立訂閱。 如需相關資訊，請參閱 [Create a Pull Subscription](create-a-pull-subscription.md) 及 [Create a Push Subscription](create-a-push-subscription.md)。  
  
## <a name="options-for-all-subscriptions"></a>所有訂閱的選項。  
 **Security**  
 按一下 **[代理程式處理帳戶]** 資料列，然後按一下屬性 (**...**) 按鈕，即可變更散發代理程式或合併代理程式在散發者端用以執行的帳戶。 若要變更散發代理程式或合併代理程式連接到訂閱者時所用的帳戶，請按一下 **[訂閱者連接]**，然後按一下屬性按鈕 (**...**)。  
  
 如需有關每個代理程式所需之權限的詳細資訊，請參閱＜ [Replication Agent Security Model](security/replication-agent-security-model.md)＞。  
  
## <a name="options-for-transactional-subscriptions"></a>交易式訂閱的選項  
 **防止交易迴圈**  
 決定散發代理程式是否要將源自訂閱者端的交易，傳送回到訂閱者端。 此選項適用於雙向異動複寫。 如需詳細資訊，請參閱 [Bidirectional Transactional Replication](transactional/bidirectional-transactional-replication.md)。  
  
 **可更新的訂閱**  
 決定訂閱者變更是否會複寫回發行者。 可以使用佇列更新或立即更新來複寫變更。 **[訂閱者更新方法]** 選項會決定要使用的方法。 如需詳細資訊，請參閱 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)。  
  
## <a name="options-for-merge-subscriptions"></a>合併訂閱的選項  
 **資料分割定義 (HOST_NAME)**  
 針對使用參數化篩選的發行集，合併式複寫會在同步處理過程中評估兩個系統函數之一 (如果篩選參考兩個函數，則兩個都會評估)，以決定訂閱者應接收的資料： **SUSER_SNAME()** 或 **HOST_NAME()**。 依預設， **HOST_NAME()** 會傳回執行合併代理程式之電腦的名稱，但是您可以在新增訂閱精靈中覆寫這個值。 如需參數化篩選與覆寫 **HOST_NAME()** 的詳細資訊，請參閱＜ [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)＞。  
  
 **[訂閱類型]** 和 **[優先權]**  
 顯示訂閱是客訂閱或主訂閱 (建立了訂閱之後就無法再變更)。 主訂閱可以將資料重新發行至其他訂閱者，並且可以指派衝突解決的優先權。  
  
 如果您在新增訂閱精靈中選取伺服器的訂閱類型，就會為訂閱者指定在衝突解決過程中使用的優先權。  
  
 **以互動方式解決衝突**  
 決定在合併同步處理過程中，是否使用互動解析程式使用者介面來解決衝突。 這需要 **[使用 Windows Synchronization Manager]** 的值為 **[啟用]**。 如需詳細資訊，請參閱＜ [Interactive Conflict Resolution](merge/advanced-merge-replication-conflict-interactive-resolution.md)＞。  
  
## <a name="see-also"></a>另請參閱  
 [檢視及修改提取訂閱屬性](view-and-modify-pull-subscription-properties.md)   
 [檢視及修改發送訂閱屬性](view-and-modify-push-subscription-properties.md)   
 [訂閱發行集](subscribe-to-publications.md)  
  
  
