---
title: Get-powerpivotserviceapplication 指令程式 |Microsoft 文件
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a5ccd05b8c5e947972218a22c0abbc358731ee5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027868"
---
# <a name="get-powerpivotserviceapplication-cmdlet"></a>Get-PowerPivotServiceApplication 指令程式
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  傳回一個或多個 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式。  

>[!NOTE] 
>這份文件可能包含過時的資訊和範例。 使用 Get-help cmdlet 取得最新。
  
 **適用於** ：SharePoint 2010 和 SharePoint 2013。  
  
## <a name="syntax"></a>語法  
  
```  
Get-PowerPivotServiceApplication [[-Identity] <SPGeminiServiceApplicationPipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Get-PowerPivotServiceApplication 指令程式會傳回 Identity 參數所指定的服務應用程式。 如果未指定任何參數，Cmdlet 會傳回伺服器陣列中的所有 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式。 每個應用程式都由其顯示名稱、應用程式類型和 GUID 所識別。 若要檢視 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式的其他屬性，請將 format-list 選項加入 Cmdlet。  
  
## <a name="parameters"></a>參數  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>識別\<SPGeminiServiceApplicationPipeBind >  
 指定要取得的服務應用程式。 此值必須是可在伺服器陣列中唯一識別物件的有效 GUID。  
  
|||  
|-|-|  
|必要項？|false|  
|位置？|0|  
|預設值||  
|接受管線輸入？|true|  
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
C:\PS>Get-PowerPivotServiceApplication  
```  
  
 這個範例會傳回伺服器陣列中的一個或多個服務應用程式。  
  
## <a name="example-2"></a>範例 2  
  
```  
C:\PS>Get-PowerPivotServiceApplication | format-list  
```  
  
 這個範例會傳回 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 服務應用程式的所有屬性。  
  
## <a name="example-3"></a>範例 3  
  
```  
C:\PS>get-PowerPivotServiceApplication -Identity 1234567-890a-bcde-fghijklm  
```  
  
 這個範例會傳回單一服務應用程式，顯示應用程式的顯示名稱、應用程式類型和 GUID。 太長的顯示名稱會被截斷。 使用 format-list 選項可以檢視完整名稱。  
  
  
