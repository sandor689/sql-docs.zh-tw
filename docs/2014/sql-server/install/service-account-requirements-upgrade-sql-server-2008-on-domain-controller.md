---
title: 服務升級到 SQL Server 2008 網域控制站上的帳戶需求 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
caps.latest.revision: 16
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9cc2ec39bee7f9a64d75ccf4753220f69693155b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301658"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a>在網域控制站上升級至 SQL Server 2008 的服務帳戶需求
  Upgrade Advisor 偵測到的執行個體[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上執行的網路服務或本機服務帳戶[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]網域控制站。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 網域控制站上安裝 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務不能以本機服務帳戶或網路服務帳戶權限執行。  
  
## <a name="component"></a>元件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>更正動作  
 請確定所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶都指派給網域帳戶或本機系統帳戶。 如果無法在升級之前進行這項變更，系統將封鎖安裝程式。 但是，SQL 寫入器、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Active Directory Helper 服務等服務帳戶除外，因為這些服務都已硬式編碼至網路服務帳戶而且無法變更。  
  
## <a name="see-also"></a>另請參閱  
 [Database Engine 升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor&#91;新增&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
