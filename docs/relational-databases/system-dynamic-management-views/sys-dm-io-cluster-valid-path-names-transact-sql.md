---
title: Sys.dm io_cluster_valid_path_names (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_io_cluster_valid_path_names
- dm_io_cluster_valid_path_names_TSQL
- sys.dm_io_cluster_valid_path_names_TSQL
- dm_io_cluster_valid_path_names
dev_langs:
- TSQL
helpviewer_keywords:
- dm_io_cluster_valid_path_names
- sys.dm_io_cluster_valid_path_names
- cluster valid path names
- csv name
- cluster shared volume names
ms.assetid: 5bc8a0e5-6c72-425b-8c58-f276eb9add2c
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 376d0382179b0a54793a8dca9a657ee05ff646af
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmioclustervalidpathnames-transact-sql"></a>sys.dm_io_cluster_valid_path_names (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni su tutti i dischi condivisi validi, inclusi i volumi condivisi cluster, per un'istanza del cluster di failover di SQL Server. Se l'istanza non è in cluster, viene restituito un set di righe vuoto.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**path_name**|**nvarchar (512)**|Punto di montaggio del volume o percorso dell'unità che può essere utilizzato come directory radice per i file di log e di database. Non ammette i valori Null.|  
|**cluster_owner_node**|**Nvarchar(64)**|Proprietario corrente dell'unità. Per i volumi condivisi cluster il proprietario è il nodo che ospita il server di metadati. Non ammette i valori Null.|  
|**is_cluster_shared_volume**|**Bit**|Restituisce 1 se l'unità in cui si trova questo percorso è un volume condiviso cluster; in caso contrario, restituisce 0.|  
  
## <a name="remarks"></a>Osservazioni  
 Un'istanza del cluster di failover di SQL Server deve utilizzare l'archiviazione condivisa tra tutti i nodi dell'istanza del cluster di failover per l'archiviazione dei file di dati e di log. I dischi inclusi in questa vista sono quelli presenti nel gruppo di risorse del cluster associato all'istanza e sono gli unici dischi che possono essere utilizzati per l'archiviazione dei file di dati o di log.  
  
> [!NOTE]  
>  Questa vista sostituirà [DM io_cluster_shared_drives &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md) in una versione futura.  
  
## <a name="permissions"></a>Autorizzazioni  
 L'utente deve disporre dell'autorizzazione VIEW SERVER STATE per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata la vista sys.dm_io_cluster_valid_path_names per determinare le unità condivise in un'istanza del server di cluster:  
  
```  
SELECT * FROM sys.dm_io_cluster_valid_path_names;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_os_cluster_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [sys.dm_io_cluster_shared_drives &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

