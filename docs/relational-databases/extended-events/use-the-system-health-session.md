---
title: Usare la sessione system_health | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: xevents
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 57bdc59b3b5db69fdf01737b0a850725e9b17f88
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="use-the-systemhealth-session"></a>Utilizzare la sessione system_health
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  La sessione system_health è una sessione di eventi estesi inclusa per impostazione predefinita in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa sessione viene avviata automaticamente all'avvio del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] e viene eseguita senza effetti rilevanti sulle prestazioni. La sessione raccoglie dati del sistema che consentono di semplificare la risoluzione dei problemi relativi alle prestazioni nel [!INCLUDE[ssDE](../../includes/ssde-md.md)]. È pertanto consigliabile non arrestare o eliminare la sessione.  
  
 La sessione raccoglie le informazioni seguenti:  
  
-   Sql_text e session_id per qualsiasi sessione in cui si verifica un errore con gravità >=20.  
  
-   Sql_text e session_id per qualsiasi sessione in cui si verifica un errore relativo alla memoria. ad esempio gli errori 17803, 701, 802, 8645, 8651, 8657 e 8902.  
  
-   Un record di qualsiasi problema dell'utilità di pianificazione relativo alla mancata cessione del controllo. Questi problemi sono inclusi come errori 17883 nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Qualsiasi deadlock rilevato.  
  
-   Callstack, sql_text e session_id per qualsiasi sessione in attesa su latch (o altre risorse interessanti) per un tempo maggiore a 15 secondi.  
  
-   Callstack, sql_text e session_id per qualsiasi sessione in attesa su blocchi per un tempo maggiore a 30 secondi.  
  
-   Callstack, sql_text e session_id per qualsiasi sessione rimasta in attesa per molto tempo a causa di attese preemptive. La durata varia in base al tipo di attesa. In un'attesa preemptive [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in attesa di chiamate API esterne.  
  
-   callstack e session_id per l'allocazione CLR e per errori di allocazione virtuali.  
  
-   Eventi ring_buffer per il broker di memoria, il monitoraggio dell'utilità di pianificazione, la memoria insufficiente del nodo di memoria, la sicurezza e la connettività.  
  
-   Risultati del componente di sistema da sp_server_diagnostics.  
  
-   Integrità dell'istanza raccolta da scheduler_monitor_system_health_ring_buffer_recorded.  
  
-   Errori di allocazione CLR.  
  
-   Errori di connettività utilizzando connectivity_ring_buffer_recorded.  
  
-   Errori di sicurezza utilizzando security_error_ring_buffer_recorded.  
  
## <a name="viewing-the-session-data"></a>Visualizzazione dei dati della sessione  
 Nella sessione viene utilizzata la destinazione del buffer circolare per archiviare i dati. Per visualizzare i dati della sessione, utilizzare la query seguente:  
  
```  
SELECT CAST(xet.target_data as xml) FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe  
ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
Per visualizzare i dati sessione dell'evento file, utilizzare l'interfaccia utente degli eventi estesi disponibili in Management Studio. Per altre informazioni, vedere [Visualizzazione avanzata dei dati di destinazione da eventi estesi in SQL Server](../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md).
  
## <a name="restoring-the-systemhealth-session"></a>Ripristino della sessione system_health  
 Se si elimina la sessione system_health, è possibile ripristinarla eseguendo il file **u_tables.sql** nell'editor di query. Questo file si trova nella cartella seguente, dove C: rappresenta l'unità in cui sono stati installati i file di programma di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
 C:\Programmi\Microsoft SQL Server\MSSQL13.\<*idistanza*>\MSSQL\Install  
  
 Tenere presente che dopo aver ripristinato la sessione, è necessario avviarla tramite l'istruzione ALTER EVENT SESSION o tramite il nodo **Eventi estesi** in Esplora oggetti. In caso contrario, la sessione verrà avviata al successivo riavvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti degli eventi estesi](../../relational-databases/extended-events/extended-events-tools.md)  
  
  
