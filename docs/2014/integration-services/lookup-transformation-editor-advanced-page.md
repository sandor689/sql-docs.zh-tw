---
title: 查閱轉換編輯器 （進階頁面） |Microsoft Docs
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
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
caps.latest.revision: 41
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9b44973dda00e956d25c694c835e7dc1e683eab9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169194"
---
# <a name="lookup-transformation-editor-advanced-page"></a>查閱轉換編輯器 (進階頁面)
  使用 [查閱轉換編輯器] 對話方塊的 [進階] 頁面，即可設定部分快取並修改查閱轉換的 SQL 陳述式。  
  
 若要深入了解查閱轉換，請參閱＜ [Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。  
  
## <a name="options"></a>選項。  
 **快取大小 (32 位元)**  
 調整 32 位元電腦的快取大小 (以 MB 為單位)。 預設值是 5 MB。  
  
 **快取大小 (64 位元)**  
 調整 64 位元電腦的快取大小 (以 MB 為單位)。 預設值是 5 MB。  
  
 **針對無相符項目的資料列啟用快取**  
 將參考資料集中沒有相符項目的資料列存入快取。  
  
 **來自快取的配置**  
 指定針對在資料集中沒有相符項目的資料列所配置的快取百分比。  
  
 **修改 SQL 陳述式**  
 修改用來產生參考資料集的 SQL 陳述式。  
  
> [!NOTE]  
>  在此頁面上所指定的選擇性 SQL 陳述式會覆寫並取代在 [查閱轉換編輯器] 的 [連接] 頁面上所指定的資料表名稱。 如需詳細資訊，請參閱 [查閱轉換編輯器 &#40;連接頁面&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)＞。  
  
 **設定參數**  
 使用 [設定查詢參數] 對話方塊，即可將輸入資料行對應至參數。  
  
## <a name="external-resources"></a>外部資源  
 blogs.msdn.com 上的部落格文章： [查閱快取模式](http://go.microsoft.com/fwlink/?LinkId=219518)   
  
## <a name="see-also"></a>另請參閱  
 [查閱轉換編輯器&#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md)   
 [查閱轉換編輯器&#40;連接頁面&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [查閱轉換編輯器 &#40;資料行頁面&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [查閱轉換編輯器&#40;錯誤輸出頁面&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [模糊查閱轉換](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
