---
title: SqlServiceType 屬性 （SqlService 類別） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SqlServiceType Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServiceType property
ms.assetid: dbff2968-3011-41d6-a141-52d814af0213
caps.latest.revision: 43
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0aca7106f62cc10dd1ec1288256f2e1b8351d8dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157899"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>SqlServiceType 屬性 (SqlService 類別)
  取得受管理之服務的類型。  
  
## <a name="syntax"></a>語法  
  
```  
  
object  
.SqlServiceType [= value]  
```  
  
## <a name="parts"></a>組件  
 *object*  
 表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務類型的 uint32 值。  
  
## <a name="remarks"></a>備註  
 傳回值可以是下列其中一個：  
  
|類型|定義|  
|----------|----------------|  
|*1*|MSSQLSERVER 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務。|  
|*2*|SQLSERVERAGENT 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 服務。|  
|*3*|MSFTESQL 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 全文檢索搜尋引擎服務。|  
|*4*|MsDtsServer 是 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 服務。|  
|*5*|MSSQLServerOLAPService 是 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 服務。|  
|*6*|ReportServer 是 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服務。|  
|*7*|SQLBrowser 是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser 服務。|  
  
## <a name="see-also"></a>另請參閱  
 [啟動及停止服務](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
