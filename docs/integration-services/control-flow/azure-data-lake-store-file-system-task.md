---
title: "Azure Data Lake Store 檔案系統工作 |Microsoft 文件"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 303d3b74da3fe370d19b7602c0e11e67b63191e7
ms.openlocfilehash: ce2355de312faed9ab66991d6d0dd344ff315a55
ms.contentlocale: zh-tw
ms.lasthandoff: 08/29/2017

---
# <a name="azure-data-lake-store-file-system-task"></a>Azure Data Lake Store 檔案系統工作

**Azure 資料湖存放區檔案系統工作**可讓使用者執行各種不同的檔案系統作業上[Azure 資料湖存放區 (ADLS)](https://azure.microsoft.com/services/data-lake-store/)。

**Azure 資料湖存放區檔案系統工作**是一種元件的[Azure 的 SQL Server Integration Services (SSIS) Feature Pack](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)。

若要將 Azure 資料湖存放區檔案系統 」 工作加入封裝時，將它從 [SSIS 工具箱] 拖曳至設計工具的畫布。 按兩下此工作，或以滑鼠右鍵按一下工作，然後選取**編輯**，以開啟 [工作編輯器] 對話方塊。

**作業**屬性會指定要執行的檔案系統作業。 支援下列作業。

* **CopyToADLS:**檔案上傳至 ADLS。
* **CopyFromADLS:**從 ADLS 下載檔案。

對於任何作業，您必須指定 Azure 資料湖連接管理員。

以下是屬性的說明每個作業專屬。

## <a name="copytoadls"></a>CopyToADLS
* **LocalDirectory:**指定含有要上傳檔案的來源目錄。
* **FileNamePattern:**指定原始程式檔的檔案名稱篩選條件。 將會上傳其名稱符合指定的模式的檔案。 萬用字元`*`和`?`支援。
* **SearchRecursively:**指定是否要搜尋以遞迴方式上傳檔案的來源目錄內。
* **AzureDataLakeDirectory:**指定檔案上傳到的 ADLS 目的地目錄。
* **FileExpiry:**指定到期的日期和時間的檔案上傳至 ADLS，或將此屬性保留空白，表示檔案永遠不過期。

## <a name="copyfromadls"></a>CopyFromADLS
* **AzureDataLakeDirectory:**指定包含要下載之檔案的 ADLS 來源目錄。
* **SearchRecursively:**指定是否要下載的檔案的來源目錄中以遞迴方式搜尋。
* **LocalDirectory:**指定要儲存下載的檔案的目的地目錄。