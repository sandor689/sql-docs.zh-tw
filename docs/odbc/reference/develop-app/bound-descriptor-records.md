---
title: 繫結描述元記錄 |Microsoft 文件
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
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ac161220673c32f13c08ab7588c269237b5aa6f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907565"
---
# <a name="bound-descriptor-records"></a>繫結描述元記錄
當應用程式設定 SQL_DESC_DATA_PTR 欄位的描述項記錄，使其不再包含 null 值時，即為記錄*繫結*。  
  
 如果描述元 APD，每個繫結的記錄構成繫結的參數。 輸入參數，應用程式必須繫結參數，以針對每個動態參數標記，在執行陳述式之前的 SQL 陳述式。 輸出參數的應用程式需要繫結參數。  
  
 如果描述元 ARD，描述資料庫資料的資料列，每個繫結的記錄構成繫結的資料行。
