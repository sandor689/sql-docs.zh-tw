---
title: 安全性概觀 (複寫) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- authorization [SQL Server replication]
- cryptography [SQL Server replication]
- encryption [SQL Server replication]
- security [SQL Server replication], about security
- authentication [SQL Server replication]
ms.assetid: 27828fe4-3b54-4c33-886e-08e8279e34b5
caps.latest.revision: 44
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 62567dbbb53db61780f002779abb825e19287578
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148259"
---
# <a name="security-overview-replication"></a>安全性概觀 (複寫)
  基本上，確保複寫環境的安全性也就是要了解您的驗證與授權選項，了解如何適當使用複寫篩選功能，並學習有助於確保各複寫環境安全性的特定方法。 複寫環境包括「散發者」、「發行者」、「訂閱者」和快照集資料夾。 本章描述複寫安全性，但複寫安全性是以 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安全性和 Windows 安全性為基礎； 因此，您應該了解這項基礎以及複寫安全性的特性。 如需安全性的詳細資訊，請參閱 [SQL Server 安裝的安全性考量](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md)。 如需 Oracle 發行之安全性考量的詳細資訊，請參閱＜ [Design Considerations and Limitations for Oracle Publishers](../non-sql/design-considerations-and-limitations-for-oracle-publishers.md)＞主題中的「複寫安全性模型」一節。  
  
## <a name="in-this-section"></a>本節內容  
 [威脅和弱點安全防護 &#40;複寫&#41;](threat-and-vulnerability-mitigation-replication.md)  
 討論複寫拓撲的可能威脅並描述減輕這些威脅的方式。  
  
 [識別和存取控制 &#40;複寫&#41;](identity-and-access-control-replication.md)  
 描述如何使用驗證、授權和篩選，以協助確保複寫拓撲的安全性。  
  
 [安全程式開發 &#40;複寫&#41;](secure-development-replication.md)  
 描述複寫安全性行為、複寫安全性的最佳做法以及複寫的最低權限。  
  
 [安全的部署 &#40;複寫&#41;](secure-deployment-replication.md)  
 描述確保複寫拓撲所有元件安全性的最佳方式。  
  
## <a name="see-also"></a>另請參閱  
 [安全性與保護 &#40;複寫&#41;](security-and-protection-replication.md)  
  
  
