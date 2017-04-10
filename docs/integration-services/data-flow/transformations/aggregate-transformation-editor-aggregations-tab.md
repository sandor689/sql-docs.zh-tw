---
title: "彙總轉換編輯器 (彙總索引標籤) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.aggregationtransformation.aggregations.f1"
helpviewer_keywords: 
  - "彙總轉換編輯器"
ms.assetid: a01cb124-ec79-4673-b1a1-bf4d60ee1b45
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# 彙總轉換編輯器 (彙總索引標籤)
  使用 [彙總轉換編輯器] 對話方塊的 [彙總] 索引標籤，即可指定彙總的資料行與彙總屬性。 您可以套用多個彙總。 此轉換不會產生錯誤輸出。  
  
> [!NOTE]  
>  索引鍵計數、索引鍵小數位數、相異索引鍵計數和相異索引鍵小數位數的選項，若是指定在 [進階] 索引標籤上，就會套用至元件層級；若是指定在 [彙總] 索引標籤的進階畫面上，則會套用至輸出層級；若是指定在 [彙總] 索引標籤底端的資料行清單中，則會套用至資料行層級。  
>   
>  在彙總轉換中， **[索引鍵]** 和 **[索引鍵小數位數]** 會參考預期要從 **[群組依據]** 作業產生的群組數。 **[計算相異索引鍵]** 和 **[計算相異小數位數]** 會參考預期要從 **[相異計數]** 作業產生的相異值數目。  
  
 若要了解有關彙總轉換的詳細資訊，請參閱＜ [Aggregate Transformation](../../../integration-services/data-flow/transformations/aggregate-transformation.md)＞。  
  
## 選項。  
 **進階 / 基本**  
 顯示或隱藏設定多個輸出之多個彙總的選項。 依預設，會隱藏 [進階] 選項。  
  
 **彙總名稱**  
 在 [進階] 顯示中，輸入彙總的易記名稱。  
  
 **群組依據資料行**  
 在 [進階] 顯示中，使用 [可用的輸入資料行] 清單選取要群組的資料行，如下所述。  
  
 **索引鍵小數位數**  
 在 [進階] 顯示中，選擇性地指定彙總可以寫入的大約索引鍵數目。 根據預設，此選項的值為 **[未指定]**。 如果 [索引鍵小數位數] 和 [索引鍵] 屬性都有設定，會優先使用 [索引鍵]。  
  
|Value|說明|  
|-----------|-----------------|  
|[未指定]|不使用 [索引鍵小數位數] 屬性。|  
|低|彙總可寫入大約 500,000 個索引鍵。|  
|中|彙總可寫入大約 5,000,000 個索引鍵。|  
|高|彙總可寫入超過 25,000,000 個索引鍵。|  
  
 **索引鍵**  
 在 [進階] 顯示中，選擇性地指定彙總可以寫入的確切索引鍵數目。 如果 [索引鍵小數位數] 和 [索引鍵] 都有指定，會優先使用 [索引鍵]。  
  
 **可用的輸入資料行**  
 使用此資料表中的核取方塊，從可用的輸入資料行清單中選取。  
  
 **輸入資料行**  
 從可用的輸入資料行清單中選取。  
  
 **輸出別名**  
 輸入每個資料行的別名。 預設是輸入資料行的名稱；但是，您可以選擇任何唯一的、描述性名稱。  
  
 **運算**  
 使用下表作為指南，從可用的作業清單中選擇。  
  
|運算|說明|  
|---------------|-----------------|  
|**GroupBy**|將資料集分割成群組。 具有任何資料類型的資料行可用於分組。 如需詳細資訊，請參閱 GROUP BY。|  
|**Sum**|加總資料行中的值。 只能加總具有數值資料類型的資料行。 如需詳細資訊，請參閱 SUM。|  
|**平均值**|傳回資料行中資料行值的平均。 只能平均具有數值資料類型的資料行。 如需詳細資訊，請參閱 AVG。|  
|**Count**|傳回群組中的項目數。 如需詳細資訊，請參閱 COUNT。|  
|**CountDistinct**|傳回群組中唯一非 Null 值的數目。 如需詳細資訊，請參閱 COUNT 和 Distinct。|  
|**最小值**|傳回群組中的最小值。 限制為數值資料類型。|  
|**最大值**|傳回群組中的最大值。 限制為數值資料類型。|  
  
 **比較旗標**  
 如果您選擇 [群組依據]，請使用核取方塊來控制轉換執行比較的方式。 如需字串比較選項的資訊，請參閱[比較字串資料](../../../integration-services/data-flow/comparing-string-data.md)。  
  
 **計算相異小數位數**  
 可選擇性地指定彙總可寫入之相異值的近似數目。 根據預設，此選項的值為 **[未指定]**。 如果 [CountDistinctScale] 和 [CountDistinctKeys] 都有指定，會優先使用 [CountDistinctKeys]。  
  
|Value|說明|  
|-----------|-----------------|  
|[未指定]|不使用 **CountDistinctScale** 屬性。|  
|低|彙總可寫入大約 500,000 個相異值。|  
|中|彙總可寫入大約 5,000,000 個相異值。|  
|高|彙總可寫入超過 25,000,000 個相異值。|  
  
 **計算相異索引鍵**  
 可選擇性地指定彙總可寫入之相異值的確實數目。 如果 [CountDistinctScale] 和 [CountDistinctKeys] 都有指定，會優先使用 [CountDistinctKeys]。  
  
## 請參閱＜  
 [Integration Services 錯誤和訊息參考](../../../integration-services/integration-services-error-and-message-reference.md)   
 [彙總轉換編輯器 &#40;進階索引標籤&#41;](../../../integration-services/data-flow/transformations/aggregate-transformation-editor-advanced-tab.md)   
 [使用彙總轉換來彙總資料集中的值](../../../integration-services/data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  