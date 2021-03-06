---
title: 將次要資料庫聯結至可用性群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
caps.latest.revision: 37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 21218bdd04922de0da35511c0d93f4770d5d6b30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269494"
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a>將次要資料庫聯結至可用性群組 (SQL Server)
  本主題說明如何將次要資料庫聯結至 AlwaysOn 可用性群組中，使用[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]， [!INCLUDE[tsql](../../../includes/tsql-md.md)]，或在 PowerShell [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。 當您準備次要複本的次要資料庫之後，您必須盡快將此資料庫聯結至可用性群組。 這會從對應的主要資料庫開始將資料移動到次要資料庫。  
  
-   **開始之前：**  
  
     [必要條件](#Prerequisites)  
  
     [Security](#Security)  
  
-   **若要使用下列項目來準備次要資料庫：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
> [!NOTE]  
>  次要資料庫加入群組之後，會發生什麼情況的相關資訊，請參閱[AlwaysOn 可用性群組概觀&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)。  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Prerequisites"></a> 必要條件  
  
-   您必須連接到裝載次要複本的伺服器執行個體。  
  
-   次要複本必須已經加入可用性群組。 如需詳細資訊，請參閱 [將次要複本聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。  
  
-   最近必須已經準備次要資料庫。 如需詳細資訊，請參閱 [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 **若要將次要資料庫聯結至可用性群組**  
  
1.  在 [物件總管] 中，連接到裝載次要複本的伺服器執行個體，然後展開伺服器樹狀目錄。  
  
2.  依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。  
  
3.  展開您要變更的可用性群組，然後擴展 **[可用性資料庫]** 節點。  
  
4.  以滑鼠右鍵按一下資料庫，然後按一下 [加入可用性群組]。  
  
5.  這會開啟 **[將資料庫加入至可用性群組]** 對話方塊。 請確認顯示在標題列上的可用性群組名稱，以及顯示在方格中的資料庫名稱，然後按一下 **[確定]** 或按一下 **[取消]**。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **若要將次要資料庫聯結至可用性群組**  
  
1.  連接到裝載次要複本的伺服器執行個體。  
  
2.  使用 [ALTER DATABASE 陳述式的 SET HADR 子句](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) ，如下所示：  
  
     ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*  
  
     *database_name* 是要聯結的資料庫名稱，而 *group_name* 是可用性群組的名稱。  
  
     下列範例會將次要資料庫 `Db1` 聯結至 `MyAG` 可用性群組的本機次要複本。  
  
    ```  
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  若要查看內容中使用的這個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，請參閱 [建立可用性群組和 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)。  
  
##  <a name="PowerShellProcedure"></a> 使用 PowerShell  
 **若要將次要資料庫聯結至可用性群組**  
  
1.  將目錄變更 (`cd`) 裝載次要複本的伺服器執行個體。  
  
2.  使用`Add-SqlAvailabilityDatabase`cmdlet 來將一或多個次要資料庫聯結至可用性群組。  
  
     例如，下列命令會將次要資料庫 `Db1`聯結至裝載次要複本之其中一個伺服器執行個體上的可用性群組 `MyAG` 。  
  
    ```  
    Add-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG `   
    -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  若要檢視 cmdlet 的語法，請使用`Get-Help`指令程式在[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]PowerShell 環境。 如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。  
  
 **若要設定和使用 SQL Server PowerShell 提供者**  
  
-   [SQL Server PowerShell 提供者](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> 相關工作  
  
-   [將次要複本聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>另請參閱  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)   
 [AlwaysOn 可用性群組概觀&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [疑難排解 AlwaysOn 可用性群組組態&#40;SQL Server&#41;刪除](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
