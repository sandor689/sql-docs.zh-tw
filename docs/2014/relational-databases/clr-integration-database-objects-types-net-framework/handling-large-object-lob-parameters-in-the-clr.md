---
title: 處理 CLR 中的大型物件 (LOB) 參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
caps.latest.revision: 20
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f23f42a01ba5268c9165a79f5330fb0efcc538ce
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353230"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>處理 CLR 中的大型物件 (LOB) 參數
  使用 `SqlBytes` 和 `SqlChars` 分別傳遞大型物件 (LOB) 二進位類型 (`varbinary(max)`) 和 LOB 字元類型 (`nvarchar(max)`) 參數。 這些類型允許將 LOB 值從資料庫串流到 Common Language Runtime (CLR) 常式，而非將整個值複製到 Managed 空間。 `SqlBinary` 和 `SqlString` 應該僅用於小型二進位和字元字串值。  
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 的 SQL Server 資料類型](sql-server-data-types-in-the-net-framework.md)  
  
  
