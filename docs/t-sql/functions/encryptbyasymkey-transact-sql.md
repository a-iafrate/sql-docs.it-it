---
title: ENCRYPTBYASYMKEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- ENCRYPTBYASYMKEY
- ENCRYPTBYASYMKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTBYASYMKEY function
- encryption [SQL Server], asymmetric keys
- asymmetric keys [SQL Server], ENCRYPTBYASYMKEY function
ms.assetid: 86bb2588-ab13-4db2-8f3c-42c9f572a67b
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff79a5a15cb293646d75d4a411632f58c3efe0de
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="encryptbyasymkey-transact-sql"></a>ENCRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crittografa i dati con una chiave asimmetrica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EncryptByAsymKey ( Asym_Key_ID , { 'plaintext' | @plaintext } )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Asym_Key_ID*  
 ID di una chiave asimmetrica nel database. **int**.  
  
 *cleartext*  
 Stringa di dati che verrà crittografata con la chiave asimmetrica.  
  
 **@plaintext**  
 Variabile di tipo **nvarchar**, **char**, **varchar**, **binary**, **varbinary** o **nchar** contenente i dati da crittografare con la chiave asimmetrica.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varbinary** con un valore massimo di 8.000 byte.  
  
## <a name="remarks"></a>Remarks  
 La crittografia e la decrittografia con chiave asimmetrica sono estremamente costose rispetto alla crittografia e alla decrittografia con chiave simmetrica. È consigliabile non utilizzare una chiave asimmetrica per crittografare set di dati di grandi dimensioni, ad esempio i dati utente contenuti nelle tabelle. Crittografare invece i dati mediante una chiave simmetrica avanzata e crittografare la chiave simmetrica utilizzando una chiave asimmetrica.  
  
 **EncryptByAsymKey** restituisce **NULL** se l'input supera un determinato numero di byte, a seconda dell'algoritmo. I limiti sono: una chiave RSA a 512 bit può crittografare fino a 53 byte, una chiave a 1024 bit può crittografare un massimo di 117 byte e una chiave a 2048 bit può crittografare fino a 245 byte. Si noti che in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sia i certificati sia le chiavi asimmetriche sono wrapper sulle chiavi RSA.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene crittografato il testo archiviato in `@cleartext` con la chiave asimmetrica `JanainaAsymKey02`. I dati crittografati vengono quindi inseriti nella tabella `ProtectedData04`.  
  
```  
INSERT INTO AdventureWorks2012.Sales.ProtectedData04   
    VALUES( N'Data encrypted by asymmetric key ''JanainaAsymKey02''',  
    EncryptByAsymKey(AsymKey_ID('JanainaAsymKey02'), @cleartext) );  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DECRYPTBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/decryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
