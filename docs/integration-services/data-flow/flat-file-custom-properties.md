---
title: 一般檔案自訂屬性 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 609fb5bf856bcea35ea7af2e814c9d93008dc5f5
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2018
ms.locfileid: "35406210"
---
# <a name="flat-file-custom-properties"></a>一般檔案自訂屬性
  **來源自訂屬性**  
  
 一般檔案來源同時具有自訂屬性以及所有資料流程元件通用的屬性。  
  
 下表描述的是一般檔案來源的自訂屬性。 所有屬性都是可讀寫的。  
  
|屬性名稱|資料類型|描述|  
|-------------------|---------------|-----------------|  
|FileNameColumnName|String|包含檔案名稱之輸出資料行的名稱。 如果沒有指定任何名稱，就不會產生包含檔案名稱的輸出資料行。<br /><br /> 注意：雖然您無法在 [一般檔案來源編輯器] 中使用這個屬性，但是可以使用 [進階編輯器] 來設定這個屬性。|  
|RetainNulls|布林|一個值，指定當「資料轉換管線」引擎處理資料時，是否要將來源檔案的 Null 值保留成 Null 值。 此屬性的預設值為 **False**。|  
  
 一般檔案來源的輸出沒有任何自訂屬性。  
  
 下表描述的是一般檔案來源之輸出資料行的自訂屬性。 所有屬性都是可讀寫的。  
  
|屬性名稱|資料類型|描述|  
|-------------------|---------------|-----------------|  
|FastParse|布林|一個值，指出資料行會使用 DTS 所提供之速度更快但不區分地區設定的快速剖析常式，還是區分地區設定的標準剖析常式。 如需詳細資訊，請參閱 [快速剖析](http://msdn.microsoft.com/library/6688707d-3c5b-404e-aa2f-e13092ac8d95) 和 [標準剖析](http://msdn.microsoft.com/library/dfe835b1-ea52-4e18-a23a-5188c5b6f013)。 此屬性的預設值為 **False**。<br /><br /> 注意：雖然您無法在 [一般檔案來源編輯器] 中使用這個屬性，但是可以使用 [進階編輯器] 來設定這個屬性。|  
  
 如需詳細資訊，請參閱 [一般檔案來源](../../integration-services/data-flow/flat-file-source.md)。  
  
 **目的地自訂屬性**  
  
 一般檔案目的地同時具有自訂屬性以及所有資料流程元件通用的屬性。  
  
 下表描述的是一般檔案目的地的自訂屬性。 所有屬性都是可讀寫的。  
  
|屬性名稱|資料類型|描述|  
|-------------------|---------------|-----------------|  
|標頭|String|寫入任何資料之前插入檔案中的文字區塊。<br /><br /> 此屬性的值可以使用屬性運算式指定。|  
|Overwrite|布林|一個值，指定要覆寫或附加至具有相同名稱的現有目的地檔案。 這個屬性的預設值為 **True**。|  
  
 一般檔案目的地的輸入和輸入資料行沒有任何自訂屬性。  
  
 如需詳細資訊，請參閱 [一般檔案目的地](../../integration-services/data-flow/flat-file-destination.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
