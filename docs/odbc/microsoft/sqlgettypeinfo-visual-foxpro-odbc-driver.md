---
title: SQLGetTypeInfo （Visual FoxPro ODBC 驅動程式） |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9bbf3983ccdeb2c320f4776d608b73e362f0a479
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904303"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo （Visual FoxPro ODBC 驅動程式）
> [!NOTE]  
>  本主題包含 Visual FoxPro ODBC 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支援： 完整  
  
 ODBC 應用程式開發介面相容性： 層級 1  
  
 傳回的資料來源所支援的資料類型的相關資訊。 驅動程式會傳回 SQL 結果集內的資訊。 下表列出 ODBC 資料類型和對應的 Visual FoxPro 資料型別。  
  
|ODBC 類型|Visual FoxPro 類型|  
|---------------|------------------------|  
|SQL_BIGINT|不支援。 沒有 64 位元 Visual FoxPro 型別。|  
|SQL_BIT|邏輯|  
|SQL_CHAR|字元|  
|SQL_DATE|日期|  
|SQL_DECIMAL|數值|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Integer|  
|SQL_LONGVARBINARY|備忘 （二進位）|  
|SQL_LONGVARCHAR|備忘錄|  
|SQL_NUMERIC|數字 *，貨幣、 Float|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Integer|  
|SQL_TIME|不支援。 沒有任何 Visual FoxPro*時間*型別。|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Integer|  
|SQL_VARBINARY|備忘 （二進位） *、 一般|  
|SQL_VARCHAR|字元|  
  
 * 預設類型  
  
 如需 Visual FoxPro 資料類型的詳細資訊，請參閱[CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)。 如需此函式的詳細資訊，請參閱[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)中*ODBC 程式設計人員參考*。
