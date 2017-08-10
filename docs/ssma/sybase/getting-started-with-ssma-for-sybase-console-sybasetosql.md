---
title: "開始使用 SSMA for Sybase 主控台 (SybaseToSQL) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
caps.latest.revision: 22
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 239b7a8f4dbc3069e67d680b319bf426a0f917e6
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma-for-sybase-console-sybasetosql"></a>開始使用 SSMA for Sybase 主控台 (SybaseToSQL)
本章節描述的程序啟動並開始使用 Sybase 主控台應用程式。 亦會使用的慣例典型的 SSMA 主控台輸出視窗中。  
  
## <a name="launching-ssma-console"></a>啟動 SSMA 主控台  
若要啟動 SSMA 主控台應用程式中使用下列步驟：  
  
1.  移至 開始，並指向 所有程式。  
  
2.  按一下**SQL Server 移轉小幫手的 Sybase 命令提示字元**捷徑。  
  
    它會顯示 [SSMA 主控台使用方式] 功能表和`(/? Help)`，以協助您開始使用主控台應用程式。  
  
## <a name="procedure-for-using-the-ssma-console"></a>針對使用 SSMA 主控台的程序  
Windows 系統上已成功啟動主控台之後，您可以在 bob_ws 上工作使用下列步驟：  
  
1.  透過指令碼檔案中設定 SSMA 主控台。 如需有關本章節的詳細資訊，請參閱[建立指令碼檔案 &#40;SybaseToSQL &#41;](../../ssma/sybase/creating-script-files-sybasetosql.md) .  
  
2.  [建立變數值的檔案 &#40;SybaseToSQL &#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [建立伺服器連接檔案 &#40;SybaseToSQL &#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [執行 SSMA 主控台 &#40;SybaseToSQL &#41;](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md)根據您的專案需求  
  
其他功能：  
  
1.  [指定密碼](http://msdn.microsoft.com/en-us/9b6a70f9-6840-4140-a059-bb7bd7ccc67c)及匯出 / 匯入其他視窗機器  
  
2.  [產生報告](http://msdn.microsoft.com/en-us/19278f6a-6d58-4867-9d71-c6228040466e)以檢視詳細的 xml 輸出評估 /conversion 和資料移轉的報表。 詳細的錯誤報表也可以產生重新整理] 和 [同步處理的命令。  
  
## <a name="ssma-console-output-conventions"></a>SSMA 主控台輸出慣例  
時執行的 SSMA 指令碼命令和選項，主控台程式會在主控台上對使用者顯示的結果和訊息 （資訊、 錯誤等），或如果需要，重新導向至 xml 輸出檔。 在輸出訊息的每個型別被以獨特的色彩。 例如，白色文字訊息表示指令碼檔案的命令;綠色中的一個代表提示使用者輸入，依此類推。  
  
![SSMAConsoleOutput_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "SSMAConsoleOutput_Sybase")  
  
下表中的主控台輸出的色彩解譯：  
  
|Color|Description|  
|---------|---------------|  
|紅色|執行期間發生嚴重錯誤|  
|灰色|日期和時間戳記，訊息給使用者|  
|白色|編寫指令碼檔案的命令、 訊息類型|  
|黃色|警告|  
|綠色|提示使用者輸入|  
|11：青色|開始、 完成和作業的結果。|  
  
## <a name="see-also"></a>另請參閱  
[安裝 SSMA for Sybase &#40;SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
  
