---
title: 檢查資料庫完整性工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.checkdatabaseintegritytask.f1
helpviewer_keywords:
- data integrity [Integration Services]
- Check Database Integrity task [Integration Services]
- checking database consistency
- database consistency checks [Integration Services]
- verifying database consistency
- integrity checking [Integration Services]
ms.assetid: 5a82fe99-4503-429f-9337-e6bac7649fe4
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d4f2801b550f760c9a14efa2fba780a686dd80ab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243038"
---
# <a name="check-database-integrity-task"></a>檢查資料庫完整性工作
  「檢查資料庫完整性」工作會檢查指定資料庫中所有物件的配置及結構完整性。 這項工作可檢查單一資料庫或多個資料庫，而且您可以選擇是否同時檢查資料庫索引。  
  
 「檢查資料庫完整性」工作會封裝 DBCC CHECKDB 陳述式。 如需詳細資訊，請參閱 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)。  
  
## <a name="configuration-of-the-check-database-integrity-task"></a>設定檢查資料庫完整性工作  
 您可以透過「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」設定屬性 這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 區段。  
  
 如需有關可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：  
  
-   [檢查資料庫完整性工作 &#40;維護計畫&#41;](../../relational-databases/maintenance-plans/check-database-integrity-task-maintenance-plan.md)  
  
 如需有關如何在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：  
  
-   [設定工作或容器的屬性](../set-the-properties-of-a-task-or-container.md)  
  
  
