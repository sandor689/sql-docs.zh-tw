---
title: "卸除預設值 (TRANSACT-SQL) |Microsoft 文件"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_DEFAULT_TSQL
- DROP DEFAULT
dev_langs:
- TSQL
helpviewer_keywords:
- DROP DEFAULT statement
- defaults [SQL Server], removing
ms.assetid: d2d3af25-8877-46ba-95d9-1844961d97ee
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cb7de5514d74ed4650d44bed145c32e9bea2c845
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="drop-default-transact-sql"></a>DROP DEFAULT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  從目前資料庫移除一或多個使用者自訂的預設值。  
  
> [!IMPORTANT]  
>  將移除 DROP DEFAULT 的下一版[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 請勿在新的開發工作中使用 DROP DEFAULT，並規劃修改目前使用 DROP DEFAULT 的應用程式。 請改用 default 定義，您可以使用 DEFAULT 關鍵字建立[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)或[CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
DROP DEFAULT [ IF EXISTS ] { [ schema_name . ] default_name } [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>引數  
 *如果存在*  
 **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。  
  
 只有當它已經存在有條件地卸除預設值。  
  
 *schema_name*  
 這是預設值所屬的結構描述名稱。  
  
 *default_name*  
 這是現有預設值的名稱。 若要查看存在的預設值的清單，請執行**sp_help**。 預設值必須符合的規則[識別碼](../../relational-databases/databases/database-identifiers.md)。 您可以選擇性地指定預設結構描述名稱。  
  
## <a name="remarks"></a>備註  
 先卸除預設值解除繫結預設值執行**sp_unbindefault**如果預設值目前繫結到資料行或別名資料類型。  
  
 在從允許 Null 值的資料行中卸除預設值之後，當加入資料列且未明確提供值時，會在這個位置插入 NULL。 從 NOT NULL 資料行中卸除預設值之後，當加入資料列且未明確提供值時，會傳回錯誤訊息。 稍後，會做為一般 INSERT 陳述式行為的一部份而加入這些資料列。  
  
## <a name="permissions"></a>Permissions  
 若要執行 DROP DEFAULT，使用者至少必須有預設值所屬結構描述的 ALTER 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-dropping-a-default"></a>A. 卸除預設值  
 如果預設值尚未繫結到資料行或別名資料類型，只能利用 DROP DEFAULT 來卸除它。 下列範例會移除名稱為 `datedflt` 的使用者建立預設值。  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.objects  
         WHERE name = 'datedflt'   
            AND type = 'D')  
   DROP DEFAULT datedflt;  
GO  
```  
  
 開頭為[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]您可以使用下列語法。  
  
```  
DROP DEFAULT IF EXISTS datedflt;  
GO  
```  
  
### <a name="b-dropping-a-default-that-has-been-bound-to-a-column"></a>B. 卸除已繫結到資料行的預設值  
 下列範例會將預設值和相關聯之 `EmergencyContactPhone` 資料表的 `Contact` 資料行解除繫結，再卸除名稱為 `phonedflt` 的預設值。  
  
```  
USE AdventureWorks2012;  
GO  
   BEGIN   
      EXEC sp_unbindefault 'Person.Contact.Phone'  
      DROP DEFAULT phonedflt  
   END;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_unbindefault &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)  
  
  
