---
title: Operatori di confronto (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], testing
- operators [Transact-SQL], comparison
- testing expressions
- Boolean data type
- Boolean expressions
- comparing expressions
- comparison operators [SQL Server]
ms.assetid: b0cc68ef-3029-484c-a917-0c15dcbc230d
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: f9bac752bfffc59f895e35d8e6e5e5c09748772e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="comparison-operators-transact-sql"></a>Operatori di confronto (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gli operatori di confronto consentono di confrontare due espressioni. Possono essere usati in qualsiasi espressione, ad eccezione delle espressioni con tipo di dati **text**, **ntext** o **image**. Nella tabella seguente vengono elencati gli operatori di confronto [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
|Operatore|Significato|  
|--------------|-------------|  
|[= (uguale a)](../../t-sql/language-elements/equals-transact-sql.md)|Uguale a|  
|[> (maggiore di)](../../t-sql/language-elements/greater-than-transact-sql.md)|Maggiore di|  
|[< (minore di)](../../t-sql/language-elements/less-than-transact-sql.md)|Minore di|  
|[>= (maggiore o uguale a)](../../t-sql/language-elements/greater-than-or-equal-to-transact-sql.md)|Maggiore o uguale a|  
|[<= (minore o uguale a)](../../t-sql/language-elements/less-than-or-equal-to-transact-sql.md)|Minore o uguale a|  
|[<> (diverso da)](../../t-sql/language-elements/not-equal-to-transact-sql-traditional.md)|Diverso da|  
|[!= (diverso da)](../../t-sql/language-elements/not-equal-to-transact-sql-exclamation.md)|Diverso da (non conforme allo standard ISO)|  
|[!< (non minore di)](../../t-sql/language-elements/not-less-than-transact-sql.md)|Non minore di (non conforme allo standard ISO)|  
|[!> (non maggiore di)](../../t-sql/language-elements/not-greater-than-transact-sql.md)|Non maggiore di (non conforme allo standard ISO)|  
  
## <a name="boolean-data-type"></a>Tipo di dati Boolean  
 Il risultato di un operatore di confronto è espresso nel tipo di dati **Boolean**. I possibili valori sono tre: TRUE, FALSE e UNKNOWN. Le espressioni che restituiscono un tipo di dati **Boolean** sono note come espressioni booleane.  
  
 A differenza di altri tipi di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un tipo di dati **Boolean** non può essere specificato per una colonna di tabella o una variabile e non può essere restituito in un set di risultati.  
  
 Quando l'opzione SET ANSI_NULLS è impostata su ON, un operatore con una o due espressioni NULL restituisce UNKNOWN. Quando l'opzione SET ANSI_NULLS è impostata su OFF, vengono applicate le stesse regole, ma l'operatore di uguaglianza (=) restituisce TRUE quando entrambe le espressioni sono NULL. Ad esempio, se SET ANSI_NULLS è impostata su OFF, NULL = NULL restituisce TRUE.  
  
 Le espressioni con tipi di dati **Boolean** vengono usate nella clausola WHERE per filtrare le righe che soddisfano le condizioni di ricerca e in istruzioni con elementi del linguaggio per il controllo di flusso quali IF e WHILE, ad esempio:  
  
```  
-- Uses AdventureWorks  
  
DECLARE @MyProduct int;  
SET @MyProduct = 750;  
IF (@MyProduct <> 0)  
   SELECT ProductID, Name, ProductNumber  
   FROM Production.Product  
   WHERE ProductID = @MyProduct;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
