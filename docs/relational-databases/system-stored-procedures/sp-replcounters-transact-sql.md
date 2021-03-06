---
title: sp_replcounters (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_replcounters
- sp_replcounters_TSQL
helpviewer_keywords:
- sp_replcounters
ms.assetid: fe585b1f-edda-421f-81d6-8a03a3a535d2
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5cc67b000b231146c9544ea7ef1bc1e2a3b6b667
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spreplcounters-transact-sql"></a>sp_replcounters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le statistiche di replica relative a latenza, velocità effettiva e numero delle transazioni per ogni database pubblicato. Questa stored procedure viene eseguita in qualsiasi database del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replcounters  
  
```  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**Database**|**sysname**|Nome del database.|  
|**Transazioni replicate**|**int**|Numero di transazioni nel log in attesa di recapito al database di distribuzione.|  
|**Frequenza di replica trans/sec**|**float**|Numero medio di transazioni al secondo recapitate al database di distribuzione.|  
|**Latenza di replica**|**float**|Tempo medio di permanenza delle transazioni nel log prima della distribuzione, espresso in secondi.|  
|**Replbeginlsn**|**binary(10)**|Numero di sequenza del file di log (LSN) corrispondente al punto di troncamento corrente nel log.|  
|**Replnextlsn**|**binary(10)**|LSN del record di commit successivo in attesa di recapito al database di distribuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replcounters** viene utilizzata nella replica transazionale.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **db_owner** ruolo predefinito del database o **sysadmin** ruolo predefinito del server.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
