---
title: 一般檔案來源編輯器 （資料行頁面） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0d0007a98a02da095887aa0faedb12ba629f5e01
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171019"
---
# <a name="flat-file-source-editor-columns-page"></a>一般檔案來源編輯器 (資料行頁面)
  使用 [一般檔案來源編輯器] 對話方塊的 [資料行] 節點，將輸出資料行對應至每個外部 (來源) 資料行。  
  
> [!NOTE]  
>  `FileNameColumnName`一般檔案來源的屬性和`FastParse`其輸出資料行的屬性不適用於**一般檔案來源編輯器**，但可以透過設定**進階編輯器**. 如需這些屬性的詳細資訊，請參閱[一般檔案自訂屬性](data-flow/flat-file-custom-properties.md)的＜一般檔案來源＞一節。  
  
 若要深入了解一般檔案來源，請參閱＜ [Flat File Source](data-flow/flat-file-source.md)＞。  
  
## <a name="options"></a>選項。  
 **可用的外部資料行**  
 在資料來源中檢視可用的外部資料行清單。 您無法使用此資料表來加入或刪除資料行。  
  
 **[外部資料行]**  
 依工作讀取外部 (來源) 資料行的順序來檢視它們。 首先取消選取資料表中選取的資料行，然後依不同順序從清單中選取外部資料行，就可以變更此順序。  
  
 **輸出資料行**  
 為每個輸出資料行提供唯一的名稱。 預設值為選取的外部 (來源) 資料行的名稱；不過，您也可以選擇任何唯一的、描述性的名稱。 提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [一般檔案來源編輯器&#40;連線管理員頁面&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md)   
 [一般檔案來源編輯器&#40;錯誤輸出頁面&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [一般檔案連線管理員](connection-manager/file-connection-manager.md)  
  
  
