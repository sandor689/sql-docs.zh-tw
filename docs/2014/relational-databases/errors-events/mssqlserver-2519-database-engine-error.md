---
title: MSSQLSERVER_2519 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3262e6bbb1c78bc7c4f504cd9d102687c16b6afa
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431787"
---
# <a name="mssqlserver2519"></a>MSSQLSERVER_2519
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|2519|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DBCC_NO_EXPRESSION_EVALUATOR|  
|訊息文字|無法檢查物件識別碼 O_ID (物件 "O_NAME") 的計算資料行和使用者自訂類型，因為內部運算式評估工具無法初始化。|  
  
## <a name="explanation"></a>說明  
 這項參考用訊息指出查詢處理器無法提供 DBCC 與內部物件，以便評估計算資料行和 Common Language Runtime (CLR) 使用者自訂類型。 這表示 DBCC 不會在檢查索引和基底資料表的一致性時檢查計算資料行和 CLR 使用者自訂類型的正確性，或是使用這些使用者自訂類型。  
  
## <a name="user-action"></a>使用者動作  
 無  
  
## <a name="see-also"></a>另請參閱  
 [MSSQLSERVER_2518](mssqlserver-2518-database-engine-error.md)  
  
  
