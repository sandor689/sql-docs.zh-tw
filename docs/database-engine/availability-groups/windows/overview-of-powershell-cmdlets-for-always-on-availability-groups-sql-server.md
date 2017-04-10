---
title: "AlwaysOn 可用性群組的 PowerShell Cmdlet 概觀 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "可用性群組 [SQL Server], PowerShell Cmdlet"
  - "可用性群組 [SQL Server], 關於"
  - "PowerShell [SQL Server], Cmdlet"
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
caps.latest.revision: 36
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 36
---
# AlwaysOn 可用性群組的 PowerShell Cmdlet 概觀 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PowerShell 是以工作為基礎的命令列介面和指令碼語言，專為系統管理所設計。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 會在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中提供一組 PowerShell 指令程式，可讓您部署、管理和監視可用性群組、可用性複本以及可用性資料庫。  
  
> [!NOTE]  
>  PowerShell 指令程式可以透過順利起始動作來完成。 這並不表示預期的工作 (例如可用性群組的容錯移轉) 已經完成。 編寫一系列動作的指令碼時，您可能必須檢查動作的狀態，並且等候這些動作完成。  
  
 本主題將介紹下列各組工作的指令程式：  
  
-   [設定 AlwaysOn 可用性群組的伺服器執行個體](#ConfiguringServerInstance)  
  
-   [備份和還原資料庫與交易記錄](#BnRcmdlets)  
  
-   [建立和管理可用性群組](#DeployManageAGs)  
  
-   [建立和管理可用性群組接聽程式](#AGlisteners)  
  
-   [建立和管理可用性複本](#DeployManageARs)  
  
-   [加入和管理可用性資料庫](#DeployManageDbs)  
  
-   [監視可用性群組健全狀況](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  如需《[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 線上叢書》中描述如何使用指令程式來執行 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 工作的主題清單，請參閱 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) 的＜相關工作＞一節。  
  
##  <a name="ConfiguringServerInstance"></a> 設定 AlwaysOn 可用性群組的伺服器執行個體  
  
|指令程式|描述|支援的項目|  
|-------------|-----------------|------------------|  
|**Disable-SqlAlways On**|在伺服器執行個體上停用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 功能。|**Path**、 **InputObject**或 **Name** 參數所指定的伺服器執行個體。 (必須是支援 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 版本)。|  
|**Enable-SqlAlways On**|在支援 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 功能的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 執行個體上啟用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。 如需 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 支援的相關資訊，請參閱 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)。|支援 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的任何 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 版本。|  
|**New-SqlHadrEndPoint**|在伺服器執行個體上建立新的資料庫鏡像端點。 在主要與次要資料庫之間進行資料移動時需要這個端點。|任何 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|**Set-SqlHadrEndpoint**|變更現有資料庫鏡像端點的屬性，例如名稱、狀態或驗證屬性。|支援 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 且缺少資料庫鏡像端點的伺服器執行個體|  
  
##  <a name="BnRcmdlets"></a> 備份及還原資料庫和交易記錄  
  
|指令程式|描述|支援的項目|  
|-------------|-----------------|------------------|  
|**Backup-SqlDatabase**|建立資料或記錄備份。|任何線上資料庫 (若為 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]，則為裝載主要複本之伺服器執行個體的資料庫)|  
|**Restore-SqlDatabase**|還原備份。|任何 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體 (若為 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]，則為裝載次要複本的伺服器執行個體)<br /><br /> **\*\* 重要事項 \*\*** 準備次要資料庫時，您必須在每個 **Restore-SqlDatabase** 命令中使用 **-NoRecovery** 參數。|  
  
 如需使用這些 Cmdlet 來準備次要資料庫的相關資訊，請參閱[針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)。  
  
##  <a name="DeployManageAGs"></a> 建立和管理可用性群組  
  
|指令程式|描述|支援的項目|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityGroup**|建立新的可用性群組。|要裝載主要複本的伺服器執行個體|  
|**Remove-SqlAvailabilityGroup**|刪除可用性群組。|啟用 HADR 的伺服器執行個體|  
|**Set-SqlAvailabilityGroup**|設定可用性群組的屬性；讓可用性群組上線/離線。|裝載主要複本的伺服器執行個體|  
|**Switch-SqlAvailabilityGroup**|起始下列其中一種形式的容錯移轉：<br /><br /> 可用性群組的強制容錯移轉 (可能遺失資料)。<br /><br /> 可用性群組的手動容錯移轉。|裝載目標次要複本的伺服器執行個體|  
  
##  <a name="AGlisteners"></a> 建立和管理可用性群組接聽程式  
  
|指令程式|描述|支援的項目|  
|------------|-----------------|------------------|  
|**New-SqlAvailabilityGroupListener**|建立新的可用性群組接聽程式，並將其附加至現有的可用性群組。|裝載主要複本的伺服器執行個體|  
|**Set-SqlAvailabilityGroupListener**|修改現有可用性群組接聽程式上的通訊埠設定。|裝載主要複本的伺服器執行個體|  
|**Add-SqlAvailabilityGroupListenerStaticIp**|將靜態 IP 位址加入至現有的可用性群組接聽程式組態。 IP 位址可以是包含子網路的 IPv4 位址或 IPv6 位址。|裝載主要複本的伺服器執行個體|  
  
##  <a name="DeployManageARs"></a> 建立和管理可用性複本  
  
|指令程式|描述|支援的項目|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityReplica**|建立新的可用性複本。 您可以使用 **-AsTemplate** 參數，針對每個新的可用性複本建立記憶體內部可用性複本物件。|裝載主要複本的伺服器執行個體|  
|**Join-SqlAvailabilityGroup**|將次要複本聯結至可用性群組。|裝載次要複本的伺服器執行個體|  
|**Remove-SqlAvailabilityReplica**|刪除可用性複本。|裝載主要複本的伺服器執行個體|  
|**Set-SqlAvailabilityReplica**|設定可用性複本的屬性。|裝載主要複本的伺服器執行個體|  
  
##  <a name="DeployManageDbs"></a> 加入和管理可用性資料庫  
  
|指令程式|描述|支援的項目|  
|-------------|-----------------|------------------|  
|**Add-SqlAvailabilityDatabase**|在主要複本上，將資料庫加入至可用性群組。<br /><br /> 在次要複本上，將次要資料庫聯結至可用性群組。|裝載可用性複本的任何伺服器執行個體 (主要和次要複本的行為有所不同)|  
|**Remove-SqlAvailabilityDatabase**|在主要複本上，從可用性群組中移除資料庫。<br /><br /> 在次要複本上，從本機次要複本中移除本機次要資料庫。|裝載可用性複本的任何伺服器執行個體 (主要和次要複本的行為有所不同)|  
|**Resume-SqlAvailabilityDatabase**|繼續進行暫停之可用性資料庫的資料移動。|已暫停資料庫的伺服器執行個體。|  
|**Suspend-SqlAvailabilityDatabase**|暫停可用性資料庫的資料移動。|裝載可用性複本的任何伺服器執行個體。|  
  
##  <a name="MonitorTblshtAGs"></a> 監視可用性群組健全狀況  
 下列 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式可讓您監視可用性群組及其複本和資料庫的健全狀況。  
  
> [!IMPORTANT]  
>  您必須擁有 CONNECT、VIEW SERVER STATE 和 VIEW ANY DEFINITION 權限，才能執行這些指令程式。  
  
|指令程式|描述|支援的項目|  
|------------|-----------------|------------------|  
|**Test-SqlAvailabilityGroup**|透過評估 SQL Server 原則式管理 (PBM) 原則，評估可用性群組的健全狀況。|裝載可用性複本的任何伺服器執行個體。*|  
|**Test-SqlAvailabilityReplica**|透過評估 SQL Server 原則式管理 (PBM) 原則，評估可用性複本的健全狀況。|裝載可用性複本的任何伺服器執行個體。*|  
|**Test-SqlDatabaseReplicaState**|透過評估 SQL Server 原則式管理 (PBM) 原則，評估所有聯結可用性複本之可用性資料庫的健全狀況。|裝載可用性複本的任何伺服器執行個體。*|  
  
 *若要檢視可用性群組中所有可用性複本的相關資訊，請用於裝載主要複本的伺服器執行個體。  
  
 如需詳細資訊，請參閱[使用 AlwaysOn 原則檢視可用性群組的健全狀況 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)。  
  
## 另請參閱  
 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [取得 SQL Server PowerShell 說明](../../../relational-databases/scripting/get-help-sql-server-powershell.md)  
  
  