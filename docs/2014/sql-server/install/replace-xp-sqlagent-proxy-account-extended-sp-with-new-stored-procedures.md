---
title: 取代 xp_sqlagent_proxy_account 擴充預存程序，新的預存程序的使用方式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- xp_sqlagent_proxy_account
ms.assetid: 0e3cc931-6237-41dd-bf0d-0c03f4d8fff2
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4cd609cca3f8197986799a7c9630d35eeaa57d41
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159809"
---
# <a name="replace-usage-of-the-xpsqlagentproxyaccount-extended-stored-procedure-with-new-stored-procedures"></a>使用新的預存程序取代 xp_sqlagent_proxy_account 擴充預存程序的使用方式
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 支援多個 Proxy。 您可以使用一組新的預存程序定義這些 Proxy。 如需有關新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 預存程序的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的下列主題：  
  
-   ＜sp_add_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
-   ＜sp_delete_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
-   ＜sp_enum_login_for_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
-   ＜sp_enum_proxy_for_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
-   ＜sp_enum_sqlagent_subsystems ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
-   ＜sp_grant_proxy_to_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
-   ＜sp_grant_login_to_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
-   ＜sp_help_proxy" ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
-   ＜sp_revoke_login_from_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
-   ＜sp_revoke_proxy_from_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
-   ＜sp_update_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞  
  
> [!NOTE]  
>  在升級到之後[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]，使用的任何陳述式**xp_sqlagent_proxy_account**擴充預存程序將無法運作。 使用**sp_xp_cmdshell_proxy_account**而不是**xp_sqlagent_proxy_account**若要設定的 proxy **xp_cmdshell**。  
  
## <a name="component"></a>元件  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Agent 升級問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
