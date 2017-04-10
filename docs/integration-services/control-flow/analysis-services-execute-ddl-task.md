---
title: "Analysis Services 執行 DDL 工作 | Microsoft Docs"
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
  - "sql13.dts.designer.asexecuteddltask.f1"
helpviewer_keywords: 
  - "Analysis Services 執行 DDL 工作"
  - "DDL"
ms.assetid: 7f25c8c6-b601-41f2-9553-be0a2ee0751a
caps.latest.revision: 48
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 48
---
# Analysis Services 執行 DDL 工作
  「[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行 DDL」工作會執行可建立、卸除或修改採礦模型和多維度物件 (如 Cube 和維度) 的資料定義語言 (DDL) 陳述式。 例如，DDL 陳述式可在 **Adventure Works** Cube 中建立資料分割，或在 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中所含的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 範例資料庫) 中刪除維度。  
  
 「[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行 DDL」工作會使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連接管理員連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案。 如需相關資訊，請參閱 [Analysis Services Connection Manager](../../integration-services/connection-manager/analysis-services-connection-manager.md)。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包括多項執行商業智慧作業的工作，例如處理分析物件和執行資料採礦預測查詢。  
  
 如需有關相關之商業智慧工作的詳細資訊，請按下列其中一個主題：  
  
-   [Analysis Services 處理工作](../../integration-services/control-flow/analysis-services-processing-task.md)  
  
-   [資料採礦查詢工作](../../integration-services/control-flow/data-mining-query-task.md)  
  
## DDL 陳述式  
 DDL 陳述式會在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 指令碼語言 (ASSL) 中以陳述式的方式呈現，在 XML for Analysis (XMLA) 命令中則會加上框架。  
  
-   ASSL 是用來定義和描述 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體，及其包含的資料庫和資料庫物件。 如需詳細資訊，請參閱 [Analysis Services 指令碼語言 &#40;ASSL&#41; 參考 ](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)。  
  
-   XMLA 為命令語言，用來傳送動作命令 (如「建立」、「改變」或「處理」) 至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體。 如需詳細資訊，請參閱 [XML for Analysis &#40;XMLA&#41; 參考](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)。  
  
 如果 DDL 程式碼存放在另一個檔案中，「[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行 DDL」工作便會使用「檔案」連線管理員指定該檔案的路徑。 如需相關資訊，請參閱 [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md)。  
  
 由於 DDL 陳述式可能包含密碼和其他機密資訊，因此包含一或多項「[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行 DDL」工作的封裝應使用封裝保護等級 **EncryptAllWithUserKey** 或 **EncryptAllWithPassword**。 如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 封裝](../../integration-services/integration-services-ssis-packages.md)。  
  
### DDL 範例  
 下列三種 DDL 陳述式由 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中所含的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫) 中的指令碼物件所產生。  
  
 下列 DDL 陳述式會刪除 **Promotion** 維度。  
  
```  
<Delete xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 下列 DDL 陳述式會處理 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] Cube。  
  
```  
<Batch xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 下列 DDL 陳述式會建立**預測**採礦模型。  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
 下列三種 DDL 陳述式由 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中所含的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫) 中的指令碼物件所產生。  
  
 下列 DDL 陳述式會刪除 **Promotion** 維度。  
  
```  
<Delete xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 下列 DDL 陳述式會處理 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] Cube。  
  
```  
<Batch xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 下列 DDL 陳述式會建立**預測**採礦模型。  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
## 設定 Analysis Services 執行 DDL 工作  
 您可以透過「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」或以程式設計方式設定屬性。  
  
 如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：  
  
-   [Analysis Services 執行 DDL 工作編輯器 &#40;一般頁面&#41;](../../integration-services/control-flow/analysis-services-execute-ddl-task-editor-general-page.md)  
  
-   [Analysis Services 執行 DDL 工作編輯器 &#40;DDL 頁面&#41;](../../integration-services/control-flow/analysis-services-execute-ddl-task-editor-ddl-page.md)  
  
-   [運算式頁面](../../integration-services/expressions/expressions-page.md)  
  
 如需在 [[!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師] 中設定這些屬性的詳細資訊，請按一下下列主題：  
  
-   [設定工作或容器的屬性](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## 以程式設計方式設定 Analysis Services 執行 DDL 工作  
 如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.ASExecuteDDLTask>  
  
  