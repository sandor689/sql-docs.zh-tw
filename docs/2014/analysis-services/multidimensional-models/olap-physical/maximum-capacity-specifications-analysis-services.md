---
title: 最大容量規格 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], maximum number
- objects [Analysis Services], maximum size
ms.assetid: 49fe1673-b908-4c7a-88ff-415efd294d27
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04307fb9eb5525c9ce4d91af7eda44ea3783b3b7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200268"
---
# <a name="maximum-capacity-specifications-analysis-services"></a>最大容量規格 (Analysis Services)
  下表指定 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 元件中的不同伺服器部署模式下，所定義之各種物件的大小和數目上限。  
  
 本主題包含下列幾節：  
  
 [多維度和資料採礦 (DeploymentMode = 0)](#bkmk_OLAP)  
  
 [SharePoint (DeploymentMode = 1)](#bkmk_sharepoint)  
  
 [表格式 (DeploymentMode = 2)](#bkmk_vertipaq)  
  
##  <a name="bkmk_OLAP"></a> 多維度和資料採礦 (DeploymentMode = 0)  
 MOLAP 儲存模式，會同時儲存資料和中繼資料，對於檔案大小另有實體限制。 字串存放檔案的預設大小上限為 4 GB。 如果您需要更大的字串存放檔案，可以指定不同的字串儲存體架構。 如需詳細資訊，請參閱 <<c0> [ 設定的維度和資料分割的字串儲存體](../configure-string-storage-for-dimensions-and-partitions.md)。  
  
|Object|大小/數目上限|  
|------------|----------------------------|  
|執行個體中的資料庫|2^31-1 = 2,147,483,647|  
|資料庫中的維度|2^31-1 = 2,147,483,647|  
|維度中的屬性|2^31-1 = 2,147,483,647|  
|維度屬性中的成員|2^31-1 = 2,147,483,647|  
|維度中的使用者自訂階層|2^31-1 = 2,147,483,647|  
|使用者自訂階層中的層級|2^31-1 = 2,147,483,647|  
|資料庫中的 Cube|2^31-1 = 2,147,483,647|  
|Cube 中的量值群組|2^31-1 = 2,147,483,647|  
|量值群組中的量值|2^31-1 = 2,147,483,647|  
|Cube 中的計算|2^31-1 = 2,147,483,647|  
|Cube 中的 KPI|2^31-1 = 2,147,483,647|  
|Cube 中的動作|2^31-1 = 2,147,483,647|  
|Cube 中的資料分割|2^31-1 = 2,147,483,647|  
|Cube 中的翻譯|2^31-1 = 2,147,483,647|  
|資料分割中的彙總|2^31-1 = 2,147,483,647|  
|查詢傳回的資料格|2^31-1 = 2,147,483,647|  
|來源查詢的記錄大小|64K|  
|物件名稱的長度|100 個字元|  
|資料採礦模型屬性資料行中相異狀態數目的上限|2^31-1 = 2,147,483,647|  
|考量的屬性數目上限 (特徵選取)|2^31-1 = 2,147,483,647|  
  
 如需有關物件命名方針的詳細資訊，請參閱 < [ASSL 物件和物件特性](../scripting-language-assl/assl-objects-and-object-characteristics.md)。  
  
 如需有關線上分析處理 (OLAP) 和資料採礦的資料來源限制的詳細資訊，請參閱 <<c0> [ 支援的資料來源&#40;SSAS 多維度&#41;](../supported-data-sources-ssas-multidimensional.md)，[支援資料來源&#40;SSAS 多維度&#41;](../supported-data-sources-ssas-multidimensional.md)，並[ASSL 物件和物件特性](../scripting-language-assl/assl-objects-and-object-characteristics.md)。</c0>  
  
##  <a name="bkmk_sharepoint"></a> SharePoint (DeploymentMode = 1)  
  
|Object|大小/數目上限|  
|------------|----------------------------|  
|執行個體中的資料庫|2^31-1 = 2,147,483,647|  
|資料庫中的資料表|2^31-1 = 2,147,483,647|  
|資料表中的資料行|2 ^31-1 = 2,147,483,647**警告：** 資料表中的資料行總數取決於量值的總數和相同的資料表相關聯的導出資料行。 資料表的「資料行 + 量值 + 導出資料行」的最大數目為 2^31-1 = 2,147,483,647|  
|資料表中的資料列|無限制**警告：** 與單一資料行可能包含超過 1,999,999,997 的相異值的限制。|  
|資料表中的階層|2^31-1 = 2,147,483,647|  
|階層中的層級|2^31-1 = 2,147,483,647|  
|關聯性|2^31-1 = 2,147,483,647|  
|資料表中的索引鍵資料行|2^31-1 = 2,147,483,647|  
|資料表中的量值|2 ^31-1 = 2,147,483,647**警告：** 中資料表的量值的總數取決於資料行總數和相同的資料表相關聯的導出資料行。 資料表的「資料行 + 量值 + 導出資料行」的最大數目為 2^31-1 = 2,147,483,647|  
|資料表中的導出資料行|2 ^31-1 = 2,147,483,647**警告：** 資料表中的導出資料行總數取決於資料行總數和相同的資料表相關聯的量值。 資料表的「資料行 + 量值 + 導出資料行」的最大數目為 2^31-1 = 2,147,483,647|  
|查詢傳回的資料格|2^31-1 = 2,147,483,647|  
|來源查詢的記錄大小|64K|  
|物件名稱的長度|100 個字元|  
  
##  <a name="bkmk_vertipaq"></a> 表格式 (DeploymentMode = 2)  
  
|Object|大小/數目上限|  
|------------|----------------------------|  
|執行個體中的資料庫|2^31-1 = 2,147,483,647|  
|資料庫中的資料表|2^31-1 = 2,147,483,647|  
|資料表中的資料行|2 ^31-1 = 2,147,483,647**警告：** 資料表中的資料行總數取決於量值的總數和相同的資料表相關聯的導出資料行。 資料表的「資料行 + 量值 + 導出資料行」的最大數目為 2^31-1 = 2,147,483,647|  
|資料表中的資料列|無限制**警告：** 限制資料表中的單一資料行可以有超過 1,999,999,997 的相異值。|  
|資料表中的階層|2^31-1 = 2,147,483,647|  
|階層中的層級|2^31-1 = 2,147,483,647|  
|關聯性|2^31-1 = 2,147,483,647|  
|資料表中的索引鍵資料行|2^31-1 = 2,147,483,647|  
|資料表中的量值|2 ^31-1 = 2,147,483,647**警告：** 中資料表的量值的總數取決於資料行總數和相同的資料表相關聯的導出資料行。 資料表的「資料行 + 量值 + 導出資料行」的最大數目為 2^31-1 = 2,147,483,647|  
|資料表中的導出資料行|2 ^31-1 = 2,147,483,647**警告：** 資料表中的導出資料行總數取決於資料行總數和相同的資料表相關聯的量值。 資料表的「資料行 + 量值 + 導出資料行」的最大數目為 2^31-1 = 2,147,483,647|  
|查詢傳回的資料格|2^31-1 = 2,147,483,647|  
|來源查詢的記錄大小|64K|  
|物件名稱的長度|100 個字元|  
  
## <a name="see-also"></a>另請參閱  
 [判斷 Analysis Services 執行個體的伺服器模式](../../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [一般屬性](../../server-properties/general-properties.md)  
  
  
