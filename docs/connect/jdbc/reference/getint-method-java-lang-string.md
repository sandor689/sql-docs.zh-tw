---
title: "getInt 方法 (java.lang.String) |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerCallableStatement.getInt (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1705812f-1f04-4e84-b6c8-d164dded47b3
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 589ceac845495d5f3242aed6d04dbde1c2cd68c0
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="getint-method-javalangstring"></a>getInt 方法 (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取所指定之參數的值**int**在 Java 程式語言中使用給定的參數名稱。  
  
## <a name="syntax"></a>語法  
  
```  
  
public int getInt(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>參數  
 *sCol*  
  
 A**字串**，其中包含參數名稱。  
  
## <a name="return-value"></a>傳回值  
 **Int**值。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 GetInt 方法 java.sql.CallableStatement 介面中所指定此 getInt 方法。  
  
 這個方法僅支援[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]可以安全傳回整數值，例如 int、 smallint、 tinyint 和 bit 資料類型。 對任何其他資料類型使用這個方法，將擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [getInt 方法 &#40;SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getint-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成員](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 類別](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  