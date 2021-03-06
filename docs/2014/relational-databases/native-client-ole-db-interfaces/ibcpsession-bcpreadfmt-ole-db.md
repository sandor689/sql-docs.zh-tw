---
title: 'Ibcpsession:: Bcpreadfmt (OLE DB) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa0f1501955db61889bb437e545cda95dfe8b31f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428253"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>IBCPSession::BCPReadFmt (OLE DB)
  從格式檔案中讀取每個資料行的格式資訊。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>備註  
 **BCPReadFmt**方法適用於從資料檔中指定的資料格式的格式檔案讀取資料。 這個方法能夠偵測格式檔案的正確版本。 它可以自動偵測格式檔案為 xml 還是舊樣式的文字格式，並適當地產生行為。 所支援的格式檔案版本[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者 BCP 為 6.0 版或更新版本。  
  
 在後**BCPReadFmt**方法讀取格式值，它會適當地呼叫[ibcpsession:: Bcpcolumns](ibcpsession-bcpcolumns-ole-db.md)並[ibcpsession:: Bcpcolfmt](ibcpsession-bcpcolfmt-ole-db.md)方法。 使用者不需要剖析格式檔案，也不需要進行這些呼叫。  
  
 若要儲存的格式檔案，請呼叫[ibcpsession:: Bcpwritefmt](ibcpsession-bcpwritefmt-ole-db.md)方法。 若要呼叫**BCPReadFmt**方法可以參考已儲存的格式。 或者，大量複製公用程式 (**bcp**) 可以將使用者定義的資料格式儲存在您可以參考的檔案**BCPReadFmt**方法。  
  
 `BCP_OPTION_DELAYREADFMT`的值*eOption*參數[ibcpsession:: Bcpcontrol](ibcpsession-bcpcontrol-ole-db.md)修改 ibcpsession:: Bcpreadfmt 的行為。  
  
## <a name="arguments"></a>引數  
 *pwszFormatFile*[in]  
 包含資料檔案式值之檔案的路徑和檔案名稱。  
  
## <a name="return-code-values"></a>傳回碼值  
 S_OK  
 此方法已成功。  
  
 E_FAIL  
 發生提供者特定的錯誤，如需詳細的資訊，請使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)介面。  
  
 E_OUTOFMEMORY  
 記憶體不足的錯誤。  
  
 E_UNEXPECTED  
 此方法的呼叫是非預期的。 例如， [ibcpsession:: Bcpinit](ibcpsession-bcpinit-ole-db.md)方法不會呼叫這個方法之前呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [執行大量複製作業](../native-client/features/performing-bulk-copy-operations.md)  
  
  
