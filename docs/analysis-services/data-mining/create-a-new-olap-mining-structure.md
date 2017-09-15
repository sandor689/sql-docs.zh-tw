---
title: "建立新的 OLAP 採礦結構 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], OLAP
- mining structures [Analysis Services], creating
- OLAP [Analysis Services], mining models
ms.assetid: 368f4273-a016-4748-bcb6-505a3e745af3
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 41047907b0e53f6d17fc49a9734ed4b9a52817f1
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-new-olap-mining-structure"></a>建立新的 OLAP 採礦結構
  您可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的資料採礦精靈，建立使用多維度模型資料的採礦結構。 以 OLAP Cube 為基礎的採礦模型可以使用事實資料表、維度和量值群組中的資料行和值做為分析屬性。  
  
### <a name="to-create-a-new-olap-mining-structure"></a>若要建立新的 OLAP 採礦結構  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的方案總管中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案中的 [採礦結構] 資料夾，然後按一下 [新增採礦結構] 開啟 [資料採礦精靈]。  
  
2.  在 **[歡迎使用資料採礦精靈]** 頁面上，按 **[下一步]**。  
  
3.  在 **[選取定義方法]** 頁面上，選取 **[從現有的 Cube]**，然後按 **[下一步]**。  
  
     如果出現錯誤訊息：「無法擷取支援的資料採礦演算法的清單」，請開啟 [專案屬性] 對話方塊，確認您已經指定支援多維度模型的 Analysis Services 執行個體名稱。 不能在支援表格式模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上建立採礦模型。  
  
4.  在 **[建立資料採礦結構]** 頁面上，決定只要建立採礦結構，還是建立採礦結構再加上一個相關的採礦模型。 通常，同時建立採礦模型比較容易，因為這樣系統會提示您包含必要的資料行。  
  
     如果您要建立採礦模型，請選取您想要使用的資料採礦演算法，然後按 **[下一步]**。 如需如何選擇演算法的詳細資訊，請參閱[資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)。  
  
5.  在 **[選取來源 Cube 維度]** 頁面的 **[選取來源 Cube 維度]**之下，找出包含多數案例資料的維度。  
  
     例如，如果您嘗試識別客戶群組，可以選擇 [Customer] 維度；如果您嘗試分析跨多筆交易的購買行為，可以選擇 [Internet Sales Order Details] 維度。 不限制您只能使用此維度中的資料，但該維度應該包含要在分析中使用的重要屬性。  
  
     按一下 **[下一步]**。  
  
6.  在 **[選取案例索引鍵]** 頁面的 **[屬性]**之下，選取將成為採礦結構之索引鍵的屬性，然後按 **[下一步]**。  
  
     通常，做為採礦結構之索引鍵的屬性也是維度的索引鍵，並且會預先選取。  
  
7.  在 **[選取案例層級資料行]** 頁面的 **[相關的屬性和量值]**之下，選取其值要加入至採礦結構中做為案例資料的屬性和量值。 按一下 **[下一步]**。  
  
8.  在 **[指定採礦模型資料行使用方式]** 頁面的 **[採礦模型結構]**之下，先設定可預測資料行，然後選擇要做為輸入的資料行。  
  
    -   選取最左邊資料行的核取方塊，將資料包含在採礦結構中。 您可以在結構中包含僅供參考但不用於分析的資料行。  
  
    -   選取 **[輸入]** 資料行的核取方塊，將屬性做為分析中的變數。  
  
    -   選取 **[預測]** 資料行的核取方塊，只做為可預測屬性。  
  
     請注意，已指定為索引鍵的資料行不能用於輸入或預測。  
  
     按一下 **[下一步]**。  
  
9. 在 **[指定採礦模型資料行使用方式]** 頁面上，您也可以使用 **[加入巢狀資料表]** 和 **[移除巢狀資料表]**，對採礦結構新增及移除巢狀資料表。  
  
     在 OLAP 採礦模型中，巢狀資料表是 Cube 中與表示案例屬性的維度具有一對多關聯性的另一組資料。 因此，在對話方塊開啟時，它會預先選取已經與您選定為案例資料表的維度相關的量值群組。 此時，您可以選擇包含可用於分析之附加資訊的其他維度。  
  
     例如，如果您要分析客戶，可以使用 [Customer] 維度作為案例資料表。 對於巢狀資料表，您可以加入客戶在購買時陳述的原因，該原因包含在 [Sales Reason] 維度中。  
  
     如果您新增巢狀資料，則必須多指定兩個資料行：  
  
    -   巢狀資料表的索引鍵：這應該在 [選取巢狀資料表索引鍵] 頁面上預先選取。  
  
    -   用於分析的屬性： **[選取巢狀資料表資料行]**頁面提供巢狀資料表選取範圍的量值和屬性清單。  
  
        -   對於要包含在模型中的每個屬性，請選取左側資料行的核取方塊。  
  
        -   如果您要屬性只做為分析之用，請核取 **[輸入]**。  
  
        -   如果您想要將資料行包含在模型中做為其中一個可預測屬性，請選取 **[預測]**。  
  
        -   包含在結構中、但未指定為輸入或可預測屬性的任何項目，在新增至結構中時會標示 **Ignore**；這表示在建立模型時會處理此資料，但資料不用於分析，只供鑽研使用。 如果您想要包含詳細資料 (例如客戶名稱)，但不想在分析中使用這些資訊時，此功能可能很方便。  
  
     按一下 **[完成]** 關閉處理巢狀資料表的精靈部分。 您可以重複此程序，新增多個巢狀資料行。  
  
10. 在 **[指定資料行的內容和資料類型]** 頁面的 **[採礦模型結構]**之下，設定每一個資料行的內容類型和資料類型。  
  
    > [!NOTE]  
    >  OLAP 採礦模型不支援使用 [偵測] 功能，來自動偵測資料行包含連續資料或不連續資料。  
  
     按一下 **[下一步]**。  
  
11. 在 **[配量來源 Cube]** 頁面上，您可以篩選用來建立採礦結構的資料。  
  
     配量 Cube 可讓您限制用來建立模型的資料。 例如，您可以透過對 [Geography] 階層和下列項目進行配量，為每個地區建立不同的模型。  
  
    -   **維度**：從下拉式清單中選擇相關維度。  
  
    -   **階層**：選取要套用篩選的維度階層層級。 例如，如果您依 [Geography] 維度進行配量，則可以選擇階層層級，例如 [Region Country Name]。  
  
    -   **運算子**：從清單選取運算子。  
  
    -   **篩選運算式**：輸入要做為篩選條件的值或運算式，或者使用下拉式清單，從指定之階層層級的成員清單中選取一個值  
  
         例如，如果您選取 [Geography] 作為維度並選取 [Region Country Name] 作為階層層級，則下拉式清單會包含可作為篩選條件的所有有效國家/地區。 您可以複選。 因此，採礦結構中的資料會限制為來自這些地域的 Cube 資料。  
  
    -   **參數**：忽略此核取方塊。 此對話方塊支援多個 Cube 篩選案例，而此選項與建立採礦結構無關。  
  
     按一下 **[下一步]**。  
  
12. 在 **[將資料分割成定型集和測試集]** 頁面上，指定要保留供測試的採礦結構資料百分比，或指定測試案例的最大數目。 按一下 **[下一步]**。  
  
     如果您指定了這兩個值，就會結合這些限制，以便使用最低的值。  
  
13. 在 **[正在完成精靈]** 頁面上，為新的 OLAP 採礦結構和初始採礦模型提供名稱。  
  
14. 按一下 **[完成]**。  
  
15. 在 [正在完成精靈] 頁面上，您也可以選擇建立採礦模型維度和/或使用採礦模型維度的 Cube。 只有使用下列演算法建立的模型才支援這些選項：  
  
    -   Microsoft 叢集演算法  
  
    -   Microsoft 決策樹演算法  
  
    -   Microsoft 關聯規則演算法  
  
     **建立採礦模型維度**：選取此核取方塊，並提供採礦模型維度的類型名稱。 當您使用此選項時，會在用於建立採礦結構的原始 Cube 內建立新維度。 您可以使用此維度向下鑽研和執行進一步的分析。 因為該維度位於 Cube 內，所以該維度會自動對應至案例資料維度。  
  
     **使用採礦模型維度建立 Cube**：選取此核取方塊，並提供新 Cube 的名稱。 當您使用此選項時，所建立的新 Cube 同時會包含建立結構所使用的現有維度，以及包含模型結果的新資料採礦維度。  
  
## <a name="see-also"></a>請參閱＜  
 [採礦結構工作和使用說明](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  