---
title: sys.dm_pdw_node_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8e263b65-81d0-49d0-8873-62ef424369d6
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 873f83991cbc89ff3e552646c04e8657b005181b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmpdwnodestatus-transact-sql"></a>sys.dm_pdw_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contiene informazioni aggiuntive (tramite [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)) sulle prestazioni e dello stato di tutti i nodi dello strumento. Contiene una riga per ogni nodo nel dispositivo.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Id numerico univoco associato al nodo.<br /><br /> Chiave per la visualizzazione.|Univoche tra il dispositivo, indipendentemente dal tipo.|  
|process_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|process_name|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|allocated_memory|**bigint**|Totale di memoria su questo nodo.||  
|available_memory|**bigint**|Memoria totale disponibile su questo nodo.||  
|process_cpu_usage|**bigint**|Utilizzo CPU totale del processo, in tick.||  
|total_cpu_usage|**bigint**|Utilizzo totale della CPU, in tick.||  
|thread_count|**bigint**|Numero totale di thread in uso su questo nodo.||  
|handle_count|**bigint**|Numero totale di handle in uso su questo nodo.||  
|total_elapsed_time|**bigint**|Tempo totale trascorso dal sistema avviare o riavviare.|Tempo totale trascorso dal sistema avviare o riavviare. Se total_elapsed_time supera il valore massimo per un numero intero (24.8 giorni, in millisecondi), errore di materializzazione scadenza comporterà un overflow.<br /><br /> Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
|is_available|**bit**|Flag che indica se questo nodo è disponibile.||  
|sent_time|**datetime**|Ultima volta da questo nodo è stato inviato un pacchetto di rete.||  
|received_time|**datetime**|Ultima volta che un pacchetto di rete è stato ricevuto da questo nodo.||  
|error_id|**nvarchar(36)**|Identificatore univoco dell'ultimo errore che si sono verificati in questo nodo.||  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
