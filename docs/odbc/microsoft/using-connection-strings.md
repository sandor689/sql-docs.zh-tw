---
title: 使用連接字串 |Microsoft 文件
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
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 014c3cf66d18ab0b859c98e96584e73e160a6e63
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905684"
---
# <a name="using-connection-strings"></a>使用連接字串
您可以使用的連接字串連接至 Visual FoxPro 資料來源。  
  
 例如，若要連接的 TasTrade 資料來源和覆寫目前專有的設定相關聯的資料來源，您會使用字串：  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 如需屬性的關鍵字，您可以在連接字串中包含的值，請參閱[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)。  
  
 如需連接字串語法的完整說明，請參閱[SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md)中*ODBC 程式設計人員參考*。
