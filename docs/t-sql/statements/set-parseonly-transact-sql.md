---
title: SET PARSEONLY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSEONLY_TSQL
- SET_PARSEONLY_TSQL
- PARSEONLY
- SET PARSEONLY
dev_langs:
- TSQL
helpviewer_keywords:
- parsing [SQL Server], SET PARSEONLY statement
- checking syntax
- PARSEONLY option
- syntax [SQL Server], verifying
- verifying syntax
- SET PARSEONLY statement
ms.assetid: 514ab042-c53e-4d96-be71-fb08fcc6ef3c
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2a117e81d9645edd9f24702ac01d8eeea3765726
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-parseonly-transact-sql"></a>SET PARSEONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Esamina la sintassi di ogni istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] e restituisce eventuali messaggi di errore senza compilare o eseguire l'istruzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET PARSEONLY { ON | OFF }  
```  
  
## <a name="remarks"></a>Osservazioni  
 Quando l'opzione SET PARSEONLY è impostata su ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue soltanto l'analisi dell'istruzione. Quando l'opzione SET PARSEONLY è impostata su OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compila ed esegue l'istruzione.  
  
 L'opzione SET PARSEONLY viene impostata in fase di analisi, non in fase di esecuzione.  
  
 Non utilizzare l'opzione PARSEONLY in una stored procedure o in un trigger. SET PARSEONLY restituisce valori di offset se l'opzione OFFSETS è impostata su ON e non si verificano errori.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [IMPOSTARE gli offset &#40; Transact-SQL &#41;](../../t-sql/statements/set-offsets-transact-sql.md)  
  
  