---
title: Dbmslpcn.dll 共用記憶體中的 ConnectionValidSharedMemory 函式 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6ae35826-7d75-4542-b686-5f79316b6157
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 9eb72ca108c6f4d01626d75f5dc3ad8e8354fad1
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39537088"
---
# <a name="connectionvalidsharedmemory-function-in-dbmslpcndll-shared-memory"></a>dbmslpcn.dll 共用記憶體中的 ConnectionValidSharedMemory 函式
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  此函式決定 SQL Server 共用記憶體是否已安裝並作用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
BOOL ConnectionValidSharedMemory(char * szServerName);  
```  
  
## <a name="parameters"></a>參數  
 *szServerName*  
  
-   類型： **char\***  
  
-   SQL server 的名稱。  
  
## <a name="return-value"></a>傳回值  
 類型： **BOOL**  
  
 傳回 0，如果不正確;否則會傳回非零值。  
  
  
