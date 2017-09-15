---
title: "執行 Data Quality Client 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.browseforservers.f1"
  - "sql13.dqs.connecttoserver.f1"
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# 執行 Data Quality Client 應用程式
  執行 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]並登入 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]。  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Prerequisites"></a> 必要條件  
 您必須執行 DQSInstaller.exe 檔案，才可以完成 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 的安裝。 如需詳細資訊，請參閱 [執行 DQSInstaller.exe 完成 Data Quality Server 安裝](../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 您必須擁有授與 DQS_MAIN 資料庫的其中一個 DQS 角色 (dqs_adminstrator、dqs_kb_editor 或 dqs_kb_operator)，才能登入 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]。  
  
##  <a name="Run"></a> 執行 Data Quality Client  
 若要在已安裝 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 的電腦上執行它，請：  
  
1.  按一下 [ **啟動**, ，指向 **所有程式**, ，按一下 [ **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, ，按一下 [ **Data Quality Services**, ，然後按一下 [ **Data Quality Client**。  
  
2.  在 **[連接到伺服器]** 對話方塊中：  
  
    1.  指定您想要讓 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式連接的目標伺服器。 選取 **(LOCAL)** 連線到 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 本機電腦上。 您也可以按一下向下箭號，然後選取 **\< 瀏覽網路，找出其他伺服器>** 連線到另一部伺服器 （或依照名稱連接到本機伺服器）。 此時會顯示 **[瀏覽伺服器]** 對話方塊。 您可以在 **[本機伺服器]** 索引標籤或 **[網路伺服器]** 索引標籤中選取伺服器。  
  
    2.  加密 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 與 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]之間的資料傳輸，按一下 [選項] ，然後選取 [加密連接]  核取方塊。  
  
3.  按一下 **[連接]**。  
  
 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面隨即出現。 如需詳細資訊，請參閱 [資料品質用戶端首頁畫面](../data-quality-services/data-quality-client-home-screen.md)。  
  
  