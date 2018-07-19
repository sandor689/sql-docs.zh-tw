---
title: 檢閱資料類型對應 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.reviewissues.f1
ms.assetid: 0625c4f9-b8ff-4593-b884-39398b9d43af
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cbfaab44f1b7c40a912eec0c6c6cef8a6b00c51f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158909"
---
# <a name="review-data-type-mapping-sql-server-import-and-export-wizard"></a>檢閱資料類型對應 (SQL Server 匯入和匯出精靈)
  使用**檢閱資料類型對應**頁面來檢閱精靈必須執行才能讓來源資料與目的地相容的資料類型轉換的詳細的資訊。 這項資訊包括視覺提示，可區別預期會成功的轉換與可能導致錯誤或截斷的轉換。 針對每個轉換，您可以決定是否要接受精靈所建議的轉換，而且可以指定如何處理發生的任何錯誤。  
  
 若要深入了解此精靈，請參閱[SQL Server 匯入和匯出精靈](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。 若要深入了解啟動精靈，選項和相關的權限，才能成功執行精靈，請參閱[執行 SQL Server 匯入和匯出精靈](start-the-sql-server-import-and-export-wizard.md)。  
  
 目的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]匯入和匯出精靈是將資料從來源複製到目的地。 這個精靈也可以為您建立目的地資料庫和目的地資料表。 不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。 如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。  
  
## <a name="options"></a>選項。  
 **[檢閱資料類型對應]** 頁面包含 **[資料表]** 清單、 **[資料類型對應]** 清單和錯誤處理選項。  
  
### <a name="table-list"></a>資料表清單  
 上半部**檢閱資料類型問題**頁**資料表**清單，其中列出要從來源傳送到目的地的資料表。 下表將描述這份清單中的資料行。  
  
|「資料行」|描述|  
|------------|-----------------|  
|來源圖示|指出資料類型轉換的成功機率：<br /><br /> 綠色核取記號圖示表示精靈預期這個資料表的所有資料類型轉換都會成功。<br /><br /> 黃色警告圖示表示您應該檢閱精靈即將執行的個別轉換。 若要檢閱這些轉換，請選取資料表，然後在 **[資料類型對應]** 清單中檢閱個別資料行的轉換。<br /><br /> 紅色錯誤圖示表示精靈無法確實針對這個資料表執行某些轉換。|  
|**Source**|顯示來源資料表的名稱。|  
|目的地圖示|指出目的地已經存在或將由精靈建立：<br /><br /> 資料表圖示表示目的地是現有的資料表。<br /><br /> 含有光環的資料表圖示表示目的地是精靈即將建立的新資料表。|  
|**目的地**|顯示目的地資料表的名稱。|  
  
 若要檢視有關個別資料表的轉換資訊，請選取資料表中這**資料表**方格。 選取資料表的轉換資訊會顯示在此頁面下半部 **[資料類型對應]** 方格的資料行中。  
  
### <a name="data-type-mapping-list"></a>資料類型對應清單  
 下半部**檢閱資料類型問題**頁**資料類型對應**清單。 此方格會提供有關在 **[資料表]** 清單中選取之資料表內資料行的詳細轉換資訊。 下表將描述這份清單中的資料行。  
  
|「資料行」|描述|  
|------------|-----------------|  
|轉換圖示|指出資料類型轉換的成功機率：<br /><br /> 綠色核取記號圖示表示精靈預期這個資料行的資料類型轉換會成功。<br /><br /> 黃色警告圖示表示您應該檢閱精靈即將執行的轉換。 若要檢閱轉換，請按兩下資料行，即可檢視 [資料行轉換詳細資訊]  對話方塊。<br /><br /> 紅色錯誤圖示表示精靈無法確實執行轉換。|  
|**來源資料行**|顯示來源資料行的名稱。|  
|**來源類型**|顯示來源資料行的資料類型。|  
|**目的地資料行**|顯示目的地資料行的名稱。|  
|**目的地類型**|顯示目的地資料行的資料類型。|  
|**轉換**|指定是否應該繼續進行規劃的轉換：<br /><br /> 選取此核取方塊，即可讓精靈繼續進行規劃的轉換。<br /><br /> 清除此核取方塊，即可取消資料類型轉換。|  
|**錯誤時**|指定精靈如何處理錯誤：<br /><br /> 使用**錯誤時 （全域）** 設定。<br /><br /> 因錯誤而失敗，並停止匯入或匯出程序。<br /><br /> 忽略錯誤。|  
|**截斷時**|指定精靈如何處理截斷：<br /><br /> 使用**截斷時 （全域）** 設定。<br /><br /> 因錯誤而失敗，並停止匯入或匯出程序。<br /><br /> 忽略截斷。|  
  
 若要檢視有關特定資料行轉換的詳細資訊，請在清單中按兩下任何資料列。 此時， **[資料行轉換詳細資訊]** 對話方塊會開啟並針對該資料行顯示更詳細的轉換資訊。  
  
### <a name="error-handling-options"></a>錯誤處理選項  
 **錯誤時 (全域)**  
 指定精靈如何處理錯誤：  
  
-   因錯誤而失敗，並停止匯入或匯出程序。  
  
-   忽略錯誤，並繼續進行匯入或匯出程序。  
  
 這項設定會套用至在 **[資料類型對應]** 清單的 **[錯誤時]** 資料行中選取了 **[使用全域]** 的所有轉換。  
  
 **截斷時 (全域)**  
 指定精靈如何處理截斷：  
  
-   因錯誤而失敗，並停止匯入或匯出程序。  
  
-   忽略截斷，並繼續進行匯入或匯出程序。  
  
 這項設定會套用至在 **[資料類型對應]** 清單的 **[截斷時]** 資料行中選取了 **[使用全域]** 的所有轉換。  
  
  