---
title: getCharacterStream 方法 (long，long) (SQLServerNClob) |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5a8028bc-c877-4668-b662-0746d462040e
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d54808511d4bdfe6c464cd6deee989757521266
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32831623"
---
# <a name="getcharacterstream-method-long-long-sqlservernclob"></a>getCharacterStream 方法 (long, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取**NCLOB**資料做為**讀取器**物件或字元的指定的位置和長度的資料流。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                  long length)  
```  
  
#### <a name="parameters"></a>參數  
 *pos*  
  
 A**長**，表示要擷取之部分值的第一個字元的位移。  
  
 *長度*  
  
 A**長**，表示要擷取之部分值的字元長度。  
  
## <a name="return-value"></a>傳回值  
 讀取器物件，其中包含**NCLOB**資料。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 GetCharacterStream 方法 java.sql.NClob 介面中所指定這個 getCharacterStream 方法。  
  
## <a name="see-also"></a>另請參閱  
 [getCharacterStream 方法&#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [SQLServerNClob 方法](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob 成員](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob 類別](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
