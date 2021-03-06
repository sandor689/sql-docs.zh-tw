---
title: 授與預存程序的權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], permissions
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4e811af7aa55fc6ced619d1a69347867bf2aef05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150399"
---
# <a name="grant-permissions-on-a-stored-procedure"></a>授與預存程序的權限
  本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中授與預存程序的權限。 權限可以授與資料庫中現有的使用者、資料庫角色或應用程式角色。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **使用下列方法授與預存程序的權限：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   您無法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 授與系統程序或系統函數的權限。 請改用 [GRANT 物件權限](/sql/t-sql/statements/grant-object-permissions-transact-sql) 。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 同意授權者 (或是指定了 AS 選項的主體) 必須具有指定了 GRANT OPTION 的權限本身，或是具有隱含目前正在授與權限的更高權限。 需要程序所屬結構描述的 ALTER 權限，或程序的 CONTROL 權限。 如需詳細資訊，請參閱 [GRANT 物件權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)中授與預存程序的權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>若要授與預存程序的權限  
  
1.  在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。  
  
2.  依序展開 **[資料庫]**、程序所屬的資料庫，以及 **[可程式性]**。  
  
3.  展開 [預存程序]，以滑鼠右鍵按一下要授與權限的程序，然後按一下 [屬性]。  
  
4.  在 **[預存程序屬性]** 上選取 **[權限]** 頁面。  
  
5.  若要將權限授與使用者、資料庫角色或應用程式角色，請按一下 **[搜尋]**。  
  
6.  在 **[選取使用者或角色]** 中，按一下 **[物件類型]** ，以加入或清除想要的使用者和角色。  
  
7.  按一下 **[瀏覽]** 顯示使用者或角色的清單。 選取要獲得權限授與的使用者或角色。  
  
8.  在 **[明確權限]** 方格中，選取要授與指定使用者或角色的權限。 如需權限的說明，請參閱 [權限 &#40;Database Engine&#41;](../security/permissions-database-engine.md)。  
  
 選取 **[授與]** 表示要將指定的權限提供給被授與者。 選取 **[可授與]** 則表示授與者也能夠將指定的權限授與給其他主體。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a>若要授與預存程序的權限  
  
1.  連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。 此範例會將預存程序 `EXECUTE` 的 `HumanResources.uspUpdateEmployeeHireInfo` 權限授與名為 `Recruiting11`的應用程式角色。  
  
```tsql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)   
 [GRANT 物件權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)   
 [建立預存程序](../stored-procedures/create-a-stored-procedure.md)   
 [修改預存程序](modify-a-stored-procedure.md)   
 [刪除預存程序](../stored-procedures/delete-a-stored-procedure.md)   
 [重新命名預存程序](rename-a-stored-procedure.md)  
  
  
