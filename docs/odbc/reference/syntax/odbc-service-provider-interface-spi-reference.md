---
title: ODBC 服務提供者介面 (SPI) 參考 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c909e38e1aa4ee78412c7025cb6ed53254e98d0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916373"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>ODBC 服務提供者介面 (SPI) 參考
傳統上，ODBC 定義應用程式開發介面 (API)。 應用程式可以呼叫 API 中的函式，所以應該實作驅動程式管理員和驅動程式內部。  
  
 加上的可感知驅動程式的連接集區的功能，ODBC 導入了服務提供者介面 (SPI)。 SPI 中的函式可用來驅動程式管理員與驅動程式之間的通訊。 SPI 函式的實作驅動程式。驅動程式管理員不會公開給應用程式的 SPI 函式。 應用程式不應該直接呼叫這些函式。  
  
 包含 sqlspi.h ODBC 驅動程式開發。  
  
 本節涵蓋下列主題  
  
-   [SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [SQLGetPoolID](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [SQLPoolConnect](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [SQLSetConnectInfo](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [SQLSetDriverConnectInfo](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>另請參閱  
 [開發 ODBC 驅動程式](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [開發中的 ODBC 驅動程式的連接集區感知](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [驅動程式管理員連接共用](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
