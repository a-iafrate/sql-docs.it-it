---
title: sys.dm_xtp_transaction_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_xtp_transaction_stats_TSQL
- dm_xtp_transaction_stats
- sys.dm_xtp_transaction_stats_TSQL
- sys.dm_xtp_transaction_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_transaction_stats dynamic management view
ms.assetid: 9389f48d-0de5-47bd-9821-4db8f04504e4
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4bf4a371e65a6457453d6a98d37e88a5f8878ba8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmxtptransactionstats-transact-sql"></a>sys.dm_xtp_transaction_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Indica le statistiche sulle transazioni eseguite dopo che il server è stato avviato.  
  
 Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|total_count|**bigint**|Numero totale di transazioni eseguite nel motore di database OLTP in memoria.|  
|read_only_count|**bigint**|Numero di transazioni di sola lettura.|  
|total_aborts|**bigint**|Numero totale di transazioni che sono state arrestate, attraverso un arresto di sistema o dell'utente.|  
|user_aborts|**bigint**|Numero di arresti avviati dal sistema. Possono essere dovuti a conflitti di scrittura, errori di convalida o di dipendenza.|  
|validation_failures|**bigint**|Numero di volte che una transazione è stata interrotta a causa di un errore di convalida.|  
|dependencies_taken|**bigint**|Solo per uso interno.|  
|dependencies_failed|**bigint**|Numero di volte che una transazione viene interrotta perché una transazione da cui dipendeva è stata interrotta.|  
|savepoint_create|**bigint**|Numero di punti di salvataggio creati. Viene creato un nuovo punto di salvataggio per ogni blocco atomico.|  
|savepoint_rollbacks|**bigint**|Numero di rollback a un punto di salvataggio precedente.|  
|savepoint_refreshes|**bigint**|Solo per uso interno.|  
|log_bytes_written|**bigint**|Numero totale di byte scritti nei record del log OLTP in memoria.|  
|log_IO_count|**bigint**|Numero totale di transazioni che richiedono attività di I/O nel log. Considera unicamente le transazioni sulle tabelle durevoli.|  
|phantom_scans_started|**bigint**|Solo per uso interno.|  
|phatom_scans_retries|**bigint**|Solo per uso interno.|  
|phantom_rows_touched|**bigint**|Solo per uso interno.|  
|phantom_rows_expiring|**bigint**|Solo per uso interno.|  
|phantom_rows_expired|**bigint**|Solo per uso interno.|  
|phantom_rows_expired_removed|**bigint**|Solo per uso interno.|  
|scans_started|**bigint**|Solo per uso interno.|  
|scans_retried|**bigint**|Solo per uso interno.|  
|rows_returned|**bigint**|Solo per uso interno.|  
|rows_touched|**bigint**|Solo per uso interno.|  
|rows_expiring|**bigint**|Solo per uso interno.|  
|rows_expired|**bigint**|Solo per uso interno.|  
|rows_expired_removed|**bigint**|Solo per uso interno.|  
|rows_inserted|**bigint**|Solo per uso interno.|  
|rows_updated|**bigint**|Solo per uso interno.|  
|rows_deleted|**bigint**|Solo per uso interno.|  
|write_conflicts|**bigint**|Solo per uso interno.|  
|unique_constraint_violations|**bigint**|Numero totale di violazioni di vincoli univoci.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste a gestione dinamica tabella ottimizzazione della memoria &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
