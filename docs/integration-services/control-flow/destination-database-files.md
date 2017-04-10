---
title: "目的地資料庫檔案 | Microsoft Docs"
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
  - "sql13.dts.designer.transferdatabasetask.destdbfiles.f1"
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# 目的地資料庫檔案
  使用 **[目的地資料庫檔案]** 對話方塊，即可檢視或變更目的地伺服器上的資料庫檔案名稱和位置，或是指定傳送資料庫工作的網路檔案位置。 如需這項工作的詳細資訊，請參閱[傳送資料庫工作](../../integration-services/control-flow/transfer-database-task.md)。  
  
 若要使用來源伺服器上的資料庫檔案名稱和位置，來自動擴展此對話方塊，請先在 **[傳送資料庫工作編輯器]**對話方塊的 **[資料庫]**頁面中，指定 **[SourceConnection]** 、 **[SourceDatabaseName]** 和 **[SourceDatabaseFiles]** 。  
  
## 選項。  
 **目的地檔案**  
 目的地伺服器上已傳送資料庫檔案的名稱。  
  
 輸入檔案名稱，或是按一下檔案名稱來編輯它。  
  
 **目的資料夾**  
 目的地伺服器上的資料夾，用於存放將傳送的資料庫檔案。  
  
 輸入資料夾路徑，按一下該資料夾路徑來編輯它，或是按一下瀏覽來找出在目的地伺服器上的資料夾，以存放要傳送的資料庫檔案。  
  
 **網路檔案共用**  
 在目的地伺服器上的網路共用資料夾，其中存放要傳送的資料庫檔案。 當您在 **[傳送資料庫工作編輯器]** 對話方塊的 **[資料庫]** 頁面中，將 **[方法]** 指定為 **[DatabaseOffline]** ，以離線模式傳送資料庫時，請使用 **[網路檔案共用]** 。  
  
 輸入網路檔案共用位置，或是按一下瀏覽來找出網路檔案共用位置。  
  
 當您以離線模式傳送資料庫時，在將資料庫檔案傳送到 **[目的資料夾]** 位置之前，會將其複製到 **[網路檔案共用]** 位置。  
  
## 請參閱＜  
 [Integration Services 錯誤和訊息參考](../../integration-services/integration-services-error-and-message-reference.md)   
 [傳送資料庫工作編輯器 &#40;一般頁面&#41;](../../integration-services/control-flow/transfer-database-task-editor-general-page.md)   
 [傳送資料庫工作編輯器 &#40;資料庫頁面&#41;](../../integration-services/control-flow/transfer-database-task-editor-databases-page.md)  
  
  