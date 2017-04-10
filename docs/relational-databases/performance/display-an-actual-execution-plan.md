---
title: "顯示實際執行計畫 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "顯示執行計畫"
  - "實際執行計畫"
  - "檢視執行計畫"
  - "執行計劃 [SQL Server], 顯示"
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# 顯示實際執行計畫
  此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 產生實際的圖形執行計畫。 產生實際執行計畫後，就會執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢或批次。 所產生的執行計畫會顯示實際查詢執行計畫，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 將用來執行查詢。  
  
 若要使用這個功能，使用者必須具有適當權限，以便執行將會產生圖形執行計畫的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢，同時也需將查詢所參考之所有資料庫的 SHOWPLAN 權限，都授與給使用者。  
  
### 若要在執行期間包括查詢的執行計畫  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 工具列上，按一下 [Database Engine 查詢]。 您也可以按一下 [開啟檔案] 工具列按鈕並找出現有的查詢，以開啟現有的查詢並顯示估計執行計畫。  
  
2.  輸入您希望顯示其實際執行計畫的查詢。  
  
3.  在 [查詢] 功能表上，按一下 [包括實際執行計畫] 或按一下 [包括實際執行計畫] 工具列按鈕  
  
4.  按一下 [執行] 工具列按鈕執行查詢。 查詢最佳化工具所使用的計畫，會顯示在結果窗格的 [執行計畫] 索引標籤上。 將滑鼠游標暫時放在邏輯與實體運算子上，即可在顯示的 [工具提示] 中檢視運算子的說明與屬性。  
  
     或者，您可以在 [屬性] 視窗中檢視運算子屬性。 如果沒有看到 [屬性] 視窗，請以滑鼠右鍵按一下運算子，然後選取 [屬性]。 選取運算子以檢視其屬性。  
  
5.  您可以用滑鼠右鍵按一下執行計畫，然後選取 [放大]、[縮小]、[自訂顯示比例] 或 [縮放至適當比例]，來改變執行計畫的顯示。 [放大] 及 [縮小] 可讓您放大或縮小執行計畫，而 [自訂顯示比例] 則可讓您定義自己的顯示比例，如 80% 的顯示比例。 [縮放至適當比例] 會放大執行計畫，以符合結果窗格的大小。  
  
  