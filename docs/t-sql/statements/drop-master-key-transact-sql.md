---
title: DROP MASTER KEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP MASTER KEY
- DROP_MASTER_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing Database Master Keys
- database master key [SQL Server], removing
- encryption [SQL Server], Database Master Key
- DROP MASTER KEY statement
- cryptography [SQL Server], Database Master Key
- dropping Database Master Keys
- deleting Database Master Keys
ms.assetid: 5ccef797-408f-4964-80da-965d8e1ccba7
caps.latest.revision: 34
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: e967e2b33d2602ef490ae96046db4709cdf03383
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454152"
---
# <a name="drop-master-key-transact-sql"></a>DROP MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  從目前資料庫移除主要金鑰。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
DROP MASTER KEY  
```  
  
## <a name="arguments"></a>引數  
 這個陳述式沒有引數。  
  
## <a name="remarks"></a>Remarks  
 如果資料庫中有任何受主要金鑰保護的私密金鑰，卸除作業便會失敗。  
  
## <a name="permissions"></a>[權限]  
 需要資料庫的 CONTROL 權限。  
  
## <a name="examples"></a>範例  
 下列範例會移除 `AdventureWorks2012` 資料庫的主要金鑰。  
  
```  
USE AdventureWorks2012;  
DROP MASTER KEY;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 下列範例會移除主要金鑰。  
  
```  
USE master;  
DROP MASTER KEY;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [OPEN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-master-key-transact-sql.md)   
 [CLOSE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/close-master-key-transact-sql.md)   
 [BACKUP MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/backup-master-key-transact-sql.md)   
 [RESTORE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-master-key-transact-sql.md)   
 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

