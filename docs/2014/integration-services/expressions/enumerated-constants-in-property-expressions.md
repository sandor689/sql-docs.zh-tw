---
title: 屬性運算式中的列舉常數 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d000c77263a0448ff838bff42a5020b86a299a72
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221828"
---
# <a name="enumerated-constants-in-property-expressions"></a>屬性運算式中的列舉常數
  如果屬性運算式包含來自列舉值成員清單的值，運算式必須使用列舉值成員的數值來取代成員的易記名稱。 例如，如果運算式設定`LoggingMode`屬性，您必須使用數值 2 來取代易記名稱 Disabled。  
  
 此主題列出相當於列舉值易記名稱的數值，但僅限屬性運算式中常用之成員所屬的列舉值。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 物件模型包含其他許多列舉值，您在設計物件模型程式以程式設計方式建立封裝，或是對自訂封裝元素 (例如工作和資料流程元件) 進行編碼時，都會使用這些列舉值。  
  
 除了封裝和封裝物件適用的自訂屬性以外， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的 [屬性] 視窗還包含一組可用於封裝、工作以及「Foreach 迴圈」、「For 迴圈」和「時序」等容器的屬性。 來自列舉值的值所設定的通用屬性 (`ForceExecutionResult`、`LoggingMode`、`IsolationLevel` 和 `Transaction Option`) 都列在「通用屬性」一節。  
  
 下列章節提供有關列舉常數的資訊：  
  
 [封裝](#Package)  
  
 [Foreach 迴圈列舉值](#Foreach)  
  
 [工作](#Tasks)  
  
 [維護計畫工作](#MaintenancePlanTasks)  
  
 [通用屬性](#CommonProperties)  
  
##  <a name="Package"></a> 封裝  
 下列表格列出使用來自列舉值的值所設定之封裝屬性的易記名稱和數值相等項。  
  
 `PackageType` 屬性 — 使用來自值來設定`DTSPackageType`列舉型別。  
  
|DTSPackageType 中的易記名稱|數值|  
|-------------------------------------|-------------------|  
|預設|0|  
|DTSWizard|1|  
|DTSDesigner|2|  
|SQLReplication|3|  
|DTSDesigner100|5|  
|SQLDBMaint|6|  
  
 `CheckpointUsage` 屬性 — 使用來自值來設定`DTSCheckpointUsage`列舉型別。  
  
|DTSCheckpointUsage 中的易記名稱|數值|  
|-----------------------------------------|-------------------|  
|永不|0|  
|IfExists|1|  
|永遠|2|  
  
 `PackagePriorityClass` 屬性 — 使用來自值來設定`DTSPriorityClass`列舉型別。  
  
|DTSPriorityClass 中的易記名稱|數值|  
|---------------------------------------|-------------------|  
|預設|0|  
|AboveNormal|1|  
|一般|2|  
|BelowNormal|3|  
|Idle|4|  
  
 `ProtectionLevel` 屬性 — 使用來自值來設定`DTSProtectionLevel`列舉型別。  
  
|DTSProtectionLevel 中的易記名稱|數值|  
|-----------------------------------------|-------------------|  
|DontSaveSensitive|0|  
|EncryptSensitiveWithUserKey|1|  
|EncryptSensitiveWithPassword|2|  
|EncryptAllWithPassword|3|  
|EncryptAllWithUserKey|4|  
|ServerStorage|5|  
  
##  <a name="PrecedenceConstraints"></a> 優先順序條件約束  
 `EvalOp` 屬性 — 使用來自值來設定`DTSPrecedenceEvalOp`列舉型別。  
  
|DTSPrecedenceEvalOp 中的易記名稱|數值|  
|------------------------------------------|-------------------|  
|運算式|1|  
|條件約束|2|  
|ExpressionAndConstraint|3|  
|ExpressionOrConstraint|4|  
  
 `Value` 屬性 — 使用來自值來設定`DTSExecResult`列舉型別。  
  
|易記名稱|數值|  
|-------------------|-------------------|  
|成功|0|  
|失敗|1|  
|Completion|2|  
|已取消|3|  
  
##  <a name="Foreach"></a> Foreach 迴圈列舉值  
 「Foreach 迴圈」包含一組列舉值，其屬性可由屬性運算式設定。  
  
### <a name="foreach-ado-enumerator"></a>Foreach ADO 列舉值  
 `Type` 屬性 — 使用來自值來設定`ADOEnumerationType`列舉型別。  
  
|ADOEnumerationType 中的易記名稱|數值|  
|-----------------------------------------|-------------------|  
|EnumerateTables|0|  
|EnumerateAllRows|1|  
|EnumerateRowsInFirstTable|2|  
  
### <a name="foreach-nodelist-enumerator"></a>Foreach NodeList 列舉值  
 `SourceDocumentType``InnerXPathStringSourceType`，並**OuterXPathStringSourceType**屬性 — 使用中的值設定`SourceType`列舉型別。  
  
|SourceType 中的易記名稱|數值|  
|---------------------------------|-------------------|  
|FileConnection|0|  
|變數|1|  
|DirectInput|2|  
  
 `EnumerationType` 屬性 — 使用來自值來設定`EnumerationType`列舉型別。  
  
|EnumerationType 中的易記名稱|數值|  
|--------------------------------------|-------------------|  
|Navigator|0|  
|節點|1|  
|NodeText|2|  
|ElementCollection|3|  
  
 `InnerElementType` 屬性 — 使用來自值來設定`InnerElementType`列舉型別。  
  
|InnerElementType 中的易記名稱|數值|  
|---------------------------------------|-------------------|  
|Navigator|0|  
|節點|1|  
|NodeText|2|  
  
##  <a name="Tasks"></a> 工作  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含許多工作，其屬性可由屬性運算式設定。  
  
### <a name="analysis-services-execute-ddl-task"></a>Analysis Services 執行 DDL 工作  
 `SourceType` 屬性 — 使用來自值來設定`DDLSourceType`列舉型別。  
  
|DDLSourceType 中的易記名稱|數值|  
|------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|變數|2|  
  
### <a name="bulk-insert-task"></a>大量插入工作  
 `DataFileType` 屬性 — 使用來自值來設定`DTSBulkInsert_DataFileType`列舉型別。  
  
|DTSBulkInsert_DataFileType 中的易記名稱|數值|  
|--------------------------------------------------|-------------------|  
|DTSBulkInsert_DataFileType_Char|0|  
|DTSBulkInsert_DataFileType_Native|1|  
|DTSBulkInsert_DataFileType_WideChar|2|  
|DTSBulkInsert_DataFileType_WideNative|3|  
  
### <a name="execute-sql-task"></a>執行 SQL 工作  
 `ResultSetType` 屬性 — 使用來自值來設定`ResultSetType`列舉型別。  
  
|ResultSetType 中的易記名稱|數值|  
|------------------------------------|-------------------|  
|ResultSetType_None|1|  
|ResultSetType_SingleRow|2|  
|ResultSetType_Rowset|3|  
|ResultSetType_XML|4|  
  
 `SqlStatementSourceType` 屬性 — 使用來自值來設定`SqlStatementSourceType`列舉型別。  
  
|SqlStatementSourceType 中的易記名稱|數值|  
|---------------------------------------------|-------------------|  
|DirectInput|1|  
|FileConnection|2|  
|變數|3|  
  
### <a name="file-system-task"></a>檔案系統工作  
 `Operation` 屬性 — 使用來自值來設定`DTSFileSystemOperation`列舉型別。  
  
|DTSFileSystemOperation 中的易記名稱|數值|  
|---------------------------------------------|-------------------|  
|CopyFile|0|  
|MoveFile|1|  
|DeleteFile|2|  
|RenameFile|3|  
|SetAttributes|4|  
|CreateDirectory|5|  
|CopyDirectory|6|  
|MoveDirectory|7|  
|DeleteDirectory|8|  
|DeleteDirectoryContent|9|  
  
 `Attributes` 屬性 — 使用來自值來設定`DTSFileSystemAttributes`列舉型別。  
  
|DTSFileSystemAttributes 中的易記名稱|數值|  
|----------------------------------------------|-------------------|  
|一般|0|  
|Archive|1|  
|Hidden|2|  
|ReadOnly|4|  
|系統|8|  
  
### <a name="ftp-task"></a>FTP 工作  
 `Operation` 屬性 — 使用來自值來設定`DTSFTPOp`列舉型別。  
  
|DTSFTPOp 中的易記名稱|數值|  
|-------------------------------|-------------------|  
|Send|0|  
|Receive|1|  
|DeleteLocal|2|  
|DeleteRemote|3|  
|MakeDirLocal|4|  
|MakeDirRemote|5|  
|RemoveDirLocal|6|  
|RemoveDirRemote|7|  
  
### <a name="message-queue-task"></a>Message Queue Task  
 `MessageType` 屬性 — 使用來自值來設定`MQMessageType`列舉型別。  
  
|MQMessageType 中的易記名稱|數值|  
|------------------------------------|-------------------|  
|DTSMQMessageType_String|0|  
|DTSMQMessageType_DataFile|1|  
|DTSMQMessageType_Variables|2|  
|DTSMQMessagType_StringMessageToVariable|3|  
  
 `StringCompareType` 屬性 — 使用來自值來設定`MQStringMessageCompare`列舉型別。  
  
|MQStringMessageCompare 中的易記名稱|數值|  
|---------------------------------------------|-------------------|  
|DTSMQStringMessageCompare_None|0|  
|DTSMQStringMessageCompare_Exact|1|  
|DTSMQStringMessageCompare_IgnoreCase|2|  
|DTSMQStringMessageCompare_Contains|3|  
  
 `TaskType` 屬性 — 使用來自值來設定`MQType`列舉型別。  
  
|MQType 中的易記名稱|數值|  
|-----------------------------|-------------------|  
|DTSMQType_Sender|0|  
|DTSMQType_Receiver|1|  
  
### <a name="send-mail-task"></a>傳送郵件工作  
 `MessageSourceType` 屬性 — 使用來自值來設定`SendMailMessageSourceType`列舉型別。  
  
|SendMailMessageSourceType 中的易記名稱|數值|  
|------------------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|變數|2|  
  
 `Priority` 屬性 — 使用來自值來設定`MailPriority`列舉型別。  
  
|MailPriority 中的易記名稱|數值|  
|-----------------------------------|-------------------|  
|高|1|  
|一般|3|  
|低|5|  
  
### <a name="transfer-database-task"></a>傳送資料庫工作  
 `Action` 屬性 — 使用來自值來設定`TransferAction`列舉型別。  
  
|TransferAction 中的易記名稱|數值|  
|-------------------------------------|-------------------|  
|[複製]|0|  
|[移動]|1|  
  
 `Method` 屬性 — 使用來自值來設定`TransferMethod`列舉型別。  
  
|TransferMethod 中的易記名稱|數值|  
|-------------------------------------|-------------------|  
|DatabaseOffline|0|  
|DatabaseOnline|1|  
  
### <a name="transfer-error-messages-task"></a>傳送錯誤訊息工作  
 `IfObjectExists` 屬性 — 使用來自值來設定`IfObjectExists`列舉型別。  
  
|IfObjectExists 中的易記名稱|數值|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-jobs-task"></a>傳送作業工作  
 `IfObjectExists` 屬性 — 使用來自值來設定`IfObjectExists`列舉型別。  
  
|IfObjectExists 中的易記名稱|數值|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-logins-task"></a>傳送登入工作  
 `IfObjectExists` 屬性 — 使用來自值來設定`IfObjectExists`列舉型別。  
  
|IfObjectExists 中的易記名稱|數值|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
 `LoginsToTransfer` 屬性 — 使用來自值來設定`LoginsToTransfer`列舉型別。  
  
|LoginsToTransfer 中的易記名稱|數值|  
|---------------------------------------|-------------------|  
|AllLogins|0|  
|SelectedLogins|1|  
|AllLoginsFromSelectedDatabases|2|  
  
### <a name="transfer-master-stored-procedures-task"></a>傳送主要預存程序工作  
 `IfObjectExists` 屬性 — 使用來自值來設定`IfObjectExists`列舉型別。  
  
|IfObjectExists 中的易記名稱|數值|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-sql-server-objects-task"></a>傳送 SQL Server 物件工作  
 `ExistingData` 屬性 — 使用來自值來設定`ExistingData`列舉型別。  
  
|ExistingData 中的易記名稱|數值|  
|-----------------------------------|-------------------|  
|取代|0|  
|附加|1|  
  
### <a name="web-service-task"></a>Web 服務工作  
 `OutputType` 屬性 — 使用來自值來設定`DTSOutputType`列舉型別。  
  
|DTSOutputType 中的易記名稱|數值|  
|------------------------------------|-------------------|  
|檔案|0|  
|變數|1|  
  
### <a name="wmi-data-reader-task"></a>WMI 資料讀取器工作  
 `OverwriteDestination` 屬性 — 使用來自值來設定`OverwriteDestination`列舉型別。  
  
|OverwriteDestination 中的易記名稱|數值|  
|-------------------------------------------|-------------------|  
|OverwriteDestination|0|  
|AppendToDestination|1|  
|KeepOriginal|2|  
  
 `OutputType` 屬性 — 使用來自值來設定`OutputType`列舉型別。  
  
|OutputType 中的易記名稱|數值|  
|---------------------------------|-------------------|  
|DataTable|0|  
|PropertyValue|1|  
|PropertyNameAndValue|2|  
  
 `DestinationType` 屬性 — 使用來自值來設定`DestinationType`列舉型別。  
  
|DestinationType 中的易記名稱|數值|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|變數|1|  
  
 `WqlQuerySourceType` 屬性 — 使用來自值來設定`QuerySourceType`列舉型別。  
  
|QuerySourceType 中的易記名稱|數值|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|變數|2|  
  
 WMI 事件監看員 `ActionAtEvent` 屬性 — 使用來自 `ActionAtEvent` 列舉的值加以設定。  
  
|ActionAtEvent 中的易記名稱|數值|  
|------------------------------------|-------------------|  
|LogTheEventAndFireDTSEvent|0|  
|LogTheEvent|1|  
  
 `ActionAtTimeout` 屬性 — 使用來自值來設定`ActionAtTimeout`列舉型別。  
  
|ActionAtTimeout 中的易記名稱|數值|  
|--------------------------------------|-------------------|  
|LogTimeoutAndFireDTSEvent|0|  
|LogTimeout|1|  
  
 `AfterEvent` 屬性 — 使用來自值來設定`AfterEvent`列舉型別。  
  
|AfterEvent 中的易記名稱|數值|  
|---------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `AfterTimeout` 屬性 — 使用來自值來設定`AfterTimeout`列舉型別。  
  
|AfterTimeout 中的易記名稱|數值|  
|-----------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `WqlQuerySourceType` 屬性 — 使用來自值來設定`QuerySourceType`列舉型別。  
  
|QuerySourceType 中的易記名稱|數值|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|變數|2|  
  
### <a name="xml-task"></a>XML 工作  
 `OperationType` 屬性 — 使用來自值來設定`DTSXMLOperation`列舉型別。  
  
|DTSXMLOperation 中的易記名稱|數值|  
|--------------------------------------|-------------------|  
|Validate|0|  
|XSLT|1|  
|XPATH|2|  
|合併式|3|  
|Diff|4|  
|修補|5|  
  
 `SourceType`、`SecondOperandType` 和 `XPathSourceType` 屬性 — 使用來自 `DTSXMLSourceType` 列舉的值加以設定。  
  
|DTSXMLSourceType 中的易記名稱|數值|  
|---------------------------------------|-------------------|  
|FileConnection|0|  
|變數|1|  
|DirectInput|2|  
  
 `DestinationType` 並**DiffGramDestinationType**屬性 — 使用中的值設定`DTSXMLSaveResultTo`列舉型別。  
  
|DTSXMLSaveResultTo 中的易記名稱|數值|  
|-----------------------------------------|-------------------|  
|FileConnection|0|  
|變數|1|  
  
 `ValidationType` 屬性 — 使用來自值來設定`DTSXMLValidationType`列舉型別。  
  
|DTSXMLValidationType 中的易記名稱|數值|  
|-------------------------------------------|-------------------|  
|DTD|0|  
|XSD|1|  
  
 `XPathOperation` 屬性 — 使用來自值來設定`DTSXMLXPathOperation`列舉型別。  
  
|DTSXMLXPathOperation 中的易記名稱|數值|  
|-------------------------------------------|-------------------|  
|Evaluation|0|  
|值|1|  
|NodeList|2|  
  
 `DiffOptions` 屬性 — 使用來自值來設定`DTSXMLDiffOptions`列舉型別。 此列舉值中的選項不會互斥。 若要使用多個選項，請提供要套用之選項的逗號分隔清單。  
  
|DTSXMLDiffOptions 中的易記名稱|數值|  
|----------------------------------------|-------------------|  
|無|0|  
|IgnoreChildOrder|1|  
|IgnoreComments|2|  
|IgnorePI|4|  
|IgnoreWhitespace|8|  
|IgnoreNamespaces|16|  
|IgnorePrefixes|32|  
|IgnoreXmlDecl|64|  
|IgnoreDtd|128|  
  
 `DiffAlgorithm` 屬性 — 使用來自值來設定`DTSXMLDiffAlgorithm`列舉型別。  
  
|DTSXMLDiffAlgorithm 中的易記名稱|數值|  
|------------------------------------------|-------------------|  
|Auto|0|  
|快速|1|  
|精確|2|  
  
##  <a name="MaintenancePlanTasks"></a> 維護計畫工作  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含一組工作，用以執行要在維護計畫和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝中使用的 SQL Server 工作。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支援以程式設計方式處理這些工作，而且程式設計參考文件集也不包括這些工作及其列舉值的 API 文件集。  
  
### <a name="all-maintenance-tasks"></a>所有維護工作  
 所有維護工作都使用下列列舉來設定指定的屬性。  
  
 `DatabaseSelectionType` 屬性 — 使用來自值來設定`DatabaseSelection`列舉型別。  
  
|DatabaseSelection 中的易記名稱|數值|  
|----------------------------------------|-------------------|  
|無|0|  
|All|1|  
|系統|2|  
|使用者|3|  
|Specific|4|  
  
 `TableSelectionType` 屬性 — 使用來自值來設定`TableSelection`列舉型別。  
  
|TableSelection 中的易記名稱|數值|  
|-------------------------------------|-------------------|  
|無|0|  
|All|1|  
|Specific|2|  
  
 `ObjectTypeSelection` 屬性 — 使用來自值來設定`ObjectType`列舉型別。  
  
|ObjectType 中的易記名稱|數值|  
|---------------------------------|-------------------|  
|Table|0|  
|檢視|1|  
|TableView|2|  
  
### <a name="back-up-database-task"></a>備份資料庫工作  
 `DestinationCreationType` 屬性 — 使用來自值來設定`DestinationType`列舉型別。  
  
|DestinationType 中的易記名稱|數值|  
|--------------------------------------|-------------------|  
|Auto|0|  
|手動|1|  
  
 `ExistingBackupsAction` 屬性 — 使用來自值來設定`ActionForExistingBackups`列舉型別。  
  
|ActionForExistingBackups 中的易記名稱|數值|  
|-----------------------------------------------|-------------------|  
|附加|0|  
|Overwrite|1|  
  
 `BackupAction` 屬性 — 使用來自值來設定`BackupTaskType`列舉型別。 此屬性可搭配`BackupIsIncremental`屬性來定義工作執行的備份類型。  
  
|BackupTaskType 中的易記名稱|數值|  
|-------------------------------------|-------------------|  
|[資料庫]|0|  
|檔案|1|  
|Log|2|  
  
 `BackupDevice` 屬性 ─ 使用來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件 (SMO) `DeviceType` 列舉的值加以設定。  
  
|DeviceType 中的易記名稱|數值|  
|---------------------------------|-------------------|  
|LogicalDevice|0|  
|磁帶|1|  
|檔案|2|  
|Pipe|3|  
|VirtualDevice|4|  
  
### <a name="maintenance-cleanup-task"></a>維護清除工作  
 `FileTypeSelected` 屬性 — 使用來自值來設定`FileType`列舉型別。  
  
|FileType 中的易記名稱|數值|  
|-------------------------------|-------------------|  
|FileBackup|0|  
|FileReport|1|  
  
 `OlderThanTimeUnitType` 屬性 — 使用來自值來設定`TimeUnitType`列舉型別。  
  
|TimeUnitType 中的易記名稱|數值|  
|-----------------------------------|-------------------|  
|Day|0|  
|週|1|  
|Month|2|  
|Year|3|  
  
### <a name="update-statistics-task"></a>更新統計資料工作  
 `UpdateType` 屬性 ─ 使用來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件 (SMO) `StatisticsTarget` 列舉的值加以設定。  
  
|StatisticsTarget 中的易記名稱|數值|  
|---------------------------------------|-------------------|  
|「資料行」|1|  
|索引|2|  
|All|3|  
  
##  <a name="CommonProperties"></a> 通用屬性  
 封裝、工作以及「Foreach 迴圈」、「For 迴圈」和「時序」等容器可以使用下列列舉來設定指定的屬性。  
  
 `ForceExecutionResult` 屬性 — 使用來自值來設定`DTSForcedExecResult`列舉型別。  
  
|DTSForcedExecResult 中的易記名稱|數值|  
|------------------------------------------|-------------------|  
|無|-1|  
|成功|0|  
|失敗|1|  
|Completion|2|  
  
 `IsolationLevel` 屬性 — 使用來自 .NET Framework `IsolationLevel` 列舉的值加以設定。 如需詳細資訊，請參閱 [MSDN Library](http://go.microsoft.com/fwlink?LinkId=17313)中的＜.NET Framework 類別庫＞。  
  
 `LoggingMode` 屬性 — 使用來自值來設定`DTSLoggingMode`列舉型別。  
  
|DTSLoggingMode 中的易記名稱|數值|  
|-------------------------------------|-------------------|  
|UseParentSetting|0|  
|已啟用|1|  
|已停用|2|  
  
 `TransactionOption` 屬性 — 使用來自值來設定`DTSTransactionOption`列舉型別。  
  
|DTSTransactionOption 中的易記名稱|數值|  
|-------------------------------------------|-------------------|  
|NotSupported|0|  
|支援|1|  
|必要項|2|  
  
## <a name="related-tasks"></a>相關工作  
 [新增或變更屬性運算式](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a>另請參閱  
 [在封裝中使用屬性運算式](use-property-expressions-in-packages.md)   
 [Integration Services &#40;SSIS&#41;封裝](../integration-services-ssis-packages.md)   
 [Integration Services 容器](../control-flow/integration-services-containers.md)   
 [Integration Services 工作](../control-flow/integration-services-tasks.md)   
 [優先順序條件約束](../control-flow/precedence-constraints.md)  
  
  
