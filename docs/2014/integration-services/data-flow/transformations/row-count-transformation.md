---
title: 資料列計數轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 966f42cf41f93c162ef3aac7be17fce920edbceb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209528"
---
# <a name="row-count-transformation"></a>資料列計數轉換
  「資料列計數」轉換會在資料列通過資料流程時計算其數目，並將最後計數儲存到變數中。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 封裝可使用資料列計數更新指令碼、運算式和屬性運算式中使用的變數 (例如，儲存資料列計數的變數可更新電子郵件訊息中的訊息文字，以便加入資料列數)。「資料列計數」轉換使用的變數必須已存在，且必須在擁有「資料列計數」轉換的資料流程所屬的「資料流程」工作範圍內。  
  
 此轉換只會在最後一個資料列傳遞至轉換之後，才使用變數儲存資料列計數值。 因此，變數的值不會及時更新為使用資料流程中包含「資料列計數」轉換的更新值。 您可以在個別的資料流程中使用更新的變數。  
  
 此轉換有一個輸入和一個輸出。 它不支援錯誤輸出。  
  
## <a name="configuration-of-the-row-count-transformation"></a>資料列計數轉換的組態  
 您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。  
  
 **[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。 如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：  
  
-   [通用屬性](../../common-properties.md)  
  
-   [轉換自訂屬性](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>相關工作  
 如需如何設定此元件屬性的資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services &#40;SSIS&#41;變數](../../integration-services-ssis-variables.md)   
 [資料流程](../data-flow.md)   
 [Integration Services 轉換](integration-services-transformations.md)  
  
  
