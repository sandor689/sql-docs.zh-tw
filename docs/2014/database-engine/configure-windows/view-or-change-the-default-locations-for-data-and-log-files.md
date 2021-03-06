---
title: 檢視或變更預設位置，資料和記錄檔 (SQL Server Management Studio) |Microsoft Docs
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
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b62c6264686efe2b117ca755fc291c784308fe9d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320778"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files-sql-server-management-studio"></a>檢視或變更資料及記錄檔的預設位置 (SQL Server Management Studio)
  此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中檢視及變更新資料和記錄檔的預設位置。 預設路徑是從登錄取得。 在變更位置之後，如果未指定不同的位置， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中建立的所有新資料庫都會使用該位置。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [建議](#Recommendations)  
  
-   **若要檢視或變更資料和記錄檔的預設位置使用：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
-   **待處理**  [變更預設位置之後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Recommendations"></a> 建議  
 保護資料檔和記錄檔的最佳作法是確定它們受到存取控制清單 (ACL) 所保護。 ACL 應該設在建立這些檔案所在的根目錄下。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-default-locations-for-database-files"></a>若要檢視或變更資料庫檔案的預設位置  
  
1.  在物件總管中，以滑鼠右鍵按一下伺服器，然後按一下 [屬性]。  
  
2.  在左面板中，按一下 **[資料庫設定]** 頁面。  
  
3.  在 **[資料庫預設位置]** 中，您可以檢視新資料檔和新記錄檔的目前預設位置。 若要變更預設位置，在 **[資料]** 或 **[記錄]** 欄位中輸入新的預設路徑名稱，或按一下 [瀏覽] 按鈕來尋找並選取路徑名稱。  
  
##  <a name="FollowUp"></a> 待處理： 變更預設位置之後  
 您必須停止然後啟動 SQL Server 服務以完成變更。  
  
## <a name="see-also"></a>另請參閱  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [建立資料庫](../../relational-databases/databases/create-a-database.md)  
  
  
