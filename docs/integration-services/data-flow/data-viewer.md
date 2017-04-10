---
title: "資料檢視器 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dataviewer.f1"
helpviewer_keywords: 
  - "資料檢視器對話方塊"
ms.assetid: 6351309a-688f-4e82-9697-1712130f10a1
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 13
---
# 資料檢視器
  如果路徑設定為使用資料檢視器，當資料在資料流程元件之間移動時，資料檢視器會一一顯示緩衝區的資料。  
  
## 選項。  
 **綠色箭頭**  
 按一下即可顯示下一個緩衝區中的資料。 如果在單一緩衝區中可以移動資料，則無法使用此選項。  
  
 **卸離**  
 卸離資料檢視器。  
  
 **請注意** 卸離資料檢視器不會刪除資料檢視器。 如果已卸離資料檢視器，則資料會繼續流經路徑，但不會更新檢視器中的資料以符合每個緩衝區中的資料。  
  
 **附加**  
 附加資料檢視器。  
  
 **請注意** 當附加資料檢視器時，它會顯示資料流程中之每個緩衝區的資訊，然後暫停。 您可以使用綠色箭頭來在緩衝區中向前推進。  
  
 **複製資料**  
 將目前緩衝區中的資料複製到剪貼簿。  
  
## 請參閱＜  
 [偵錯資料流程](../../integration-services/troubleshooting/debugging-data-flow.md)  
  
  