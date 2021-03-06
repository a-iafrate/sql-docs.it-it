---
title: sys.dm_resource_governor_resource_pools (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pools_TSQL
- dm_resource_governor_resource_pools_TSQL
- sys.dm_resource_governor_resource_pools
- dm_resource_governor_resource_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_resource_pools dynamic management view
ms.assetid: 9bfc926e-d8bc-40f8-9229-ab1f8a1e69c5
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ef308528fe5926c760ea2e80fda79c141c429513
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmresourcegovernorresourcepools-transact-sql"></a>sys.dm_resource_governor_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Restituisce le informazioni sullo stato del pool di risorse corrente, la configurazione del pool di risorse corrente e le statistiche del pool di risorse.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_resource_governor_resource_pools**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|ID del pool di risorse. Non ammette i valori Null.|  
|name|**sysname**|Nome del pool di risorse. Non ammette i valori Null.|  
|statistics_start_time|**datetime**|Ora di reimpostazione delle statistiche per questo pool. Non ammette i valori Null.|  
|total_cpu_usage_ms|**bigint**|Utilizzo della CPU cumulativo, espresso in millisecondi, dalla reimpostazione delle statistiche di Resource Governor. Non ammette i valori Null.|  
|cache_memory_kb|**bigint**|Utilizzo corrente della memoria cache totale in kilobyte. Non ammette i valori Null.|  
|compile_memory_kb|**bigint**|Utilizzo corrente della memoria prelevata totale in kilobyte (KB). La maggioranza dell'utilizzo avviene per la compilazione e l'ottimizzazione, ma può includere anche altri utenti della memoria. Non ammette i valori Null.|  
|used_memgrant_kb|**bigint**|Il totale corrente della memoria usata (prelevata) dalle concessioni di memoria. Non ammette i valori Null.|  
|total_memgrant_count|**bigint**|Il conteggio cumulativo delle concessioni di memoria nel pool di risorse. Non ammette i valori Null.|  
|total_memgrant_timeout_count|**bigint**|Il conteggio cumulativo dei timeout delle concessioni di memoria nel pool di risorse. Non ammette i valori Null.|  
|active_memgrant_count|**int**|Il conteggio corrente delle concessioni di memoria. Non ammette i valori Null.|  
|active_memgrant_kb|**bigint**|La somma, in kilobyte (KB), delle concessioni correnti di memoria. Non ammette i valori Null.|  
|memgrant_waiter_count|**int**|Il conteggio delle query attualmente in sospeso nelle concessioni di memoria. Non ammette i valori Null.|  
|max_memory_kb|**bigint**|Quantità massima di memoria, in kilobyte, disponibile per il pool di risorse. Si basa sulle impostazioni correnti e sullo stato del server. Non ammette i valori Null.|  
|used_memory_kb|**bigint**|Quantità di memoria utilizzata, in kilobyte, per il pool di risorse. Non ammette i valori Null.|  
|target_memory_kb|**bigint**|Quantità di memoria di destinazione, in kilobyte, che il pool di risorse sta cercando di ottenere. Si basa sulle impostazioni correnti e sullo stato del server. Non ammette i valori Null.|  
|out_of_memory_count|**bigint**|Numero di allocazioni della memoria non riuscite nel pool dalla reimpostazione delle statistiche di Resource Governor. Non ammette i valori Null.|  
|min_cpu_percent|**int**|Configurazione corrente della larghezza di banda media garantita della CPU per tutte le richieste nel pool di risorse, in caso di contesa di CPU. Non ammette i valori Null.|  
|max_cpu_percent|**int**|Configurazione corrente per la larghezza di banda media massima della CPU concessa per tutte le richieste nel pool di risorse, in caso di contesa di CPU. Non ammette i valori Null.|  
|min_memory_percent|**int**|Configurazione corrente della quantità di memoria garantita per tutte le richieste nel pool di risorse, in caso di contesa di memoria. Non è condivisa con altri pool di risorse. Non ammette i valori Null.|  
|max_memory_percent|**int**|Configurazione corrente della percentuale di memoria totale del server utilizzabile dalle richieste in questo pool di risorse. Non ammette i valori Null.|  
|cap_cpu_percent|**int**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Limite di utilizzo massimo della larghezza di banda della CPU concesso per tutte le richieste nel pool di risorse. Limita il livello massimo della larghezza di banda della CPU al livello specificato. L'intervallo consentito per il valore è compreso tra 1 e 100. Non ammette i valori Null.|  
|min_iops_per_volume|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> L'I/O minimo al secondo per impostazione del volume di disco per questo pool. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.|  
|max_iops_per_volume|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> L'I/O massimo al secondo per impostazione del volume di disco per questo pool. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.|  
|read_io_queued_total|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il totale degli I/O di lettura accodati dalla reimpostazione di Resource Governor. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.|  
|read_io_issued_total|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il totale degli I/O di lettura generati dalla reimpostazione delle statistiche di Resource Govenor. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.|  
|read_io_completed_total|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il totale degli I/O di lettura completati dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null.|  
|read_io_throttled_total|**int**|Il totale degli I/O di lettura limitati dalla reimpostazione delle statistiche di Resource Governor. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.|  
|read_bytes_total|**bigint**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il numero totale di byte letti dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null.|  
|read_io_stall_total_ms|**bigint**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il tempo totale espresso in millisecondi tra l'arrivo e il completamento degli I/O di lettura. Non ammette i valori Null. |  
|read_io_stall_queued_ms|**bigint**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il tempo totale espresso in millisecondi tra l'arrivo degli I/O di lettura e il problema. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.<br /><br /> Per determinare se l'impostazione dei / o per il pool è causa di latenza, sottrarre **read_io_stall_queued_ms** da **read_io_stall_total_ms**.|  
|write_io_queued_total|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il totale degli I/O di scrittura accodati dalla reimpostazione delle statistiche di Resource Govenor. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.|  
|write_io_issued_total|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il totale degli I/O di scrittura generati dalla reimpostazione delle statistiche di Resource Govenor. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.|  
|write_io_completed_total|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il totale degli I/O di scrittura completati dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null|  
|write_io_throttled_total|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il totale degli I/O di scrittura limitati dalla reimpostazione delle statistiche di Resource Governor. Non ammette i valori Null|  
|write_bytes_total|**bigint**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il numero totale di byte scritti dalla reimpostazione delle statistiche di Resource Govenor. Non ammette i valori Null.|  
|write_io_stall_total_ms|**bigint**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il tempo totale espresso in millisecondi tra l'arrivo e il completamento degli I/O di scrittura. Non ammette i valori Null. |  
|write_io_stall_queued_ms|**bigint**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il tempo totale espresso in millisecondi tra l'arrivo degli I/O di scrittura e il problema. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.<br /><br /> Si tratta del ritardo introdotto dalla governance delle risorse di I/O.|  
|io_issue_violations_total|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Totale delle violazioni di generazione di I/O. Vale a dire, il numero di volte che la frequenza di generazione di I/O era inferiore alla frequenza riservata. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.|  
|io_issue_delay_total_ms|**bigint**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il tempo totale espresso in millisecondi tra la generazione pianificata e quella effettiva degli I/O. Ammette i valori Null. Null se il pool di risorse non è governato per l'I/O. Vale a dire che l'impostazione MIN_IOPS_PER_VOLUME del pool di risorse e l'impostazione MAX_IOPS_PER_VOLUME sono 0.|  
|pdw_node_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 I gruppi del carico di lavoro e i pool di risorse di Resource Governor presentano un mapping molti-a-uno. Di conseguenza, molte delle statistiche dei pool di risorse derivano da quelle del gruppo del carico di lavoro.  
  
 Questa vista a gestione dinamica mostra la configurazione in memoria. Per visualizzare i metadati di configurazione archiviati, utilizzare la vista del catalogo resource_governor_resource_pools.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [sys.resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  



