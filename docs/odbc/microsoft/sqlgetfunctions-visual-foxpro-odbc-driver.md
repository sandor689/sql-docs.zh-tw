---
title: SQLGetFunctions （Visual FoxPro ODBC 驅動程式） |Microsoft 文件
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
- SQLGetFunctions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8102932a-88b3-49d8-bf7a-c766f54878c0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc3350e8b6a7a4ddcf505fed14a056422cbbbe41
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904773"
---
# <a name="sqlgetfunctions-visual-foxpro-odbc-driver"></a>SQLGetFunctions （Visual FoxPro ODBC 驅動程式）
> [!NOTE]  
>  本主題包含 Visual FoxPro ODBC 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支援： 完整  
  
 ODBC 應用程式開發介面相容性： 層級 1  
  
 傳回所有支援的函式，則為 TRUE。  
  
 Visual FoxPro ODBC 驅動程式支援所有 ODBC API Core 和層級 1 的函式。 下表指出驅動程式是否支援特定的層級 2 函式。  
  
|*函數*|Supported|  
|----------------|---------------|  
|SQL_API_SQLBROWSECONNECT|否|  
|SQL_API_SQLCOLUMNPRIVELEGES|否|  
|SQL_API_SQLDATASOURCES|是|  
|SQL_API_SQLDESCRIBEPARAM|否|  
|SQL_API_SQLDRIVERS|是|  
|SQL_API_SQLEXTENDEDFETCH|是|  
|SQL_API_SQLFOREIGNKEYS|否|  
|SQL_API_SQLMORERESULTS|是|  
|SQL_API_SQLNATIVESQL|否|  
|SQL_API_SQLNUMPARAMS|是|  
|SQL_API_SQLPARAMOPTIONS|是|  
|SQL_API_SQLPRIMARYKEYS|是|  
|SQL_API_SQLPROCEDURECOLUMNS|否|  
|SQL_API_SQLPROCEDURES|否|  
|SQL_API_SQLSETPOS|是|  
|SQL_API_SQLSETSCROLLOPTIONS|是|  
|SQL_API_SQLTABLEPRIVILEGES|否|  
  
 如需詳細資訊，請參閱[SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md)中*ODBC 程式設計人員參考*。
