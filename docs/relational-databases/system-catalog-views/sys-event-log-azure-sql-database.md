---
title: Sys. event_log (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- event_log
- sys.event_log_TSQL
- event_log_TSQL
- sys.event_log
dev_langs:
- TSQL
helpviewer_keywords:
- event_log
- sys.event_log
ms.assetid: ad5496b5-e5c7-4a18-b5a0-3f985d7c4758
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 5f871501b63bd9823c5a44872224439e8df07a9c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="syseventlog-azure-sql-database"></a>sys.event_log (Database di SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce l'esito positivo [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] deadlock, errori di connessione e connessioni di database. È possibile usare queste informazioni per tenere traccia dell'attività del database con il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] o per risolvere i problemi relativi.  
  
> [!CAUTION]  
>  Per le installazioni che dispongono di un numero elevato di database o un numero elevato di account di accesso, l'attività in sys. event_log può causare limitazioni delle prestazioni, utilizzo elevato della CPU e causare errori di accesso. Query di Sys. event_log possono contribuire al problema. Microsoft sta cercando di risolvere il problema. Nel frattempo, per ridurre l'impatto di questo problema, è possibile limitare le query di Sys. event_log. Gli utenti del plug-in NewRelic SQL Server devono visitare [ottimizzazioni di prestazioni e ottimizzazione di plug-in Database SQL di Microsoft Azure](https://discuss.newrelic.com/t/microsoft-azure-sql-database-plugin-tuning-performance-tweaks/30729) per ulteriori informazioni sulla configurazione.  
  
 Il `sys.event_log` vista contiene le colonne seguenti.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|Nome del database. Se la connessione ha esito negativo e l'utente non ha specificato un nome di database, questa colonna è vuota.|  
|**start_time**|**datetime2**|Data e ora UTC dell'inizio dell'intervallo di aggregazione. In caso di eventi aggregati, l'ora è sempre un multiplo di 5 minuti. Esempio:<br /><br /> 28/09/2011 16:00:00<br />'2011-09-28 16:05:00'<br />'2011-09-28 16:10:00'|  
|**end_time**|**datetime2**|Data e ora UTC della fine dell'intervallo di aggregazione. Eventi aggregati, **End_time** è sempre esattamente 5 minuti dopo rispetto al relativo **start_time** nella stessa riga. Per gli eventi che non sono aggregati, **start_time** e **end_time** uguale l'effettiva data e ora UTC dell'evento.|  
|**event_category**|**nvarchar(64)**|Componente di alto livello tramite cui è stato generato l'evento.<br /><br /> Vedere [tipi di evento](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) per un elenco di valori possibili.|  
|**event_type**|**nvarchar(64)**|Tipo di evento.<br /><br /> Vedere [tipi di evento](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) per un elenco di valori possibili.|  
|**event_subtype**|**int**|Sottotipo dell'evento in corso.<br /><br /> Vedere [tipi di evento](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) per un elenco di valori possibili.|  
|**event_subtype_desc**|**nvarchar(64)**|Descrizione del sottotipo di evento.<br /><br /> Vedere [tipi di evento](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) per un elenco di valori possibili.|  
|**severity**|**int**|Gravità dell'errore. I valori possibili sono:<br /><br /> 0 = Informazioni<br />1 = Avviso<br />2 = errore|  
|**event_count**|**int**|Il numero di volte in cui si è verificato questo evento per il database specificato nell'intervallo di tempo specificato (**start_time** e **end_time**).|  
|**description**|**nvarchar(max)**|Descrizione dettagliata dell'evento.<br /><br /> Vedere [tipi di evento](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) per un elenco di valori possibili.|  
|**additional_data**|**XML**|*Nota: Questo valore è sempre NULL per il Database SQL di Azure V12. Vedere [esempi](#Deadlock) sezione su come recuperare gli eventi deadlock per (V12).*<br /><br /> Per **Deadlock** eventi, questa colonna contiene l'evento deadlock graph. La colonna è NULL per altri tipi di evento. |  
  
##  <a name="EventTypes"></a> Tipi di evento  
 Gli eventi registrati in ogni riga in questa vista vengono identificati per categoria (**event_category**), tipo di evento (**event_type**) e sottotipo (**event_subtype**). Nella tabella seguente sono elencati i tipi di eventi raccolti in questa vista.  
  
 Per gli eventi di **connettività** categoria, le informazioni di riepilogo sono disponibile nella vista sys. database_connection_stats.  
  
> [!NOTE]  
>  La vista non include tutti gli eventi possibili del database [!INCLUDE[ssSDS](../../includes/sssds-md.md)], ma solo quelli elencati. Nelle versioni future del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] potranno venire aggiunte categorie, tipi di evento e sottotipi.  
  
|**event_category**|**event_type**|**event_subtype**|**event_subtype_desc**|**severity**|**description**|  
|-------------------------|---------------------|------------------------|------------------------------|------------------|---------------------|  
|**Connettività**|**connection_successful**|0|**connection_successful**|0|Connessione al database effettuata.|  
|**Connettività**|**connection_failed**|0|**invalid_login_name**|2|Il nome dell'account di accesso non è valido in questa versione di SQL Server.|  
|**Connettività**|**connection_failed**|1|**windows_auth_not_supported**|2|Account di accesso di Windows non supportati in questa versione di SQL Server.|  
|**Connettività**|**connection_failed**|2|**attach_db_not_supported**|2|L'utente ha richiesto di allegare un file di database che non è supportato.|  
|**Connettività**|**connection_failed**|3|**change_password_not_supported**|2|L'utente ha richiesto di modificare la password dell'accesso utente, operazione non supportata.|  
|**Connettività**|**connection_failed**|4|**login_failed_for_user**|2|Accesso non riuscito per l'utente.|  
|**Connettività**|**connection_failed**|5|**login_disabled**|2|L'account di accesso è stato disabilitato.|  
|**Connettività**|**connection_failed**|6|**failed_to_open_db**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> Impossibile aprire il database. È possibile che il database non esista o che non sia stata effettuata l'autenticazione per aprire il database.|  
|**Connettività**|**connection_failed**|7|**blocked_by_firewall**|2|Indirizzo IP del client non consentito per l'accesso al server.|  
|**Connettività**|**connection_failed**|8|**client_close**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> È possibile che si sia verificato un timeout del client nel tentativo di stabilire la connessione. Provare ad aumentare il timeout della connessione.|  
|**Connettività**|**connection_failed**|9|**Riconfigurazione**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> Impossibile stabilire la connessione poiché era in corso una riconfigurazione del database.|  
|**Connettività**|**connection_terminated**|0|**idle_connection_timeout**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> Il tempo di inattività della connessione è stato maggiore rispetto alla soglia definita dal sistema.|  
|**Connettività**|**connection_terminated**|1|**Riconfigurazione**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> La sessione è stata terminata a causa di una riconfigurazione del database.|  
|**Connettività**|**La limitazione delle richieste**|*\<codice motivo >*|**reason_code**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> La richiesta è limitata.  Codice motivo limitazione:  *\<codice motivo >*. Per ulteriori informazioni, vedere [la limitazione del motore](http://msdn.microsoft.com/library/windowsazure/dn338079.aspx).|  
|**Connettività**|**throttling_long_transaction**|40549|**long_transaction**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> Sessione terminata perché è presente una transazione a lunga esecuzione. Provare ad abbreviare la transazione. Per ulteriori informazioni, vedere [i limiti delle risorse](http://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**Connettività**|**throttling_long_transaction**|40550|**excessive_lock_usage**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> Sessione terminata perché ha acquisito troppi blocchi. Provare a leggere o modificare meno righe in una sola transazione. Per ulteriori informazioni, vedere [i limiti delle risorse](http://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**Connettività**|**throttling_long_transaction**|40551|**excessive_tempdb_usage**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> Sessione terminata a causa di un utilizzo eccessivo di TEMPDB. Provare a modificare la query per ridurre l'utilizzo dello spazio delle tabelle temporanee. Per ulteriori informazioni, vedere [i limiti delle risorse](http://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**Connettività**|**throttling_long_transaction**|40552|**excessive_log_space_usage**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> Sessione terminata a causa di un utilizzo eccessivo dello spazio del log delle transazioni. Provare a modificare meno righe in una sola transazione. Per ulteriori informazioni, vedere [i limiti delle risorse](http://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**Connettività**|**throttling_long_transaction**|40553|**excessive_memory_usage**|2|*Nota: Si applica solo a SQL Azure Database V11.*<br /><br /> Sessione terminata a causa di un utilizzo eccessivo della memoria. Provare a modificare la query per elaborare meno righe. Per ulteriori informazioni, vedere [i limiti delle risorse](http://msdn.microsoft.com/library/windowsazure/dn338081.aspx).|  
|**Motore di**|**deadlock**|0|**deadlock**|2|Si è verificato un deadlock.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Gli utenti con autorizzazioni di accesso di **master** database hanno accesso in sola lettura a questa vista.  
  
## <a name="remarks"></a>Osservazioni  
  
### <a name="event-aggregation"></a>Aggregazione evento  
 Le informazioni sull'evento per questa vista vengono raccolte e aggregate in intervalli di 5 minuti. Il **event_count** colonna rappresenta il numero di volte in cui **event_type** e **event_subtype** si è verificato per un database specifico all'interno di un determinato intervallo di tempo.  
  
> [!NOTE]  
>  Alcuni eventi, ad esempio i deadlock, non vengono aggregati. Per questi eventi, **event_count** sarà 1 e **start_time** e **end_time** sarà uguale l'effettiva data e ora UTC quando si è verificato l'evento.  
  
 Ad esempio, se un utente non è riuscito a connettersi al database Database1 per sette volte tra le 11:00 e le 11:05 del 2/5/2012 (UTC) a causa di un nome account di accesso non valido, queste informazioni sono disponibili in una singola riga di questa vista:  
  
|**database_name**|**start_time**|**end_time**|**event_category**|**event_type**|**event_subtype**|**event_subtype_desc**|**severity**|**event_count**|**description**|**additional_data**|  
|------------------------|---------------------|-------------------|-------------------------|---------------------|------------------------|------------------------------|------------------|----------------------|---------------------|--------------------------|  
|`Database1`|`2012-02-05 11:00:00`|`2012-02-05 11:05:00`|`connectivity`|`connection_failed`|`4`|`login_failed_for_user`|`2`|`7`|`Login failed for user.`|`NULL`|  
  
### <a name="interval-starttime-and-endtime"></a>start_time e end_time dell'intervallo  
 Un evento è incluso in un intervallo di aggregazione quando si verifica l'evento *sul* o *dopo * * * start_time** e *prima * * * end_time** per tale intervallo. Ad esempio, un evento che si verifica esattamente il `2012-10-30 19:25:00.0000000` è incluso solo nel secondo intervallo indicato di seguito:  
  
```  
start_time                    end_time  
2012-10-30 19:20:00.0000000   2012-10-30 19:25:00.0000000  
2012-10-30 19:25:00.0000000   2012-10-30 19:30:00.0000000  
```  
  
### <a name="data-updates"></a>Aggiornamenti dei dati  
 I dati in questa vista vengono accumulati nel tempo. In genere, vengono accumulati entro un'ora dall'inizio dell'intervallo di aggregazione, ma la visualizzazione di tutti i dati nella vista potrebbe richiedere fino a un massimo di 24 ore. Durante questo tempo, le informazioni contenute all'interno di una singola riga possono essere aggiornate periodicamente.  
  
### <a name="data-retention"></a>Mantenimento dei dati  
 I dati in questa vista vengono mantenuti per un massimo di 30 giorni o meno, a seconda del numero di database nel server logico e del numero di eventi univoci generati da ciascun database. Per prolungare il mantenimento di queste informazioni, copiare i dati in un database separato. Dopo aver creato una copia iniziale della vista, le relative righe possono essere aggiornate quando i dati vengono accumulati. Per mantenere aggiornata la copia dei dati, eseguire periodicamente un'analisi delle righe della tabella per cercare un eventuale aumento del numero di eventi di righe esistenti e per identificare le righe nuove (è possibile effettuare questa operazione per le righe univoche mediante le ore di inizio e di fine), quindi aggiornare la copia dei dati con queste modifiche.  
  
### <a name="errors-not-included"></a>Errori non inclusi  
 In questa vista non possono essere incluse tutte le informazioni relative a connessioni ed errori:  
  
-   Questa vista non include tutti [!INCLUDE[ssSDS](../../includes/sssds-md.md)] gli errori che potrebbero verificarsi, solo quelle specificate nel database [tipi di evento](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md#EventTypes) in questo argomento.  
  
-   Se si verifica un errore del computer nel data center del [!INCLUDE[ssSDS](../../includes/sssds-md.md)], è possibile che dalla tabella eventi manchi una piccola quantità di dati per il server logico.  
  
-   Se un indirizzo IP è stato bloccato tramite DoSGuard, gli eventi di tentativi di connessione dall'indirizzo IP in questione non possono essere raccolti, né verranno visualizzati in questa vista.  
  
## <a name="examples"></a>Esempi  
  
### <a name="simple-examples"></a>Esempi semplici  
 La query seguente restituisce tutti gli eventi che si sono verificati tra le ore 12:00 del 9/25/2011 e le ore 12:00 del 9/28/2011 (UTC). Per impostazione predefinita, vengono ordinati i risultati della query **start_time** (ordine crescente).  
  
```  
SELECT * FROM sys.event_log   
WHERE start_time >= '2011-09-25:12:00:00'   
    AND end_time <= '2011-09-28 12:00:00';  
```  
  
 La query seguente restituisce tutti gli eventi deadlock per il database Database1 (si applica solo a Azure SQL Database V11).  
  
```  
SELECT * FROM sys.event_log   
WHERE event_type = 'deadlock'   
    AND database_name = 'Database1';  
```  
<a name="Deadlock"></a> La query seguente restituisce tutti gli eventi deadlock per il database Database1 (si applica solo ai Database SQL di Azure V12).  
  
```  
WITH CTE AS (  
       SELECT CAST(event_data AS XML)  AS [target_data_XML]   
   FROM sys.fn_xe_telemetry_blob_target_read_file('dl', null, null, null)  
)  
SELECT target_data_XML.value('(/event/@timestamp)[1]', 'DateTime2') AS Timestamp,  
target_data_XML.query('/event/data[@name=''xml_report'']/value/deadlock') AS deadlock_xml,  
target_data_XML.query('/event/data[@name=''database_name'']/value').value('(/value)[1]', 'nvarchar(100)') AS db_name  
FROM CTE   
  
```  
  
  
 La query seguente restituisce la limitazione a livello hardware per gli eventi dei thread di lavoro SQL che si sono verificati tra le 10:00 e le 11:00 del 9/25/2011 (UTC).  
  
```  
SELECT * FROM sys.event_log   
WHERE event_type = 'throttling'   
    AND event_subtype = 4194307   
    AND start_time >= '2011-09-25 10:00:00'   
    AND end_time <= '2011-09-25 11:00:00';  
```  
  
### <a name="db-scoped-extended-event"></a>Eventi estesi con ambito database  
 Utilizzare il seguente codice di esempio per impostare la sessione di eventi estesi (XEvent) con ambito database:  
  
```sql  
IF EXISTS  
    (SELECT * from sys.database_event_sessions  
        WHERE name = 'azure_monitor_deadlock_session')  
BEGIN  
    ALTER EVENT SESSION azure_monitor_deadlock_session  
        ON DATABASE  
        DROP TARGET package0.ring_buffer;  
  
    DROP EVENT SESSION azure_monitor_deadlock_session  
        ON DATABASE;  
END  
  
CREATE EVENT SESSION azure_monitor_deadlock_session  
    ON DATABASE  
    ADD EVENT sqlserver.database_xml_deadlock_report  
    ADD TARGET package0.ring_buffer  
    (  
        SET max_memory = 2048, max_events_limit = 10  
    )  
    WITH (STARTUP_STATE = ON,  
          EVENT_RETENTION_MODE = ALLOW_SINGLE_EVENT_LOSS);  
  
ALTER EVENT SESSION azure_monitor_deadlock_session  
    ON DATABASE  
    STATE = START;  
```  
  
### <a name="check-for-deadlock"></a>Controllo di un Deadlock

Utilizzare la query seguente per controllare se è presente un deadlock.  
  
```sql  
WITH CTE AS (  
    SELECT CAST(xet.target_data AS XML)  AS [target_data_XML]  
        FROM            sys.dm_xe_database_session_targets AS xet  
             INNER JOIN sys.dm_xe_database_sessions        AS xe  
                 ON (xe.address = xet.event_session_address)  
        WHERE xe.name = 'azure_monitor_deadlock_session'  
)  
, CTE2 AS (  
    SELECT  
            T2.EventData.query('.').value(  
                '(/event/@timestamp)[1]', 'DateTime2') AS Timestamp,  
            T2.EventData.query('.').query(  
                '(/event/data/value/deadlock)[1]')     AS deadlock_xml  
        FROM CTE  
            CROSS Apply [target_data_XML].nodes(  
                '/RingBufferTarget/event') AS T2(EventData)  
)  
SELECT * FROM CTE2;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi nel Database SQL di Azure](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)  
  
  
