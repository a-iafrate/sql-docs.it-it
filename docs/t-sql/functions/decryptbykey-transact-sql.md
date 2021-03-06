---
title: DECRYPTBYKEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DecryptByKey_TSQL
- DECRYPTBYKEY
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], DecryptByKey function
- decryption [SQL Server], keys
- decryption [SQL Server], symmetric keys
- DECRYPTBYKEY function
ms.assetid: 6edf121f-ac62-4dae-90e6-6938f32603c9
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3d3064da25a280e7fe0d2534e7b2b2040094fbc3
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="decryptbykey-transact-sql"></a>DECRYPTBYKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Decrittografa i dati tramite una chiave simmetrica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DecryptByKey ( { 'ciphertext' | @ciphertext }   
    [ , add_authenticator, { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *ciphertext*  
 Dati crittografati con la chiave. *ciphertext* è di tipo **varbinary**.  
  
 **@ciphertext**  
 Variabile di tipo **varbinary** contenente dati crittografati con la chiave.  
  
 *add_authenticator*  
 Indica se un autenticatore è stato crittografato insieme al testo normale. Deve corrispondere al valore passato a EncryptByKey durante la crittografia dei dati. *add_authenticator* è di tipo **int**.  
  
 *authenticator*  
 Dati da cui generare un autenticatore. Deve corrispondere al valore specificato per EncryptByKey. *authenticator* è di tipo **sysname**.  
  
 **@authenticator**  
 Variabile contenente i dati da cui generare un autenticatore. Deve corrispondere al valore specificato per EncryptByKey.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varbinary** con un valore massimo di 8.000 byte.
 
Restituisce NULL se la chiave simmetrica usata per crittografare i dati non è aperta o *ciphertext* è NULL.
  
## <a name="remarks"></a>Remarks  
 DecryptByKey usa una chiave simmetrica. Tale chiave deve essere già aperta nel database. È possibile che siano presenti più chiavi aperte contemporaneamente. Non è necessario aprire la chiave prima di decrittografare il testo definito dall'argomento ciphertext.  
  
 La crittografia e decrittografia simmetriche sono operazioni relativamente veloci, ideali per operazioni basate su quantità elevate di dati.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessario che la chiave simmetrica sia stata aperta durante la sessione corrente. Per altre informazioni, vedere [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-decrypting-by-using-a-symmetric-key"></a>A. Decrittografia di dati tramite una chiave simmetrica  
 Nell'esempio seguente il testo definito dall'argomento ciphertext viene decrittografato tramite una chiave simmetrica.  
  
```  
-- First, open the symmetric key with which to decrypt the data.  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
GO  
  
-- Now list the original ID, the encrypted ID, and the   
-- decrypted ciphertext. If the decryption worked, the original  
-- and the decrypted ID will match.  
SELECT NationalIDNumber, EncryptedNationalID   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalID))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-decrypting-by-using-a-symmetric-key-and-an-authenticating-hash"></a>B. Decrittografia di dati tramite una chiave simmetrica e un hash di autenticazione  
 Nell'esempio seguente vengono decrittografati i dati crittografati insieme a un autenticatore.  
  
```  
-- First, open the symmetric key with which to decrypt the data  
OPEN SYMMETRIC KEY CreditCards_Key11  
   DECRYPTION BY CERTIFICATE Sales09;  
GO  
  
-- Now list the original card number, the encrypted card number,  
-- and the decrypted ciphertext. If the decryption worked,   
-- the original number will match the decrypted number.  
SELECT CardNumber, CardNumber_Encrypted   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByKey(CardNumber_Encrypted, 1 ,   
    HashBytes('SHA1', CONVERT(varbinary, CreditCardID))))   
    AS 'Decrypted card number' FROM Sales.CreditCard;  
GO  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Scelta di un algoritmo di crittografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
  
