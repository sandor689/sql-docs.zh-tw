---
title: "建立、 改變和移除預設值 |Microsoft 文件"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e79fad6e2c3e241c665a6869695e56aaed4d9158
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="creating-altering-and-removing-defaults"></a>建立、改變和移除預設值
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]在[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理物件 (SMO) 的預設條件約束由<xref:Microsoft.SqlServer.Management.Smo.Default>物件。  
  
 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Default> 屬性可用於設定要插入的值。 這可以是常數，或傳回常數值的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，例如 GETDATE()。 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 屬性無法藉由 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法進行修改， 反而必須將 <xref:Microsoft.SqlServer.Management.Smo.Default> 物件卸除，然後重新建立。  
  
## <a name="example"></a>範例  
 如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。 如需詳細資訊，請參閱[建立 Visual C# 35。在 Visual Studio.NET 中的 SMO 專案](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a>在 Visual Basic 中建立、改變和移除預設值  
 此程式碼範例示範如何建立一個純文字的預設值，以及另一個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式的預設值。 預設值必須使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法附加到資料行，並使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法卸離。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a Default object variable by supplying the parent database and the default name 
'in the constructor.
Dim def As [Default]
def = New [Default](db, "Test_Default2")
'Set the TextHeader and TextBody properties that define the default.
def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"
def.TextBody = "GetDate()"
'Create the default on the instance of SQL Server.
def.Create()
'Declare a Column object variable and reference a column in the AdventureWorks2012 database.
Dim col As Column
col = db.Tables("SpecialOffer", "Sales").Columns("StartDate")
'Bind the default to the column.
def.BindToColumn("SpecialOffer", "StartDate", "Sales")
'Unbind the default from the column and remove it from the database.
def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")
def.Drop()
```
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a>在 Visual C# 中建立、改變和移除預設值  
 此程式碼範例示範如何建立一個純文字的預設值，以及另一個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式的預設值。 預設值必須使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法附加到資料行，並使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法卸離。  
  
```csharp  
{  
  
          Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database  db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Default object variable by supplying the parent database and the default name   
            //in the constructor.   
            Default def = new Default(db, "Test_Default2");  
  
            //Set the TextHeader and TextBody properties that define the default.   
            def.TextHeader = "CREATE DEFAULT [Test_Default2] AS";  
            def.TextBody = "GetDate()";  
  
            //Create the default on the instance of SQL Server.   
            def.Create();  
  
            //Bind the default to a column in a table in AdventureWorks2012  
            def.BindToColumn("SpecialOffer", "StartDate", "Sales");  
  
            //Unbind the default from the column and remove it from the database.   
            def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales");  
            def.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-default-in-powershell"></a>在 PowerShell 中建立、改變和移除預設值  
 此程式碼範例示範如何建立一個純文字的預設值，以及另一個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式的預設值。 預設值必須使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法附加到資料行，並使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法卸離。  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
#Define a Default object variable by supplying the parent database and the default name in the constructor.  
$def = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Default `  
-argumentlist $db, "Test_Default2"  
  
#Set the TextHeader and TextBody properties that define the default.   
$def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"  
$def.TextBody = "GetDate()"  
  
#Create the default on the instance of SQL Server.   
$def.Create()  
  
#Bind the default to the column.   
$def.BindToColumn("SpecialOffer", "StartDate", "Sales")  
  
#Unbind the default from the column and remove it from the database.   
$def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")  
$def.Drop()  
```  
  
## <a name="see-also"></a>請參閱＜  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
  
  