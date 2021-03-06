---
title: 將伺服器設定為執行 Off By Default 原則 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: 41c3022d-ab13-443e-ac64-ba1d64584f79
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bd8198d4ab869b38491a58782a03e73d2aaecb5c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32954243"
---
# <a name="lesson-1-2---configure-a-server-to-run-the-off-by-default-policy"></a>第 1-2 課：將伺服器設定為執行 Off By Default 原則
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
現在，您有一個名為 Off By Default 的原則。 在這項工作中，您將檢查伺服器是否符合這個原則的需求。  
  
### <a name="to-run-the-off-by-default-policy"></a>執行 Off By Default 原則  
  
1.  在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，指向 [原則]，然後按一下 [評估]。  
  
2.  在 [評估原則] 對話方塊中，您可以從另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體或檔案中選取原則。 在這個步驟中，請將 [來源] 保持設定為 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。  
  
3.  在 [原則] 區段中，選取 [預設關閉] 原則。  
  
4.  若要查看伺服器是否符合此原則，請按一下 [評估]。  
  
5.  如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 符合此原則，您將會在 [結果] 區域中看見含有核取記號的綠色圓圈。 如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 不符合此原則，您就會看見含有 X 的紅色圓圈。  
  
6.  在 [目標詳細資料] 區域中，您將會在錯誤發生時於 [訊息] 資料行中看到其他資訊。 在 [訊息] 資料行中，按一下 [檢視] 查看報表，其中包含所檢查之每個 Facet 屬性的檢查結果。  
  
7.  原則描述會顯示在頁面底部，而且 [其他說明] 區段會顯示您已針對此原則設定的超連結。 按一下訊息超連結，即可開啟您在建立此原則時指定的網頁。  
  
8.  關閉瀏覽器，然後關閉 [結果詳細檢視] 對話方塊。  
  
9. 如果伺服器不符合原則，而且您想要停用 Database Mail，請按一下 [評估結果] 頁面中的 [套用]。  
  
10. 關閉 [結果詳細檢視] 和 [評估原則] 對話方塊。  
  
## <a name="next-lesson"></a>下一課  
[第 2 課：建立和套用命名標準原則](../../relational-databases/policy-based-management/lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
  
