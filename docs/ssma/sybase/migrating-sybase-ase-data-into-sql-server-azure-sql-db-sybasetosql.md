---
title: 將 Sybase ASE 資料移轉至 SQL Server-Azure SQL DB |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Migrating data,Client Side Data Migration
- Migrating data,Server Side Data Migration
ms.assetid: 54a39f5e-9250-4387-a3ae-eae47c799811
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e39d74143e21d6b75a5a35a1f8dbde4f62f285f4
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395862"
---
# <a name="migrating-sybase-ase-data-into-sql-server---azure-sql-db--sybasetosql"></a>Sybase ASE 資料移轉到 SQL Server-Azure SQL DB (SybaseToSQL)
已成功載入到 Sybase Adaptive Server Enterprise (ASE) 資料庫物件之後[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 Azure SQL DB 中，您可以從 ASE 移轉資料[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 Azure SQL DB。  
  
> [!IMPORTANT]  
> 如果伺服器端資料移轉引擎所使用的引擎，然後移轉資料，您必須先安裝 SSMA for Sybase ASE 延伸模組組件和 Sybase ASE 上的提供者執行 SSMA 的電腦。 也必須執行的 SQL Server Agent 服務。 如需如何安裝此延伸模組組件的詳細資訊，請參閱[SQL Server (SybaseToSQL) 上安裝 SSMA 元件](http://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
## <a name="setting-migration-options"></a>移轉選項的設定  
在移轉之前資料載入[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 Azure SQL DB 中，檢閱中的專案移轉選項**專案設定** 對話方塊。  
  
-   使用此對話方塊中，您可以設定選項，例如移轉批次大小、 資料表鎖定、 條件約束檢查，null 值的處理和身分識別值的處理。 如需將專案移轉設定的詳細資訊，請參閱[專案設定 （移轉） (Sybase)](http://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924)。  
  
    如需詳細資訊**擴充資料移轉設定**，請參閱[資料移轉設定](data-migration-settings-sybasetosql.md)  
  
-   **移轉引擎**中**專案設定**對話方塊的 允許使用者執行上來使用兩種類型的資料移轉引擎，移轉程序。:  
  
    1.  用戶端端資料移轉引擎  
  
    2.  伺服器端資料移轉引擎  
  
**用戶端端資料移轉：**  
  
-   若要起始用戶端上的資料移轉，請選取選項**用戶端端資料移轉引擎**中**專案設定** 對話方塊。  
  
-   在 **專案設定**，則**用戶端端資料移轉引擎**選項預設設定。  
  
    > [!NOTE]  
    > 用戶端資料移轉引擎位於 SSMA 應用程式內，因此，不是取決於延伸模組組件。  
  
**伺服器端資料移轉：**  
  
-   伺服器端資料移轉期間，引擎會位於目標資料庫。 它可透過延伸模組套件進行安裝。 如需有關如何安裝此延伸模組組件的詳細資訊，請參閱[SQL Server (SybaseToSQL) 上安裝 SSMA 元件](http://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
-   若要起始移轉的伺服器端上，選取**伺服器端資料移轉引擎**選項**專案設定**對話方塊。  
  
> [!NOTE]  
> 當 Azure SQL DB 做為目標資料庫，只有**用戶端端資料移轉**允許和不支援伺服器端資料移轉。  
  
## <a name="migrating-data-to-sql-server-or-azure-sql-db"></a>將資料移轉至 SQL Server 或 Azure SQL DB  
移轉資料是從 ASE 資料表的資料列的資料進入交易中的 SQL Server 資料表的大量載入作業。 將專案設定中已載入至 SQL Server 或 Azure SQL DB 中，每一筆交易中的資料列數目。  
  
若要檢視移轉訊息，請確定 [輸出] 窗格為可見。 否則，請選取**輸出**從**檢視**功能表。  
  
**若要將資料移轉**  
  
1.  驗證下列項目：  
  
    -   執行 SSMA 的電腦上安裝的 ASE 提供者。  
  
    -   您已與目標資料庫 （SQL Server 或 Azure SQL DB） 來同步處理已轉換的物件。  
  
2.  在 Sybase 中繼資料總管 中，選取包含您想要移轉之資料的物件：  
  
    -   若要將所有結構描述的資料移轉，選取核取方塊旁**結構描述**。  
  
    -   若要將資料移轉，或省略個別資料表，第一次展開結構描述中，依序展開**資料表**，然後選取或清除資料表旁邊的核取方塊。  
  
3.  若要將資料移轉，兩種情況下發生：  
  
    **用戶端端資料移轉：**  
  
    執行**用戶端端資料移轉**，選取**用戶端端資料移轉引擎**選項**專案設定** 對話方塊。  
  
    **伺服器端資料移轉：**  
  
    -   然後再執行伺服器端資料移轉，請確定：  
  
        1.  SSMA for Sybase 延伸模組套件會安裝 SQL Server 執行個體上。  
  
        2.  SQL Server 執行個體上執行的 SQL Server Agent 服務  
  
    -   執行**伺服器端資料移轉**，選取**伺服器端資料移轉引擎**選項**專案設定** 對話方塊。  
  
4.  以滑鼠右鍵按一下**結構描述**在 Sybase 中繼資料總管，然後按一下**移轉資料**。 您也可以將移轉資料的個別物件或類別目錄的物件： 物件或其父資料夾上按一下滑鼠右鍵，然後選取**移轉資料**選項。  
  
    > [!NOTE]  
    > 如果 SQL Server 執行個體上未安裝 SSMA for Sybase 延伸模組套件，而且**伺服器端資料移轉引擎**已選取，然後同時將資料移轉到目標資料庫，發生下列錯誤: ' SSMASQL Server 上找不到資料移轉的元件，無法進行伺服器端資料移轉。 請檢查是否已正確安裝延伸模組組件 '。 按一下 **取消**終止資料移轉。  
  
5.  在 [**連接到 Sybase ASE** ] 對話方塊中，輸入連線認證，然後再按一下**Connect**。 如需有關如何連接到 Sybase ASE 的詳細資訊，請參閱 <<c0> [ 連接到 Sybase &#40;SybaseToSQL&#41;</c0>](../../ssma/sybase/connect-to-sybase-sybasetosql.md)  
  
    如果目標資料庫是 SQL Server，然後輸入中的連接認證**連接到 SQL Server**  對話方塊中，然後按一下**Connect**。 如需有關如何連接到 SQL Server 的詳細資訊，請參閱[連接到 SQL Server(SybaseToSQL)](http://msdn.microsoft.com/dd368a1a-45b0-40e9-b4d3-5cdb48c26606)  
  
    如果目標資料庫是 Azure SQL DB，然後輸入中的連接認證**連線到 Azure SQL DB**  對話方塊中，然後按一下**Connect**。 如需有關如何連線到 Azure SQL DB 的詳細資訊，請參閱[連線到 Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
    訊息會出現在**輸出**窗格。 移轉完成時，**資料移轉報告**隨即出現。 如果未移轉任何資料，按一下包含錯誤，資料列，然後按一下**詳細資料**。 當您完成報表時，請按一下**關閉**。 如需有關資料移轉報告的詳細資訊，請參閱[（SSMA 常見） 的資料移轉報告](http://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> 做為目標資料庫使用 SQL Express 版本時，允許只能用戶端端資料移轉，並不支援伺服器端資料移轉。  
  
## <a name="see-also"></a>另請參閱  
[將 Sybase ASE 資料庫移轉至 SQL Server-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
