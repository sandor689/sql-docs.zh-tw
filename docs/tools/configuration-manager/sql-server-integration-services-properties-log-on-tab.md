---
title: "SQL Server Integration Services 屬性 （登入 索引標籤） |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0eb1b87-6bb0-475e-8492-0fd3c3f910ea
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b19478c1c8df812c850156a8d2f72515e624b3b4
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-integration-services-properties-log-on-tab"></a>SQL Server Integration Services 屬性 (登入索引標籤)
  您可以使用 **[屬性]** 對話方塊的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **[登入]** 索引標籤，指定要供 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務使用的帳戶，以及啟動和停止該服務。  
  
## <a name="options"></a>選項。  
 **本機系統帳戶**  
 指定不需要密碼的本機系統帳戶。 但是，根據授與帳戶的權限，本機系統帳戶可能會限制服務與其他伺服器互動。  
  
 **這個帳戶**  
 指定使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證的本機或網域使用者帳戶。 [!INCLUDE[msCoName](../../includes/msconame-md.md)]建議您使用網域使用者帳戶具有最少權限的服務。 如需有關選取帳戶的資訊，請搜尋《線上叢書》的＜設定 Windows 服務帳戶＞主題。  
  
 **帳戶名稱**  
 指定本機或網域使用者帳戶名稱。  
  
 **密碼**  
 輸入帳戶的密碼。  
  
 **確認密碼**  
 再次輸入帳戶的密碼。  
  
 **啟動**  
 啟動服務。  
  
 **停止**  
 停止服務。  
  
 **暫停**  
 暫停服務。  
  
 **繼續**  
 繼續已暫停的服務。  
  
  