---
title: 設定參數值對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3559b30e2a8e6feff03dcd9452bd335ea8c4a268
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2018
ms.locfileid: "35329502"
---
# <a name="set-parameter-value-dialog-box"></a>設定參數值對話方塊
  使用 **[設定參數值]** 對話方塊來針對專案和封裝設定參數與連接管理員屬性的值。  
  
 **您想要做什麼事？**  
  
-   [開啟設定參數值對話方塊](#open_dialog)  
  
-   [設定選項](#option)  
  
##  <a name="open_dialog"></a> 開啟設定參數值對話方塊  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。  
  
     您正在連接到主控 SSISDB 資料庫之 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體。  
  
2.  在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。  
  
3.  展開 **[SSISDB]** 節點。  
  
4.  以滑鼠右鍵按一下封裝或專案，再按一下 [設定]，然後按一下 [參數] 索引標籤或 [連線管理員] 索引標籤中的省略符號按鈕。  
  
##  <a name="option"></a> 設定選項  
 **參數**  
 列出參數名稱。  
  
 **型別**  
 列出參數值的資料類型。  
  
 **說明**  
 顯示參數的選擇性描述。  
  
 **編輯值**  
 選取此選項來編輯參數值。  
  
 **使用封裝中的預設值**  
 選取此選項可使用儲存在封裝中的預設參數值。  
  
 **使用環境變數**  
 選取此選項可使用儲存在環境中的變數值，該值是由專案或封裝所參考。 若要將環境參考加入至專案或封裝中，請使用 **[設定]** 對話方塊。 如需相關資訊，請參閱 [Configure Dialog Box](../../integration-services/catalog/configure-dialog-box.md)。  
  
  
