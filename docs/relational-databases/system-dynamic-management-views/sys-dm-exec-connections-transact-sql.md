---
title: Sys.dm exec_connections (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 11/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_connections_TSQL
- sys.dm_exec_connections_TSQL
- sys.dm_exec_connections
- dm_exec_connections
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_connections dynamic management view
ms.assetid: 6bd46fe1-417d-452d-a9e6-5375ee8690d8
caps.latest.revision: 50
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1819fafef33e837d21cfd3d4622a2017cc821d68
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmexecconnections-transact-sql"></a>sys.dm_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sulle connessioni stabilite per questa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i dettagli di ogni connessione. Restituisce informazioni di connessione di livello server per SQL Server. Restituisce informazioni di connessione del database corrente per il Database SQL.  
  
> [!NOTE]
> Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oppure [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare [sys.dm_pdw_exec_connections &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-connections-transact-sql.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Identifica la sessione associata alla connessione Ammette i valori Null.|  
|most_recent_session_id|**int**|Rappresenta l'ID di sessione della richiesta più recente associata alla connessione. Le connessioni SOAP possono essere riutilizzate da un'altra sessione. Ammette i valori Null.|  
|connect_time|**datetime**|Timestamp relativo al momento in cui è stata stabilita la connessione. Non ammette i valori Null.|  
|net_transport|**nvarchar(40)**|Restituisce sempre **sessione** quando una connessione dispone di più set di risultati attivi (MARS) abilitato.<br /><br /> **Nota:** descrive il protocollo di trasporto fisico utilizzato dalla connessione. Non ammette i valori Null.|  
|protocol_type|**nvarchar(40)**|Specifica il tipo di protocollo del payload. Attualmente distingue tra TDS (TSQL) e SOAP. Ammette i valori Null.|  
|protocol_version|**int**|Versione del protocollo di accesso ai dati associato a questa connessione. Ammette i valori Null.|  
|endpoint_id|**int**|Identificatore che descrive il tipo di connessione. Il valore di endpoint_id può essere utilizzato per eseguire query nella vista sys.endpoints. Ammette i valori Null.|  
|encrypt_option|**nvarchar(40)**|Valore booleano che specifica se per la connessione è abilitata la crittografia. Non ammette i valori Null.|  
|auth_scheme|**nvarchar(40)**|Specifica lo schema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Autenticazione di Windows utilizzato con questa connessione. Non ammette i valori Null.|  
|node_affinity|**smallint**|Identifica il nodo di memoria con cui la connessione dispone di affinità. Non ammette i valori Null.|  
|num_reads|**int**|Numero di letture di byte che si sono verificati durante la connessione. Ammette i valori Null.|  
|num_writes|**int**|Numero di scritture di byte che si sono verificati durante la connessione. Ammette i valori Null.|  
|last_read|**datetime**|Timestamp dell'ultima lettura eseguita sulla connessione. Ammette i valori Null.|  
|last_write|**datetime**|Timestamp dell'ultima scrittura eseguita sulla connessione. Non ammette valori Null.|  
|net_packet_size|**int**|Dimensioni dei pacchetti di rete utilizzate per il trasferimento di informazioni e dati. Ammette i valori Null.|  
|client_net_address|**varchar(48)**|Indirizzo host del client che si connette al server. Ammette i valori Null.<br /><br /> Prima di V12 in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], questa colonna restituisce sempre NULL.|  
|client_tcp_port|**int**|Numero di porta del computer client associato alla connessione. Ammette i valori Null.<br /><br /> In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] questa colonna restituisce sempre un valore NULL.|  
|local_net_address|**varchar(48)**|Rappresenta l'indirizzo IP del server di destinazione della connessione. Disponibile solo per le connessioni che utilizzano il provider del trasporto TCP. Ammette i valori Null.<br /><br /> In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] questa colonna restituisce sempre un valore NULL.|  
|local_tcp_port|**int**|Rappresenta la porta TCP del server che verrebbe impiegata in caso di utilizzo del trasporto TCP per la connessione. Ammette i valori Null.<br /><br /> In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] questa colonna restituisce sempre un valore NULL.|  
|connection_id|**uniqueidentifier**|Identifica in modo univoco ogni connessione. Non ammette i valori Null.|  
|parent_connection_id|**uniqueidentifier**|Identifica la connessione primaria utilizzata dalla sessione MARS. Ammette i valori Null.|  
|most_recent_sql_handle|**varbinary(64)**|Handle SQL dell'ultima richiesta eseguita sulla connessione. La colonna most_recent_sql_handle è sempre sincronizzata con la colonna most_recent_session_id. Ammette i valori Null.|  
|pdw_node_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   

## <a name="physical-joins"></a>Join fisici  
 ![Join per DM exec_connections](../../relational-databases/system-dynamic-management-views/media/join-dm-exec-connections-1.gif "join per DM exec_connections")  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
||||  
|-|-|-|  
|dm_exec_sessions.session_id|dm_exec_connections.session_id|Uno-a-uno|  
|dm_exec_requests.connection_id|dm_exec_connections.connection_id|Molti-a-uno|  
|dm_broker_connections.connection_id|dm_exec_connections.connection_id|Uno-a-uno|  
  
## <a name="examples"></a>Esempi  
 Query tipica per raccogliere informazioni su una connessione query personalizzata.  
  
```sql  
SELECT   
    c.session_id, c.net_transport, c.encrypt_option,   
    c.auth_scheme, s.host_name, s.program_name,   
    s.client_interface_name, s.login_name, s.nt_domain,   
    s.nt_user_name, s.original_login_name, c.connect_time,   
    s.login_time   
FROM sys.dm_exec_connections AS c  
JOIN sys.dm_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = @@SPID;  
```  
  
## <a name="see-also"></a>Vedere anche  

 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


