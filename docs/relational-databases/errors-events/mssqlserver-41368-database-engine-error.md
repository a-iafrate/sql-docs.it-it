---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
robots: noindex,nofollow
ms.workload: Inactive
ms.openlocfilehash: e2aded8bf29e77ff4239528790b3b8745dd97d3a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver41368"></a>MSSQLSERVER_41368
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41368|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|Testo del messaggio|L'accesso alle tabelle con ottimizzazione per la memoria utilizzando il livello di isolamento READ COMMITTED è supportato solo per transazioni in modalità autocommit. Non è invece supportato con le transazioni implicite o esplicite. Specificare un livello di isolamento supportato per la tabella con ottimizzazione per la memoria utilizzando un hint di tabella, ad esempio WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Spiegazione  
L'accesso alle tabelle ottimizzate per la memoria utilizzando il livello di isolamento READ COMMITTED è supportato solo per transazioni in modalità autocommit. Per altre informazioni, vedere [Transazioni con tabelle e procedure in memoria](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md).  
  
Quando si accede a una tabella ottimizzata per la memoria da una transazione esplicita avviata tramite un'istruzione BEGIN TRANSACTION o da una transazione implicita, se l'opzione IMPLICIT_TRANSACTIONS è impostata su ON, il livello di isolamento READ COMMITTED non è supportato.  
  
## <a name="user-action"></a>Azione dell'utente  
Quando si accede a una tabella ottimizzata per la memoria da una transazione esplicita o implicita READ COMMITTED, utilizzare l'istruzione SNAPSHOT per accedere alla tabella. A questo scopo, è possibile usare l'hint di tabella WITH (SNAPSHOT) (per altre informazioni, vedere [Transazioni con tabelle e procedure in memoria](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)) o impostare l'opzione MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT del database su ON (per altre informazioni, vedere [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql.md)).  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
