---
title: ASYMKEY_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- AsymKey_ID
- ASYMKEY_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], AsymKey_ID
- ASYMKEY_ID function
- encryption [SQL Server], asymmetric keys
- identification numbers [SQL Server], asymmetric keys
- IDs [SQL Server], asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: d697daf8-2106-4ebb-b09a-ca0be465d747
caps.latest.revision: 22
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 36640012553196f51221924adffbfc54b1cf1c2f
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/04/2018
ms.locfileid: "37787709"
---
# <a name="asymkeyid-transact-sql"></a>ASYMKEY_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

傳回非對稱金鑰的識別碼。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
ASYMKEY_ID ( 'Asym_Key_Name' )  
```  
  
## <a name="arguments"></a>引數  
*Asym_Key_Name*  
資料庫中非對稱金鑰的名稱。
  
## <a name="return-types"></a>傳回類型
 **int**  
  
## <a name="permissions"></a>Permissions  
需要非對稱金鑰上適當的權限，且呼叫端尚未拒絕非對稱金鑰的 VIEW 權限。 如需非對稱金鑰權限的詳細資訊，請參閱 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41; ](../../t-sql/statements/create-asymmetric-key-transact-sql.md)。
  
## <a name="examples"></a>範例  
此範例傳回非對稱金鑰 `ABerglundKey11` 的識別碼。
  
```sql
SELECT ASYMKEY_ID('ABerglundKey11');  
GO  
```  
  
## <a name="see-also"></a>另請參閱
[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
[ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)  
[DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)  
[SIGNBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/signbyasymkey-transact-sql.md)  
[VERIFYSIGNEDBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/verifysignedbyasymkey-transact-sql.md)  
[加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
[sys.asymmetric_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md)  
[安全性目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)  
[ASYMKEYPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/asymkeyproperty-transact-sql.md)  
[KEY_ID &#40;Transact-SQL&#41;](../../t-sql/functions/key-id-transact-sql.md)
  
  
