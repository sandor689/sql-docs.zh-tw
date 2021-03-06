---
title: ADOStreamConstruction 介面 |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction
helpviewer_keywords:
- ADOStreamConstruction interface [ADO]
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73c5e698ecebee93e6b78d884b0b2978750db63e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275687"
---
# <a name="adostreamconstruction-interface"></a>ADOStreamConstruction 介面
**ADOStreamConstruction**介面用來建構 ADO**資料流**從 OLE DB 物件**IStream** C/c + + 應用程式中的物件。  
  
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|[Stream 屬性](../../../ado/reference/ado-api/stream-property.md)|讀取/寫入。 取得/設定 OLE DB**資料流**物件。|  
  
## <a name="methods"></a>方法  
 無。  
  
## <a name="events"></a>事件  
 無。  
  
## <a name="remarks"></a>備註  
 指定 OLE DB **IStream**物件 (`pStream`)，ADO 建構**資料流**物件 (`adoStr`) 於下列三個基本作業：  
  
1.  建立 ADO**資料流**物件：  
  
    ```  
    Stream20Ptr adoStr;  
    adoStr.CreateInstance(__uuidof(Stream));  
    ```  
  
2.  查詢**IADOStreamConstruction**介面上**資料流**物件：  
  
    ```  
    adoStreamConstructionPtr adoStrConstruct=NULL;  
    adoStr->QueryInterface(__uuidof(ADOStreamConstruction),  
                         (void**)&adoStrConstruct);  
    ```  
  
 呼叫`IADOStreamConstruction::get_Stream`屬性方法來設定 OLE DB **IStream**上之 ADO 物件**資料流**物件：  
  
```  
IUnknown *pUnk=NULL;  
pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
adoStrConstruct->put_Stream(pUnk);  
```  
  
 產生`adoStr`物件現在代表 ADO**資料流**建構從 OLE DB 物件**IStream**物件。  
  
## <a name="requirements"></a>需求  
 **版本：** ADO 2.0 或更新版本  
  
 **程式庫：** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>另請參閱  
 [ADO API 參考](../../../ado/reference/ado-api/ado-api-reference.md)
