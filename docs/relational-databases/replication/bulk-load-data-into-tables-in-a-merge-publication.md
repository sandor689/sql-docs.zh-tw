---
title: "將資料大量載入合併式發行集中的資料表 | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cbcbfedbd5b2296da2cb266bf78ca3f7db9760ac
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="bulk-load-data-into-tables-in-a-merge-publication"></a>將資料大量載入合併式發行集中的資料表
  使用 [bcp Utility](../../tools/bcp-utility.md) 或 [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) 命令將資料載入資料表時，根據預設不會引發在 [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) 系統資料表中維護追蹤資料的合併式複寫觸發程序。 您可以在資料載入時強制引發合併式複寫觸發程序，或者使用複寫預存程序，以程式設計的方式在大量複製作業之後插入產生的複寫中繼資料。  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a>使用 bcp 公用程式將資料大量載入合併式發行集所發行的資料表  
  
1.  在「發行者」或「訂閱者」端執行 [bcp Utility](../../tools/bcp-utility.md) 或 [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) ，將資料插入至使用合併式複寫所發行的資料表。  
  
2.  使用下列其中一個方法，確保會針對插入的資料產生複寫中繼資料。  
  
    -   使用 FIRE_TRIGGERS 選項執行大量複製。  
  
    -   在插入資料的資料庫上，執行 [sp_addtabletocontents &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql.md)。 指定要在其中插入 **@table_name**。  
  
  