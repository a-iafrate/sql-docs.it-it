---
title: Ricerca full-Text e le funzioni di ricerca semantica (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- semantic search [SQL Server], system functions
ms.assetid: a61a3694-7604-4583-962e-fc30f771c6fa
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 04356970f56a3a2e5ee8f2a824b722801fe7262a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="full-text-search-and-semantic-search-functions-transact-sql"></a>Funzioni di ricerca full-text e semantica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questa sezione vengono descritte le funzioni di sistema correlate alla ricerca full-text e semantica.  
  
## <a name="full-text-search-functions"></a>Funzioni di ricerca full-text  
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)  
 Restituisce una tabella contenente una o più righe o nessuna riga per le colonne che includono corrispondenze più o meno esatte per singole parole e frasi, della prossimità delle parole a una certa distanza l'una dall'altra o di corrispondenze ponderate.  
  
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)  
 Restituisce una tabella di zero, uno o più righe per le colonne contenenti valori che corrispondono al significato e non solo all'esatta formulazione, del testo specificato *freetext_string*.  
  
## <a name="semantic-search-functions"></a>Funzioni per la ricerca semantica  
 [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)  
 Restituisce una tabella con zero, una o più righe per le frasi chiave associate a colonne nella tabella specificata.  
  
 [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)  
 Restituisce una tabella di zero, una o più righe di frasi chiave comuni in due documenti (un documento di origine e un documento corrispondente) il cui contenuto è semanticamente simile.  
  
 [semanticsimilaritytable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)  
 Restituisce una tabella di zero, una o più righe per le colonne il cui contenuto è semanticamente simile a un documento specificato.  
  
  
