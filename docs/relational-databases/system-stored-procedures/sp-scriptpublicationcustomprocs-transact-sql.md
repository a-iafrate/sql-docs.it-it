---
title: sp_scriptpublicationcustomprocs (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_scriptpublicationcustomprocs
- sp_scriptpublicationcustomprocs_TSQL
helpviewer_keywords:
- sp_scriptpublicationcustomprocs
ms.assetid: b06102d5-4284-4834-b126-bc0baea49be5
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 7e3cad96acad0e5e08d92a70cd795a6022be26f5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spscriptpublicationcustomprocs-transact-sql"></a>sp_scriptpublicationcustomprocs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea gli script delle procedure personalizzate INSERT, UPDATE e DELETE per tutti gli articoli di tabella in una pubblicazione in cui è abilitata l'opzione per la generazione automatica dello schema delle procedure personalizzate. **sp_scriptpublicationcustomprocs** è particolarmente utile per la configurazione di sottoscrizioni per cui lo snapshot viene applicato manualmente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_scriptpublicationcustomprocs [ @publication = ] 'publication_name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publication**=] **'***publication_name***'**  
 Nome della pubblicazione. *publication_name* viene **sysname** non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Restituisce un set di risultati è costituito da un singolo **nvarchar (4000)** colonna. Il set di risultati forma l'istruzione CREATE PROCEDURE completa utilizzata per creare la stored procedure personalizzata.  
  
## <a name="remarks"></a>Osservazioni  
 Lo script delle procedure personalizzate non viene creato per gli articoli senza l'opzione per la generazione automatica dello schema delle procedure personalizzate (0x2).  
  
 Le procedure seguenti vengono utilizzate da **sp_scriptpublicationcustomprocs** per creare procedure nel sottoscrittore e non deve essere eseguito direttamente:  
  
 **sp_script_reconciliation_delproc**  
  
 **sp_script_reconciliation_insproc**  
  
 **sp_script_reconciliation_vdelproc**  
  
 **sp_script_reconciliation_xdelproc**  
  
 **sp_scriptdelproc**  
  
 **sp_scriptinsproc**  
  
 **sp_scriptmappedupdproc**  
  
 **sp_scriptupdproc**  
  
 **sp_scriptvdelproc**  
  
 **sp_scriptvupdproc**  
  
 **sp_scriptxdelproc**  
  
 **sp_scriptxupdproc**  
  
## <a name="permissions"></a>Autorizzazioni  
 Eseguire l'autorizzazione viene concessa per **pubblica**; un controllo della sicurezza procedurale viene eseguito all'interno di questa stored procedure per limitare l'accesso ai membri del **sysadmin** ruolo predefinito del server e **DB _ proprietario** ruolo predefinito del database nel database corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
