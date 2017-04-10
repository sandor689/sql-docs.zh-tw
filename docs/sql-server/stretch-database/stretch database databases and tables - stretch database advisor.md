---
title: "執行 Stretch Database Advisor 以識別 Stretch Database 的資料庫和資料表 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Stretch Database, 識別資料庫"
  - "Stretch Database, 識別資料表"
  - "識別 Stretch Database 的資料庫"
  - "識別 Stretch Database 的資料表"
ms.assetid: 81bd93d8-eef8-4572-88d7-5c37ab5ac2bf
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# 執行 Stretch Database Advisor 以識別 Stretch Database 的資料庫和資料表
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  若要識別屬於 Stretch Database 對象的資料庫和資料表，請下載 SQL Server 2016 Upgrade Advisor，並執行 Stretch Database Advisor。 Stretch Database Advisor 也可以識別封鎖問題。  
  
## 下載並安裝 Upgrade Advisor  
 從 [這裡](http://go.microsoft.com/fwlink/?LinkID=613421)下載並安裝 Upgrade Advisor。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 安裝媒體未隨附此工具。  
  
## 執行 Stretch Database Advisor  
  
1.  執行 Upgrade Advisor。  
  
2.  選取 [Scenarios] (案例) ，然後選取 [Run Stretch Database Advisor] (執行 Stretch Database Advisor) 。  
  
3.  在 [Run Stretch Database Advisor] (執行 Stretch Database Advisor)  刀鋒視窗上，按一下 [SELECT DATABASES TO ANALYZE] (選取要分析的資料庫) 。  
  
4.  在 [選取資料庫] 刀鋒視窗中，輸入或選取伺服器名稱和驗證資訊。 按一下 **[連接]**。

5.  所選伺服器上的資料庫清單隨即出現。 選取您想要分析的資料庫。 按一下 [選取]。  
  
6.  在 [Run Stretch Database Advisor] (執行 Stretch Database Advisor)  刀鋒視窗上，按一下 [執行] 。  即會執行分析。  
  
## 檢閱結果  
  
1.  分析完成時，請在 [Analyzed databases (已分析資料庫)] 刀鋒視窗上選取您已分析的其中一個資料庫，以顯示 [分析結果] 刀鋒視窗。  
  
     [分析結果]  刀鋒視窗會列出所選資料庫中符合預設建議準則的建議資料表。 
  
2.  在 [分析結果] 刀鋒視窗的資料表清單中，選取其中一個建議資料表來顯示 [資料表結果] 刀鋒視窗。  
  
     [資料表結果] 刀鋒視窗會列出所選資料表的封鎖問題。 如需 Stretch Database Advisor 偵測到之封鎖問題的相關資訊，請參閱 [Stretch Database 的限制](../../sql-server/stretch-database/limitations-for-stretch-database.md)。  
  
3.  在 [Table results (資料表結果)] 刀鋒視窗的封鎖問題清單中，選取其中一個問題，以顯示所選問題的詳細資訊，以及建議的降低風險步驟。 如果您想要設定針對 Stretch Database 選取的資料表，請實作建議的因應步驟。  
  
## 下一步  
 啟用 Stretch Database。  
  
-   若要在 **資料庫**上啟用 Stretch Database，請參閱 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)。  
  
-   若要在另一個 **資料表**上啟用 Stretch Database，而且已在資料庫上啟用 Stretch，則請參閱 [Enable Stretch Database for a table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)。  
  
## 另請參閱  
 [Stretch Database 的限制](../../sql-server/stretch-database/limitations-for-stretch-database.md)   
 [為資料庫啟用 Stretch Database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [為資料表啟用 Stretch Database](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)  
  
  