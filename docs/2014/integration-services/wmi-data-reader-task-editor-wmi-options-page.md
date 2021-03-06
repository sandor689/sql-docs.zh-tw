---
title: WMI 資料讀取器工作編輯器 （WMI 選項頁面） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
caps.latest.revision: 39
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c4af6d3458cba6e622c117ace4add62127670f13
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152409"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a>WMI 資料讀取器工作編輯器 (WMI 選項頁面)
  使用 [WMI 資料讀取器工作編輯器] 對話方塊的 [WMI 選項] 頁面，來指定 Windows Management Instrumentation 查詢語言 (WQL) 查詢的來源和查詢結果的目的地。  
  
 若要了解這個工作，請參閱＜ [WMI Data Reader Task](control-flow/wmi-data-reader-task.md)＞。 如需 WMI 查詢語言 (WQL) 的詳細資訊，請參閱 MSDN Library 中的 Windows Management Instrumentation 主題： [Querying with WQL](http://go.microsoft.com/fwlink/?LinkId=79045)(使用 WQL 查詢)。  
  
## <a name="static-options"></a>靜態選項  
 **WMIConnectionName**  
 在清單中選取 WMI 連線管理員，或按一下 [\<新增 WMI 連線...>] 建立新的連線管理員。  
  
 **相關主題：**[WMI 連接管理員](connection-manager/wmi-connection-manager.md)、[WMI 連接管理員編輯器](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 選取工作執行之 WQL 查詢的來源類型。 這個屬性具有下表中所列的選項。  
  
|值|描述|  
|-----------|-----------------|  
|**直接輸入**|設定 WQL 查詢的來源。 選取這個值就會顯示 **[WQLQuerySourceType]** 動態選項。|  
|**檔案連接**|選取包含 WQL 查詢的檔案。 選取這個值就會顯示 **[WQLQuerySourceType]** 動態選項。|  
|**變數**|將來源設定為定義 WQL 查詢的變數。 選取這個值就會顯示 **[WQLQuerySourceType]** 動態選項。|  
  
 **OutputType**  
 指定輸出應為資料表、屬性值或屬性名稱和值。  
  
 **OverwriteDestination**  
 指定是要保留、覆寫還是附加至目的地檔案或變數中的原始資料。  
  
 **DestinationType**  
 選取此工作執行之 WQL 查詢的目的地類型。 這個屬性具有下表中所列的選項。  
  
|值|描述|  
|-----------|-----------------|  
|**檔案連接**|選取檔案以儲存 WQL 查詢的結果。 選取此值會顯示動態選項 **[DestinationType]**。|  
|**變數**|設定變數以儲存 WQL 查詢的結果。 選取此值會顯示動態選項 **[DestinationType]**。|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a>WQLQuerySourceType 動態選項  
  
### <a name="wqlquerysourcetype--direct-input"></a>WQLQuerySourceType = 直接輸入  
 **WQLQuerySource**  
 提供查詢，或按一下 [省略符號 (...)]，然後使用 [WQL 查詢] 對話方塊輸入查詢。  
  
### <a name="wqlquerysourcetype--file-connection"></a>WQLQuerySourceType = 檔案連接  
 **WQLQuerySource**  
 在清單中選取檔案連線管理員，或按一下 [\<新增連線...>]，即可建立新的連線管理員。  
  
 **相關主題：** [File Connection Manager](connection-manager/file-connection-manager.md)、 [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysourcetype--variable"></a>WQLQuerySourceType = 變數  
 **WQLQuerySource**  
 在清單中選取變數，或按一下 [\<新增變數...>] 建立新的變數。  
  
 **相關主題**︰[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[加入變數](../../2014/integration-services/add-variable.md)  
  
## <a name="destinationtype-dynamic-options"></a>DestinationType 動態選項  
  
### <a name="destinationtype--file-connection"></a>DestinationType = 檔案連接  
 **目的地**  
 在清單中選取檔案連線管理員，或按一下 [\<新增連線...>]，即可建立新的連線管理員。  
  
 **相關主題：** [File Connection Manager](connection-manager/file-connection-manager.md)、 [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="destinationtype--variable"></a>DestinationType = 變數  
 **目的地**  
 在清單中選取變數，或按一下 [\<新增變數...>] 建立新的變數。  
  
 **相關主題**︰[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[加入變數](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [WMI 資料讀取器工作編輯器&#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md)   
 [運算式頁面](expressions/expressions-page.md)   
 [WMI 事件監看員工作](control-flow/wmi-event-watcher-task.md)  
  
  
