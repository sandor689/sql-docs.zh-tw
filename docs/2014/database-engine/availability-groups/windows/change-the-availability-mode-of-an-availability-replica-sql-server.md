---
title: 變更可用性複本的可用性模式 (SQL Server) (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], availability modes
ms.assetid: c4da8f25-fb1b-45a4-8bf2-195df6df634c
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9d9a742003107a2416e55f7c4f3a473c430e04eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310418"
---
# <a name="change-the-availability-mode-of-an-availability-replica-sql-server"></a>變更可用性複本的可用性模式 (SQL Server)
  本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 PowerShell，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中變更 AlwaysOn 可用性群組內可用性複本的可用性模式。 可用性模式是指控制複本以非同步方式或同步方式認可的複本屬性。 「非同步認可模式」會犧牲高可用性來達到最大效能，並且只支援強制手動容錯移轉 (可能遺失資料)，這通常稱為「強制容錯移轉」。 這種「同步認可模式」強調的是高可用性而非效能，而且一旦同步處理次要複本之後，便支援手動容錯移轉以及選擇性的自動容錯移轉。  
  

  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Prerequisites"></a> 必要條件  
  
-   您必須連接到裝載主要複本的伺服器執行個體。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 **若要變更可用性群組的可用性模式**  
  
1.  在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。  
  
2.  依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。  
  
3.  按一下要變更複本的可用性群組。  
  
4.  以滑鼠右鍵按一下複本，然後按一下 [屬性]。  
  
5.  在 **[可用性複本屬性]** 對話方塊中，使用 **[可用性模式]** 下拉式清單來變更此複本的可用性模式。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **若要變更可用性群組的可用性模式**  
  
1.  連接到裝載主要複本的伺服器執行個體。  
  
2.  使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：  
  
     ALTER AVAILABILITY GROUP *群組名稱* MODIFY REPLICA ON '*伺服器名稱*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     } )  
  
     其中 *群組名稱* 是可用性群組的名稱，而 *伺服器名稱* 是裝載要修改之複本的伺服器執行個體名稱。  
  
    > [!NOTE]  
    >  只有當您同時指定 AVAILABILITY_MODE = SYNCHRONOUS_COMMIT 時，才支援 FAILOVER_MODE = AUTOMATIC。  
  
     下列範例 (在 `AccountsAG` 可用性群組的主要複本上輸入) 會針對 `INSTANCE09` 伺服器執行個體上裝載的複本，將可用性和容錯移轉模式分別變更為同步認可和自動容錯移轉。  
  
    ```  
  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="PowerShellProcedure"></a> 使用 PowerShell  
 **若要變更可用性群組的可用性模式**  
  
1.  變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。  
  
2.  使用`Set-SqlAvailabilityReplica`cmdlet 搭配`AvailabilityMode`參數，並選擇性地`FailoverMode`參數。  
  
     例如，下列命令會將可用性群組 `MyReplica` 中的複本 `MyAg` 修改成使用同步認可的可用性模式並且支援自動容錯移轉。  
  
    ```  
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  若要檢視 cmdlet 的語法，請使用`Get-Help`指令程式在[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]PowerShell 環境。 如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。  
  
 **若要設定和使用 SQL Server PowerShell 提供者**  
  
-   [SQL Server PowerShell 提供者](../../../powershell/sql-server-powershell-provider.md)  
  
## <a name="see-also"></a>另請參閱  
 [AlwaysOn 可用性群組概觀&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [可用性模式 （AlwaysOn 可用性群組）](availability-modes-always-on-availability-groups.md)   
 [容錯移轉及容錯移轉模式&#40;AlwaysOn 可用性群組&#41;](failover-and-failover-modes-always-on-availability-groups.md)  
  
  
