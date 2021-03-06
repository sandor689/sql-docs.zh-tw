---
title: New-powerpivotserviceapplication 指令程式 |Microsoft 文件
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5be9914dfb9361af2067cbef469f2ef6737b4fb7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036481"
---
# <a name="new-powerpivotserviceapplication-cmdlet"></a>New-PowerPivotServiceApplication 指令程式
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  建立新的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式。  

>[!NOTE] 
>這份文件可能包含過時的資訊和範例。 使用 Get-help cmdlet 取得最新。
  
 **適用於** ：SharePoint 2010 和 SharePoint 2013。  
  
## <a name="syntax"></a>語法  
  
```  
New-PowerPivotServiceApplication [-ServiceApplicationName] <string> [-DatabaseServerName] <string> [-DatabaseName] <string> [-AddToDefaultProxyGroup <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 New-PowerPivotServiceApplication Cmdlet 會在伺服器陣列中建立新的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式。 您必須至少定義一個服務應用程式，而且它必須是預設 Proxy 服務群組的成員。 或者，如果您需要更改屬性或組態設定，則可以建立其他服務應用程式。 必須將自訂服務連接群組的成員資格指派給其他服務應用程式。 只有一個 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式可以是預設 Proxy 群組的成員。  
  
 新的服務應用程式是使用預設組態建立的。 若要自訂組態屬性，請使用 Set-PowerPivotServiceApplication 指令程式。  
  
## <a name="parameters"></a>參數  
  
### <a name="-serviceapplicationname-string"></a>-ServiceApplicationName \<string>  
 設定服務應用程式的顯示名稱。  
  
|||  
|-|-|  
|必要項？|true|  
|位置？|0|  
|預設值||  
|接受管線輸入？|false|  
|接受萬用字元？|false|  
  
### <a name="-databaseservername-string"></a>-DatabaseServerName \<string>  
 指定裝載應用程式資料庫的 SQL Server 關聯式 Database Engine 執行個體。 根據預設，您可以使用伺服器陣列的資料庫伺服器，也可以選擇已建立資料庫權限的另一部資料庫伺服器。  
  
|||  
|-|-|  
|必要項？|true|  
|位置？|1|  
|預設值||  
|接受管線輸入？|false|  
|接受萬用字元？|false|  
  
### <a name="-databasename-string"></a>-DatabaseName\<字串 >  
 指定儲存應用程式資料之 SQL Server 關聯式資料庫的名稱。 請務必指定對應於應用程式的名稱，以便更輕鬆地識別其用途。 您可以建立新的資料庫，或針對所建立的新應用程式，指定現有的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式資料庫。  
  
|||  
|-|-|  
|必要項？|true|  
|位置？|2|  
|預設值||  
|接受管線輸入？|false|  
|接受萬用字元？|false|  
  
### <a name="-addtodefaultproxygroup-switch"></a>-AddToDefaultProxyGroup \<switch>  
 在預設服務連接群組中，建立 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務連接。 Web 應用程式和服務應用程式之間的關聯是由此群組的成員資格所決定。 所有訂閱預設服務連接群組的 Web 應用程式，都會使用加入至此群組的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式。 雖然在伺服器陣列中可以有多個 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式，但只有一個服務應用程式可以是預設服務連接群組的成員。  
  
 如果已經有一個 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式是預設 Proxy 群組的成員，您必須為所建立的新應用程式設定 AddToDefautlProxyGroup:$false。 新服務應用程式需要加入至自訂服務連接群組。  內建 SharePoint 指令程式可用於此目的。  Get-SPServiceApplicationProxyGroup 會傳回伺服器陣列中定義的服務連接群組清單。  
  
|||  
|-|-|  
|必要項？|false|  
|位置？|具名|  
|預設值||  
|接受管線輸入？|false|  
|接受萬用字元？|false|  
  
### <a name="commonparameters"></a>\<一般參數 >  
 這個指令程式支援一般參數：Verbose、Debug、ErrorAction、ErrorVariable、WarningAction、WarningVariable、OutBuffer 和 OutVariable。 如需詳細資訊，請參閱 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)。  
  
## <a name="inputs-and-outputs"></a>輸入和輸出  
 輸入類型是可透過管道傳送至指令程式的物件類型。 傳回類型是指令程式所傳回的物件類型。  
  
|||  
|-|-|  
|輸入|無。|  
|輸出|無。|  
  
## <a name="example-1"></a>範例 1  
  
```  
C:\PS>New-PowerPivotServiceApplication -ServiceApplicationName "PowerPivot Service Application" -DatabaseServerName "AdvWorks-SRV01\PowerPivot" -DatabaseName "PowerPivotServiceApp1" -AddtoDefaultProxyGroup:$true  
```  
  
 這個範例會建立新的服務應用程式。 服務應用程式資料庫是在安裝為 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 具名執行個體的 AdvWorks-SRV01 資料庫伺服器上所建立，這是許多 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 安裝所通用的組態。 您必須有 SQL Server 執行個體的 dbcreator 權限，才能建立資料庫。 您必須是 SharePoint 組態資料庫的 db_owner。 因為這是伺服器陣列中的第一個 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式，所以它必須是預設 Proxy 群組的成員。  
  
  
