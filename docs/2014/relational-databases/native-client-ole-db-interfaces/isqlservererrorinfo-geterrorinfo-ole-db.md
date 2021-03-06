---
title: 'Isqlservererrorinfo:: Geterrorinfo (OLE DB) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f33c66d8e521339573e56b78407f0bab67b4b43e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430097"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
  將指標傳回至[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者 SSERRORINFO 結構包含[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]錯誤詳細資料。  
  
## <a name="syntax"></a>語法  
  
```  
  
   HRESULT GetErrorInfo(  
SSERRORINFO**ppSSErrorInfo,  
OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>引數  
 *ppSSErrorInfo*[out]  
 SSERRORINFO 結構的指標。 如果方法失敗，或者沒有任何[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]錯誤的相關資訊，提供者不會配置任何記憶體，並確保*ppSSErrorInfo*引數是輸出的 null 指標。  
  
 *ppErrorStrings*[out]  
 Unicode 字元字串指標的指標。 如果方法失敗，或者沒有任何[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]與錯誤相關聯的資訊，提供者不會配置任何記憶體，並確保*ppErrorStrings*引數是輸出的 null 指標。 釋放*ppErrorStrings*引數**imalloc:: Free**方法會釋放傳回的 SSERRORINFO 結構的三個個別字串成員，因為區塊中配置記憶體。  
  
## <a name="return-code-values"></a>傳回碼值  
 S_OK  
 此方法已成功。  
  
 E_INVALIDARG  
 任一*ppSSErrorInfo*或*ppErrorStrings*引數為 NULL。  
  
 E_OUTOFMEMORY  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者無法配置足夠的記憶體來完成要求。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會針對透過取用者傳遞之指標所傳回的 SSERRORINFO 和 OLECHAR 字串配置記憶體。 取用者必須使用項目取消配置此記憶體**imalloc:: Free**時不再需要存取的錯誤資料的方法。  
  
 SSERRORINFO 結構定義如下：  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|成員|描述|  
|------------|-----------------|  
|*pwszMessage*|來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的錯誤訊息。 透過傳回的訊息**ierrorinfo:: Getdescription**方法。|  
|*pwszServer*|發生錯誤之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。|  
|*pwszProcedure*|如果在預存程序中發生錯誤，則是產生錯誤之預存程序的名稱，否則為空字串。|  
|*lNative*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤號碼。 中所傳回的錯誤號碼等同*isqlerrorinfo:: Getsqlinfo*的參數**isqlerrorinfo:: Getsqlinfo**方法。|  
|*bState*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤的狀態。|  
|*bClass*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤的嚴重性。|  
|*wLineNumber*|在適用時，這是產生錯誤訊息之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序的行號。 如果不包含任何程序，預設值為 1。|  
  
 結構中的指標參考中傳回之字串中的地址*ppErrorStrings*引數。  
  
## <a name="see-also"></a>另請參閱  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
