---
title: "SQL Server 憑證與非對稱金鑰 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安全性 [SQL Server], 憑證與非對稱金鑰"
ms.assetid: 8519aa2f-f09c-4c1c-96b5-abc24811e60c
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# SQL Server 憑證與非對稱金鑰
  公開金鑰加密 (PKI) 是一種訊息加密形式，使用者可用此加密形式來建立「公開」(Public) 金鑰和「私密」(Private) 金鑰。 私密金鑰會保留在私密位置，而公開金鑰則可以散發給使用者。 雖然這些金鑰在數學上具有相關性，但是私密金鑰無法使用公開金鑰來輕鬆地衍生。 公開金鑰是用來加密資料，而私密金鑰則是用來解密資料。 使用公開金鑰加密的訊息只能使用正確的私密金鑰來加以解密。 由於有兩種不同的金鑰，所以這些金鑰為「非對稱」(Asymmetric)。  
  
 憑證和非對稱金鑰是使用非對稱加密的兩種方式。 憑證經常當做非對稱金鑰的容器使用，因為它們可以包含類似到期日和簽發者等其他資訊。 密碼編譯演算法的兩個機制之間沒有任何差異，而且當提供相同的金鑰長度時，強度不會有任何差異。 一般來說，您可以使用憑證來加密資料庫中的其他加密金鑰類型，或是簽署程式碼模組。  
  
 憑證和非對稱金鑰可以解密其他金鑰加密的資料。 一般來說，非對稱加密可用來加密對稱金鑰，以儲存在資料庫中。  
  
 公開金鑰並沒有與憑證一樣的特定格式，而且您無法將它匯出到檔案中。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含的功能可讓您建立與管理要與伺服器和資料庫搭配使用的憑證和金鑰。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法與其他應用程式搭配使用或無法用來在作業系統中建立與管理憑證和金鑰。  
  
## 憑證  
 憑證是數位簽署的安全性物件，其中包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的公開金鑰 (以及選擇性的私密金鑰)。 您可以使用外部產生的憑證，或者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 也可以產生憑證。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 憑證符合 IETF X.509v3 憑證標準的規則。  
  
 因為可以選擇將金鑰匯出及匯入成 X.509 憑證檔案，所以憑證會非常實用。 建立憑證的語法可讓您建立憑證的選項 (如到期日)。  
  
### 在 SQL Server 中使用憑證  
 憑證可用來維護連接的安全、在資料庫鏡像中用來簽署封裝和其他物件，或是加密資料或連接。 下表列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中憑證的其他資源。  
  
|主題|描述|  
|-----------|-----------------|  
|[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)|說明用來建立憑證的命令。|  
|[使用數位簽章來識別封裝的來源](../../integration-services/packages/identify-the-source-of-packages-with-digital-signatures.md)|顯示有關如何使用憑證來簽署軟體封裝的資訊。|  
|[使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|涵蓋如何搭配資料庫鏡像使用憑證的相關資訊。|  
  
## 非對稱金鑰  
 非對稱金鑰是用來維護對稱金鑰的安全， 也可用於有限制的資料加密及數位簽署資料庫物件。 非對稱金鑰是由私密金鑰與對應的公開金鑰所組成。 如需非對稱金鑰的詳細資訊，請參閱 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)。  
  
 非對稱金鑰可從強式名稱金鑰檔案匯入，但是無法匯出。 此外，它們也沒有到期選項。 非對稱金鑰無法為連接加密。  
  
### 在 SQL Server 中使用非對稱金鑰  
 非對稱金鑰可用來維護資料的安全或是簽署純文字。 下表列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中非對稱金鑰的其他資源。  
  
|主題|描述|  
|-----------|-----------------|  
|[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)|說明用來建立非對稱金鑰的命令。|  
|[SIGNBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/signbyasymkey-transact-sql.md)|顯示用來簽署物件的選項。|  
  
## 工具  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 提供了將會產生憑證和強式名稱金鑰檔案的工具和公用程式。 這些工具在金鑰產生的程序中，提供了比 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 語法更豐富的彈性。 您可以使用這些工具來建立具有更複雜金鑰長度的 RSA 金鑰，並將其匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 下表說明要在哪裡找到這些工具。  
  
|||  
|-|-|  
|工具|目的|  
|[makecert](http://msdn2.microsoft.com/library/bfsktky3\(VS.80\).aspx)|建立憑證。|  
|[sn](http://msdn2.microsoft.com/library/k5b5tt23\(VS.80\).aspx)|為對稱金鑰建立強式名稱。|  
  
## 相關工作  
 [選擇加密演算法](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
  
## 另請參閱  
 [sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)   
 [透明資料加密 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption-tde.md)  
  
  