---
title: JDBC 驅動程式管理結果集 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6e428a66a506005cdbde4fbc58b724e8b22972ab
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32829883"
---
# <a name="managing-result-sets-with-the-jdbc-driver"></a>使用 JDBC 驅動程式管理結果集
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  結果集代表從資料來源傳回的一組資料，通常是作為查詢的結果。 結果集包含用來保留所要求之資料元素的資料列和資料行，它是以資料指標來導覽。 結果集可以更新，這表示它可加以修改，並將那些修改發送到原始資料來源。 結果集對於基礎資料來源中的變更，也可以有不同的敏感性層級。  
  
 結果集的類型決定陳述式建立時，就會呼叫這個[createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)方法[SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)類別。 結果集的基礎角色是要提供 Java 應用程式可用的資料庫資料表示法。 這一點通常是以對結果集資料元素使用具類型的 getter 和 setter 方法來完成。  
  
 在下列範例中，根據[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]範例資料庫中，結果集藉由呼叫建立[executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)方法[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)類別。 從結果集中的資料即會顯示使用[getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)方法[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)類別。  
  
 [!code[JDBC#ManagingResultSets1](../../connect/jdbc/codesnippet/Java/managing-result-sets-with-t_1.java)]  
  
 本節的主題說明結果集使用方式的各方面，包括資料指標類型、並行性和資料列鎖定。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|Description|  
|-----------|-----------------|  
|[了解資料指標類型](../../connect/jdbc/understanding-cursor-types.md)|描述不同資料指標類型[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]支援。|  
|[瞭解並行控制](../../connect/jdbc/understanding-concurrency-control.md)|描述 JDBC Driver 支援並行控制的方式。|  
|[了解資料列鎖定](../../connect/jdbc/understanding-row-locking.md)|描述 JDBC 驅動程式支援資料列鎖定的方式。|  
  
## <a name="see-also"></a>另請參閱  
 [JDBC Driver 概觀](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
