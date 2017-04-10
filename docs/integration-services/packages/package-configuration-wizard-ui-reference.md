---
title: "封裝組態精靈 UI 參考 | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.configwizard.finishdtsconfiguration.f1"
  - "sql13.dts.configwizard.selectobjects.f1"
  - "sql13.dts.configwizard.selecconfigtype.f1"
  - "sql13.dts.configwizard.welcome.f1"
ms.assetid: adca6938-6d5a-40ec-950e-dceb79d044fe
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# 封裝組態精靈 UI 參考
  使用 **[封裝組態精靈]** ，即可建立在執行階段更新 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝及其物件之屬性的組態。 當您在 **[封裝組態組合管理]** 對話方塊中加入新的組態或修改現有的組態時，這個精靈便會執行 若要開啟 **[封裝組態組合管理]** 對話方塊，請在 **中選取** [SSIS] **功能表上的** [封裝組態] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。 如需詳細資訊，請參閱[建立封裝組態](../../integration-services/packages/create-package-configurations.md)。  
  
> **注意**：組態可用於套件部署模型。 參數是用來取代專案部署模型的組態。 專案部署模型讓您能將 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。 如需有關部署模型的詳細資訊，請參閱＜ [Deployment of Projects and Packages](https://msdn.microsoft.com/library/hh213290.aspx)＞。  
  
 下列章節描述精靈頁面。  
  
## 歡迎使用封裝組態精靈頁面  
 使用 **[SSIS 組態精靈]** ，即可建立在執行階段更新封裝及其物件之屬性的組態。  
  
### 選項。  
 **不要再顯示此頁面**  
 下次開啟精靈時略過歡迎頁面。  
  
 **下一個**  
 移至精靈的下一個頁面。  
  
## 選取組態類型頁面  
 使用 **[選取組態類型]** 頁面，即可指定要建立的組態類型。  
  
 如果需要其他資訊才可決定要使用的組態類型，請參閱＜ [Package Configurations](../../integration-services/packages/package-configurations.md)＞。  
  
### 靜態選項  
 **組態類型**  
 使用下列選項，即可選取儲存組態的來源類型：  
  
|Value|說明|  
|-----------|-----------------|  
|**XML 組態檔**|將組態儲存為 XML 檔案。 選取這個值就會顯示 **[組態類型]**區段中的動態選項。|  
|**環境變數**|將組態儲存在其中一個環境變數中。 選取這個值就會顯示 **[組態類型]**區段中的動態選項。|  
|**登錄項目**|將組態儲存在登錄中。 選取這個值就會顯示 **[組態類型]**區段中的動態選項。|  
|**父封裝變數**|以變數將組態儲存在包含工作的封裝中。  選取這個值就會顯示 **[組態類型]**區段中的動態選項。|  
|**SQL Server**|將組態儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的資料表中。 選取這個值就會顯示 **[組態類型]**區段中的動態選項。|  
  
 **下一個**  
 檢視精靈順序的下一頁。  
  
### 動態選項  
  
#### 組態類型選項 = XML 組態檔  
 **直接指定組態設定**  
 這可用來直接指定設定。  
  
|Value|說明|  
|-----------|-----------------|  
|**組態檔名稱**|鍵入精靈產生之組態檔的路徑。|  
|**瀏覽**|使用 **[選取組態檔位置]** 對話方塊，即可指定精靈產生之組態檔的路徑。 如果檔案不存在，精靈就會建立檔案。|  
  
 **組態位置儲存在環境變數中**  
 這可用來指定儲存組態的環境變數。  
  
|Value|說明|  
|-----------|-----------------|  
|**環境變數**|從清單中選取環境變數。|  
  
#### 組態類型選項 = 環境變數  
 **環境變數**  
 選取包含組態資訊的環境變數。  
  
#### 組態類型選項 = 登錄項目  
 **直接指定組態設定**  
 這可用來直接指定設定。  
  
|Value|說明|  
|-----------|-----------------|  
|**登錄項目**|輸入包含組態資訊的登錄機碼。 格式為 \<registry key>。<br /><br /> 登錄機碼必須已經存在於 HKEY_CURRENT_USER 中且具有名為 Value 的值。 該值可以是 DWORD 或字串。<br /><br /> 如果您想要使用不是在 HKEY_CURRENT_USER 根目錄的登錄機碼，請使用 \<Registry key\registry key\\...> 格式來識別該機碼。|  
  
 **組態位置儲存在環境變數中**  
 這可用來指定儲存組態的環境變數。  
  
|Value|說明|  
|-----------|-----------------|  
|**環境變數**|從清單中選取環境變數。|  
  
#### 組態類型選項 = 父封裝變數  
 **直接指定組態設定**  
 這可用來直接指定設定。  
  
|Value|說明|  
|-----------|-----------------|  
|**父變數**|在包含組態資訊的父封裝中指定變數。|  
  
 **組態位置儲存在環境變數中**  
 這可用來指定儲存組態的環境變數。  
  
|Value|說明|  
|-----------|-----------------|  
|**環境變數**|從清單中選取環境變數。|  
  
#### 組態類型選項 = SQL Server  
 **直接指定組態設定**  
 這可用來直接指定設定。  
  
|Value|說明|  
|-----------|-----------------|  
|**連接**|請從清單中選取連接，或按一下 **[新增]** 即可建立新的連接。|  
|**組態資料表**|選取現有的資料表，或按一下 **[新增]** ，即可撰寫建立新資料表的 SQL 陳述式。|  
|**組態篩選**|選取現有的組態名稱或鍵入新的名稱。<br /><br /> 許多 SQL Server 組態可儲存在相同的資料表中，且每個組態都可包括多個組態項目。<br /><br /> 這個使用者自訂值是儲存在資料表中，以識別特定組態所屬的組態項目。|  
  
 **組態位置儲存在環境變數中**  
 這可用來指定儲存組態的環境變數。  
  
|Value|說明|  
|-----------|-----------------|  
|**環境變數**|從清單中選取環境變數。|  
  
## 選取要匯出的物件頁面  
 使用 **[選取目標屬性] 或 [選取要匯出的屬性]** 頁面，即可指定組態包含的物件屬性。 只有選取 XML 組態類型時，才能選取多個屬性。  
  
### 選項。  
 **物件**  
 展開封裝階層，並選取要匯出的屬性。  
  
 **Property 屬性**  
 檢視屬性 (property) 的屬性 (attribute)。  
  
 **下一個**  
 移至精靈的下一頁。  
  
## 正在完成精靈頁面  
 使用 **[正在完成精靈]** 頁面，即可提供組態的名稱，並檢視精靈用來建立組態的設定。 在精靈完成之後，就會顯示 **[封裝組態組合管理]** ，其中會列出封裝的所有組態。  
  
### 選項。  
 **組態名稱**  
 鍵入組態的名稱。  
  
 **預覽**  
 檢視精靈用來建立組態的設定。  
  
 **完成**  
 建立組態，並結束 [封裝組態精靈]。  
  
## 請參閱＜  
 [建立封裝組態](../../integration-services/packages/create-package-configurations.md)  
  
  