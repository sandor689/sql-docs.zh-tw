---
title: 接收多個資料錄集 |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving multiple Recordsets [ADO]
- Recordset object [ADO], receiving multiple Recordsets
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73bf5b086b82f1accdcb34f4e75c4101e324e532
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272257"
---
# <a name="receiving-multiple-recordsets"></a>接收多個資料錄集
[Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)支援傳回多個**資料錄集**物件單一命令，其中包含多個 SQL 陳述式，一個**資料錄集**每個 SQL 陳述式。 順序**資料錄集**會傳回遵照 SQL 陳述式會置於命令文字的順序。  
  
 Microsoft OLE DB Provider for SQL Server 也會傳回多個結果集至 ADO 當命令包含 COMPUTE 子句。 比方說，包含下列 SQL 陳述式的命令時，會在兩個傳回的結果**資料錄集**物件： 一個用於資料列集 (*ProductID*， *ProductName*，*UnitPrice*)，和另一個則用於資料表中的所有產品的平均價格。  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 您可以使用**Recordset.NextRecordset**方法來列舉將兩個物件。  
  
 如需詳細資訊，請參閱[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)。
