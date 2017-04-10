---
title: "ADO NET 來源編輯器 (連接管理員頁面) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.adonetsource.connection.f1"
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# ADO NET 來源編輯器 (連接管理員頁面)
  使用 [ADO NET 來源編輯器] 對話方塊的 [連線管理員] 頁面，即可選取來源的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員。 這個頁面也可以讓您從資料庫中選取資料表或檢視。  
  
 若要深入了解 ADO NET 來源，請參閱＜ [ADO NET Source](../../integration-services/data-flow/ado-net-source.md)＞。  
  
 **開啟連接管理員頁面**  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟具有 ADO NET 來源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。  
  
2.  在 [資料流程] 索引標籤中，按兩下 ADO NET 來源。  
  
3.  在 [ADO NET 來源編輯器] 中，按一下 [連線管理員]。  
  
## 靜態選項  
 **ADO.NET 連接管理員**  
 從清單中選取現有的連線管理員，或按一下 [新增] 來建立新的連線。  
  
 **新增**  
 使用 [設定 ADO.NET 連線管理員] 對話方塊建立新的連線管理員。  
  
 **資料存取模式**  
 從來源中指定選取資料的方法。  
  
|選項|說明|  
|------------|-----------------|  
|資料表或檢視|從 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 資料來源中的資料表或檢視擷取資料。|  
|SQL (命令)|使用 SQL 查詢從 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 資料來源中擷取資料。|  
  
 **預覽**  
 使用 [資料檢視] 對話方塊來預覽結果。 [預覽] 最多可顯示 200 個資料列。  
  
> [!NOTE]  
>  在預覽資料時，具有 CLR 使用者定義型別的資料行不會包含資料。 而會顯示 \<數值太大而無法顯示> 或 System.Byte[]。 使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 提供者存取資料來源時會顯示前者，而使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 提供者時會顯示後者。  
  
## 資料存取模式動態選項  
  
### 資料存取模式 = 資料表或檢視  
 **資料表或檢視的名稱**  
 從資料來源中可用的清單中選取資料表或檢視名稱。  
  
### 資料存取模式 = SQL 命令  
 **SQL 命令文字**  
 輸入 SQL 查詢文字，按一下 [建立查詢] 建立查詢，或按一下 [瀏覽] 找到包含查詢文字的檔案。  
  
 **建立查詢**  
 使用 [查詢產生器] 對話方塊，以視覺化的方式來建構 SQL 查詢。  
  
 **瀏覽**  
 使用 [開啟] 對話方塊來找出包含 SQL 查詢文字的檔案。  
  
## 請參閱＜  
 [ADO NET 來源編輯器 &#40;資料行頁面&#41;](../../integration-services/data-flow/ado-net-source-editor-columns-page.md)   
 [ADO NET 來源編輯器 &#40;錯誤輸出頁面&#41;](../../integration-services/data-flow/ado-net-source-editor-error-output-page.md)   
 [ADO.NET 連接管理員](../../integration-services/connection-manager/ado-net-connection-manager.md)  
  
  