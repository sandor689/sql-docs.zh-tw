---
title: "驗證資料 (適用於 Excel 的 MDS 增益集) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# 驗證資料 (適用於 Excel 的 MDS 增益集)
  在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，當您發行資料時，會進行下列兩種驗證類型：  
  
-   任何已定義的商務規則會套用至資料。  
  
-   對允許的屬性值 (例如，字元數目或資料類型) 檢查資料。  
  
 在每種情況下，有效資料都會發行到 MDS 儲存機制。 無效資料已反白顯示，而且在狀態資料行中顯示錯誤的詳細資料。  
  
## 當發生驗證時  
 在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，當您發行新的或已變更的資料時，或當您手動套用商務規則時，會發生驗證。  
  
 當商務規則失敗時，資料仍然會發行到 MDS 儲存機制。 當輸入驗證失敗時，資料就不會發行到儲存機制。  
  
## 驗證狀態  
 在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，可能出現下列幾種驗證狀態：  
  
 如需其他狀態的資訊，請參閱[驗證狀態 &#40;Master Data Services&#41;](../../master-data-services/validation-statuses-master-data-services.md)。  
  
|狀態|說明|  
|------------|-----------------|  
|驗證失敗|對 MDS 管理員所定義的商務規則，資料列中一個或多個值的驗證失敗。|  
|驗證成功|資料列中的所有值已經通過商務規則驗證。|  
  
## 輸入狀態  
 在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，可能出現下列幾種輸入狀態：  
  
|狀態|說明|  
|------------|-----------------|  
|錯誤|資料列中一個或多個值不符合系統需求，如長度或資料類型。 MDS 儲存機制中的值未更新。|  
|新資料列|資料列中的值尚未發行到 MDS 儲存機制。|  
|唯讀|登入的使用者有資料列中一個或多個值的唯讀權限，而且值無法更新。|  
|未變更|工作表中尚未變更資料列中的任何值。 這不表示儲存機制中的值尚未變更；若要取得工作表中最新的資料，請在 [連接和載入] 群組中，請按一下 [載入或重新整理]。<br /><br /> 這是每個資料列的預設值。|  
  
## 相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|判斷哪些值未通過已定義的商務規則。|[套用商務規則 &#40;適用於 Excel 的 MDS 增益集&#41;](../../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
|若要更正驗證錯誤，請檢視成員進行的所有交易。|[檢視成員的所有註解或交易 &#40;適用於 Excel 的 MDS 增益集&#41;](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## 相關內容  
  
-   [概觀：從 Excel 匯入資料 &#40;適用於 Excel 的 MDS 增益集&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  