---
title: "安裝 SQL Server 移轉小幫手存取 (AccessToSQL) |Microsoft 文件"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- installing SSMA
- instructions, installation
- instructions, upgrade
- licensing SSMA
- prerequisites for installing SSMA
- procedure, installation
- procedure, licensing
- procedure, upgrading
- removing SSMA
- Setup
- uninstalling SSMA
- upgrading SSMA
ms.assetid: dd50eebd-75df-4e0d-8c4d-88b511aae4c7
caps.latest.revision: 31
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2915318b5bbe85ad21a5e5095a7322013dfa7b44
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>安裝 SQL Server 移轉小幫手存取 (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移轉小幫手 (SSMA) 的存取使用 Windows Installer 為基礎的精靈來安裝。 本主題提供資訊的安裝必要條件，SSMA，最新版本的連結和安裝、 授權、 解除安裝與升級 SSMA 的指示。  
  
## <a name="prerequisites"></a>필수 구성 요소  
SSMA 安裝之前，請確定您的系統符合下列需求：  
  
-   Windows 7 或更新版本，或 Windows Server 2008 或更新版本。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3.1 或更新版本。  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework 4.0 版或更新版本。 .NET Framework 4.0 版位於[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]產品光碟片，以及從[Microsoft.NET Framework 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=48882)網站。  
  
-   存取和裝載目標執行個體的電腦上有足夠的權限[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure 資料庫，其中您將會資料庫物件和資料移轉。  
  
-   DAO 12.0 或 14.0 的提供者版本。 您可以從 Microsoft Office 2010/2007年產品安裝 DAO 提供者，或從 Microsoft 網站下載。  
  
-   SQL Server Native Access Client (SNAC) 版本 10.5 和更新版本移轉至 SQL Azure。 您可以取得最新版的 SNAC 從[Microsoft® SQL Server® 2008 R2 功能套件](http://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 GB RAM，建議使用。  
  
## <a name="installing-ssma"></a>安裝 SSMA  
SSMA 是 Web 下載項目。 若要下載最新版本，請參閱[SQL Server 移轉小幫手的下載頁面](http://aka.ms/ssmaforaccess)。  
  
下載最新版本之後，您必須先擷取中的安裝檔案，才能安裝 SSMA。  
  
**若要安裝的 SSMA**  
  
1.  按兩下 SSMA for Access  *n* 。Install.exe 其中 *n* 是組建編號。  
  
2.  在 歡迎使用 頁面上，按一下 **下一步**。  
  
    如果您沒有安裝必要元件，會出現訊息，指出您必須先安裝必要的元件。 請確定已安裝所有先決條件，，然後再次執行安裝程式。  
  
3.  閱讀使用者授權合約。 如果您同意，請選取**我接受授權合約中的條款**，然後按一下 **下一步**。  
  
4.  在 選擇安裝類型 頁面上，按一下 **一般**。  
  
5.  按一下 **[安裝]**。  
  
> [!IMPORTANT]  
> 1.  請安裝新版本之前，解除安裝所有舊版的 SSMA for Access。  
  
預設安裝位置是 C:\Program Files\Microsoft SQL Server 移轉小幫手進行存取。  
  
## <a name="uninstalling-ssma-for-access"></a>解除安裝的 SSMA for Access  
使用 [解除安裝 SSMA**新增或移除程式**控制台] 中。 請注意，解除安裝程式不會刪除 SSMA 專案檔案，或記錄檔。  
  
**若要解除安裝 SSMA**  
  
1.  按一下**啟動**，按一下 **控制台**，然後按一下 **新增或移除程式**。  
  
2.  選取**Microsoft SQL Server 移轉小幫手存取**，然後按一下 **移除**。  
  
## <a name="upgrading-to-a-later-version"></a>升級至更新版本  
如果您想要升級至更新版本的 SSMA for Access，您必須先解除安裝 SSMA for Access，然後再安裝較新版本。 依照稍早在本主題適用於解除安裝與安裝中的指示。  
  
如果您從較早版本的 SSMA for Access 中開啟專案，會要求 SSMA，如果您想要將專案轉換成較新版本。 您必須按一下**是**使用較新版本的 SSMA 專案。  
  
## <a name="see-also"></a>另請參閱  
[準備移轉的 Access 資料庫](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
[將 Access 資料庫移轉至 SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[連結到 SQL Server 存取應用程式](http://msdn.microsoft.com/en-us/82374ad2-7737-4164-a489-13261ba393d4)  
  
