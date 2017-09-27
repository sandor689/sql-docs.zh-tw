---
title: "查詢 Active Directory with the Script Task |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ee5a82829785e78554b105e1f3bf3bd24f05b778
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="querying-the-active-directory-with-the-script-task"></a>以指令碼工作查詢 Active Directory
  企業資料處理應用程式 (例如 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝) 通常需要根據儲存在 Active Directory 中的職等、工作職稱或是員工的其他特色，以不同的方式處理資料。 Active Directory 是[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows 目錄服務，可集中的儲存中繼資料不僅有關使用者，而且還有關電腦與印表機等其他組織資產。 **System.DirectoryServices** Microsoft.NET Framework 中的命名空間提供類別，以使用 Active Directory，可協助您根據它所儲存的資訊的直接資料處理工作流程。  
  
> [!NOTE]  
>  如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。 如需詳細資訊，請參閱 [開發自訂工作](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)。  
  
## <a name="description"></a>Description  
 下列範例根據 `email` 變數值 (包含員工的電子郵件地址)，從 Active Directory 擷取員工的姓名、職稱與電話號碼。 封裝中的優先順序條件約束可以使用擷取的資訊來判斷，例如，根據員工的工作職稱，來判斷要傳送低優先順序的電子郵件訊息或是高優先順序的頁面。  
  
#### <a name="to-configure-this-script-task-example"></a>設定此指令碼工作範例  
  
1.  建立三個字串變數 `email`、`name` 和 `title`。 輸入有效的公司電子郵件地址做為 `email` 變數值。  
  
2.  在**指令碼**頁面**指令碼工作編輯器**，新增`email`變數設為**[readonlyvariables]**屬性。  
  
3.  新增`name`和`title`變數**[readwritevariables]**屬性。  
  
4.  在指令碼專案中，加入的參考**System.DirectoryServices**命名空間。  
  
5.  執行個體時提供 SQL Server 登入。 在程式碼中，使用**匯入**陳述式匯入**DirectoryServices**命名空間。  
  
> [!NOTE]  
>  若要順利執行這個指令碼，您的公司必須在其網路上使用 Active Directory，並儲存這個範例所使用的員工資訊。  
  
### <a name="code"></a>程式碼  
  
```vb  
Public Sub Main()  
  
    Dim directory As DirectoryServices.DirectorySearcher  
    Dim result As DirectoryServices.SearchResult  
    Dim email As String  
  
    email = Dts.Variables("email").Value.ToString  
  
    Try  
        directory = New _  
            DirectoryServices.DirectorySearcher("(mail=" & email & ")")  
        result = directory.FindOne  
        Dts.Variables("name").Value = _  
            result.Properties("displayname").ToString  
        Dts.Variables("title").Value = _  
            result.Properties("title").ToString  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
public void Main()  
{  
    //  
    DirectorySearcher directory;  
    SearchResult result;  
    string email;  
  
    email = (string)Dts.Variables["email"].Value;  
  
    try  
    {  
        directory = new DirectorySearcher("(mail=" + email + ")");  
        result = directory.FindOne();  
        Dts.Variables["name"].Value = result.Properties["displayname"].ToString();  
        Dts.Variables["title"].Value = result.Properties["title"].ToString();  
        Dts.TaskResult = (int)ScriptResults.Success;  
    }  
    catch (Exception ex)  
    {  
        Dts.Events.FireError(0, "Script Task Example", ex.Message + "\n" + ex.StackTrace, String.Empty, 0);  
        Dts.TaskResult = (int)ScriptResults.Failure;  
    }  
  
}  
```  
  
## <a name="external-resources"></a>外部資源  
  
-   技術文件：[在 SSIS 中處理 Active Directory 資訊](http://go.microsoft.com/fwlink/?LinkId=199588)，social.technet.microsoft.com 上的  
  
  