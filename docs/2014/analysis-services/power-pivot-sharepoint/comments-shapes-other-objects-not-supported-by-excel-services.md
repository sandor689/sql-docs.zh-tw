---
title: 下列功能不受 Excel Services 和可能不會顯示或是只顯示一部分： 註解、 形狀或其他物件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: 4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1bee0273ba256ea6861b4259d48e377528c5e4eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192414"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a>下列功能不受 Excel Services 的支援，而且可能不會顯示或是只顯示一部分：註解、形狀或其他物件
  當您從 PowerPivot 欄位清單將交叉分析篩選器加入到 PowerPivot 活頁簿時，將會發生這個錯誤。  
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|適用對象|PowerPivot for SharePoint|  
|產品版本|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|Excel Web Access 無法轉譯形狀物件，該物件用來控制從 PowerPivot 欄位清單加入至活頁簿之交叉分析篩選器的位置和格式。|  
|訊息文字|下列功能不受 Excel Services 的支援，而且可能不會顯示或是只顯示一部分：<br /><br /> 註解、形狀或其他物件<br /><br /> 某些功能 (例如外部資料查詢) 會顯示只能在 Microsoft Excel 中重新整理的快取資料。|  
  
## <a name="explanation"></a>說明  
 Excel Web Access 會顯示這個錯誤，當您在瀏覽器中開啟 PowerPivot 活頁簿，按一下**詳細資料**訊息，按鈕**不支援此功能的活頁簿可能不會如預期般顯示**。  
  
 發生這個錯誤是因為 PowerPivot 活頁簿包含交叉分析篩選器，此交叉分析篩選器的配置是由 Excel 中的隱藏形狀物件所控制。 形狀物件會控制交叉分析篩選器在水平和垂直位置的格式與定位。  
  
 Excel Services 無法轉譯形狀物件，但是因為此物件是隱藏的，所以它無法轉譯的事實並不會造成問題。  
  
## <a name="user-action"></a>使用者動作  
 可以忽略這個錯誤。 按一下 [確定]，關閉錯誤訊息，並繼續使用活頁簿和交叉分析篩選器，而不會發生任何問題。  
  
  
