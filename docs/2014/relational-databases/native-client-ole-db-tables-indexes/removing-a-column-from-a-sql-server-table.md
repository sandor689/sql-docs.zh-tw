---
title: 從 SQL Server 資料表中移除資料行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7b5173ad5f617eccf41f8e8d60a81305ff1ca48
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409927"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>從 SQL Server 資料表中移除資料行
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會公開**itabledefinition:: Dropcolumn**函式。 這可讓取用者移除的資料行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料表。  
  
 取用者指定為 Unicode 字元字串中的資料表名稱*pwszName*隸屬*uName*聯集*pTableID*參數。 *EKind*隸屬*pTableID*必須是 DBKIND_NAME。  
  
 取用者表示中的資料行名稱*pwszName*隸屬*uName*聯集*Ekind*參數。 資料行名稱是一個 Unicode 字元字串。 *EKind*隸屬*Ekind*必須是 DBKIND_NAME。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料表和索引](tables-and-indexes.md)  
  
  