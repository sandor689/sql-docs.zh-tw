---
title: 累加式更新對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22d7038fa3d8f07c5b32e35c5cb39e0d8db95766
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284164"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a>累加式更新對話方塊 (Analysis Services - 多維度資料)
  使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [累加式更新] 對話方塊，即可定義累加更新量值群組與資料分割時使用的設定。 在 [處理] 對話方塊裡的 [物件清單] 方格中，按一下 [設定值] 資料行中的 [設定]，即可顯示 [累加式更新] 對話方塊。  
  
## <a name="options"></a>選項。  
  
|詞彙|定義|  
|----------|----------------|  
|**量值群組**|選取要進行累加式更新的量值群組。<br /><br /> 注意：唯有累加地更新 Cube 時，才會啟用此選項。 如果您正在累加地更新量值群組或資料分割，則此選項會停用。|  
|**資料分割**|選取要更新的資料分割。<br /><br /> 注意：唯有累加地更新 Cube 時，才會啟用此選項。 如果您正在累加地更新量值群組或資料分割，則此選項會停用。|  
|**Table**|按一下即可更新來自資料表的物件。|  
|**資料來源或檢視表**|選取來源資料表所在的資料來源或資料來源檢視。<br /><br /> 注意：只有選取 [資料表] 時，才會啟用此選項。|  
|**資料表結構描述和名稱**|選取用來擷取資料的來源資料表，以累加地更新 Cube、量值群組，或資料分割。<br /><br /> 注意：只有選取 [資料表] 時，才會啟用此選項。|  
|**[資料集屬性]**|按一下即可更新來自查詢的物件。|  
|**資料來源**|選取要查詢之資料表所在的資料來源。<br /><br /> 注意：只有選取 [查詢] 時，才會啟用此選項。|  
|**查詢的文字**|輸入用來擷取資料的查詢文字，以累加地更新 Cube、量值群組，或資料分割。<br /><br /> 注意：只有選取 [查詢] 時，才會啟用此選項。|  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services Designers and Dialog Boxes&#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [處理序 對話方塊&#40;Analysis Services-多維度資料&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
