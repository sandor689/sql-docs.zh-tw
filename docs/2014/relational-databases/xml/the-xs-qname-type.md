---
title: xs:QName 類型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- xs:QName type
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c0f2729640d40879fa45dc70229f9d0ed8e2d178
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223233"
---
# <a name="the-xsqname-type"></a>xs:QName 類型
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支援使用 XML 結構描述限制元素且從 **xs:QName** 衍生的類型。 此外， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目前不支援 **QName** 為成員類型的聯集類型。  
  
## <a name="example"></a>範例  
 下列 `CREATE XML SCHEMA COLLECTION` 陳述式無法載入 XML 結構描述，因為它們將 `xs:QName` 類型指定為聯集的成員類型：  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 這兩個陳述式會因錯誤而導致失敗。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器上 XML 結構描述集合的需求與限制](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
