---
title: sp_helpsubscription (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpsubscription_TSQL
- sp_helpsubscription
helpviewer_keywords: sp_helpsubscription
ms.assetid: ff96bcbf-e2b9-4da8-8515-d80d4ce86c16
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 201a7c412fbf01ca2600d3c9dc233eadfa33710b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpsubscription-transact-sql"></a>sp_helpsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce l'elenco delle informazioni sulla sottoscrizione associate a una pubblicazione, un articolo, un Sottoscrittore o un set di sottoscrizioni. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpsubscription [ [ @publication = ] 'publication' ]   
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @destination_db = ] 'destination_db' ]   
    [ , [ @found=] found OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =** ] **'***pubblicazione***'**  
 Nome della pubblicazione associata. *pubblicazione* è **sysname**, il valore predefinito è  **%** , che restituisce tutte le informazioni di sottoscrizione per questo server.  
  
 [  **@article=** ] **'***articolo***'**  
 Nome dell'articolo. *articolo* è **sysname**, il valore predefinito è  **%** , che restituisce tutte le informazioni di sottoscrizione per le pubblicazioni e selezionati i sottoscrittori. Se **tutti**, viene restituita una sola voce per la sottoscrizione completa in una pubblicazione.  
  
 [  **@subscriber=** ] **'***sottoscrittore***'**  
 Nome del Sottoscrittore di cui si desidera ottenere le informazioni sulla sottoscrizione. *Sottoscrittore* è **sysname**, il valore predefinito è  **%** , che restituisce tutte le informazioni di sottoscrizione per le pubblicazioni e selezionati gli articoli.  
  
 [  **@destination_db=** ] **'***destination_db***'**  
 Nome del database di destinazione. *destination_db* è **sysname**, il valore predefinito è  **%** .  
  
 [  **@found=** ] **'***trovato***'**OUTPUT  
 Flag che indica le righe che restituiscono valori. *trovato*è **int** e un parametro di OUTPUT con valore predefinito è 23456.  
  
 **1** indica la pubblicazione è stata trovata.  
  
 **0** indica la pubblicazione è stata trovata.  
  
 [  **@publisher** =] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* è **sysname**e il valore predefinito il nome del server corrente.  
  
> [!NOTE]  
>  *server di pubblicazione* non deve essere specificato, tranne nel caso un server di pubblicazione Oracle.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**subscriber**|**sysname**|Nome del Sottoscrittore.|  
|**pubblicazione**|**sysname**|Nome della pubblicazione.|  
|**articolo**|**sysname**|Nome dell'articolo.|  
|**database di destinazione**|**sysname**|Nome del database di destinazione per i dati replicati.|  
|**stato della sottoscrizione**|**tinyint**|Stato della sottoscrizione:<br /><br /> **0** = inattivo<br /><br /> **1** = sottoscritto<br /><br /> **2** = attivo|  
|**tipo di sincronizzazione**|**tinyint**|Tipo di sincronizzazione per la sottoscrizione:<br /><br /> **1** = automatica<br /><br /> **2** = nessuno|  
|**tipo di sottoscrizione**|**int**|Tipo di sottoscrizione:<br /><br /> **0** = push<br /><br /> **1** = pull<br /><br /> **2** = anonimo|  
|**sottoscrizione completa**|**bit**|Indica se la sottoscrizione è associata a tutti gli articoli della pubblicazione:<br /><br /> **0** = No<br /><br /> **1** = Sì|  
|**nome della sottoscrizione**|**nvarchar(255)**|Nome della sottoscrizione.|  
|**modalità di aggiornamento**|**int**|**0** = sola lettura<br /><br /> **1** = sottoscrizione ad aggiornamento immediato|  
|**id di processo di distribuzione**|**Binary (16)**|ID di processo dell'agente di distribuzione.|  
|**loopback_detection**|**bit**|Il rilevamento di loopback determina se l'agente di distribuzione deve inviare nuovamente al Sottoscrittore le transazioni provenienti dal Sottoscrittore:<br /><br /> **0** = invia nuovamente.<br /><br /> **1** = non ha restituito.<br /><br /> Utilizzato con la replica transazionale bidirezionale. Per altre informazioni, vedere [Bidirectional Transactional Replication](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md).|  
|**offload_enabled**|**bit**|Specifica se per un agente di replica è impostata l'esecuzione con ripartizione del carico di lavoro nel Sottoscrittore.<br /><br /> Se **0**, agente viene eseguito nel server di pubblicazione.<br /><br /> Se **1**, l'agente viene eseguito nel Sottoscrittore.|  
|**offload_server**|**sysname**|Nome del server abilitato per l'attivazione remota degli agenti. Se NULL, il valore di offload_server corrente elencati [MSdistribution_agents](../../relational-databases/system-tables/msdistribution-agents-transact-sql.md) viene utilizzata la tabella.|  
|**dts_package_name**|**sysname**|Specifica il nome del pacchetto Data Transformation Services (DTS).|  
|**dts_package_location**|**int**|Posizione del pacchetto DTS, se assegnato alla sottoscrizione. Se è presente un pacchetto, un valore di **0** specifica la posizione del pacchetto nel **distributore**. Il valore **1** specifica il **sottoscrittore**.|  
|**subscriber_security_mode**|**smallint**|Modalità di sicurezza nel Sottoscrittore, in cui **1** indica l'autenticazione di Windows e **0** significa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione.|  
|**subscriber_login**|**sysname**|Nome dell'account di accesso nel Sottoscrittore.|  
|**subscriber_password**||La password effettiva per il Sottoscrittore non viene mai restituita. Il risultato viene mascherato da una "**\*\*\*\*\*\***" stringa.|  
|**job_login**|**sysname**|Nome dell'account di Windows utilizzato per l'esecuzione dell'agente di distribuzione.|  
|**job_password**||La password effettiva per il processo non viene mai restituita. Il risultato viene mascherato da una "**\*\*\*\*\*\***" stringa.|  
|**distrib_agent_name**|**nvarchar (100)**|Nome del processo dell'agente che sincronizza la sottoscrizione.|  
|**subscriber_type**|**tinyint**|Tipo di Sottoscrittore. I possibili tipi sono i seguenti:<br /><br /> **0** = sottoscrittore di SQL Server<br /><br /> **1** = server di origine dati ODBC<br /><br /> **2** = database Microsoft JET (deprecato)<br /><br /> **3** = provider OLE DB|  
|**subscriber_provider**|**sysname**|ProgID univoco con il quale viene registrato il provider OLE DB per l'origine dei dati non SQL Server.|  
|**subscriber_datasource**|**nvarchar(4000)**|Nome dell'origine dei dati riconosciuto dal provider OLE DB.|  
|**subscriber_providerstring**|**nvarchar(4000)**|Stringa di connessione specifica del provider OLE DB che identifica l'origine dei dati.|  
|**subscriber_location**|**nvarchar(4000)**|Percorso del database riconosciuto dal provider OLE DB.|  
|**subscriber_catalog**|**sysname**|Catalogo da utilizzare per stabilire una connessione al provider OLE DB|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpsubscription** viene utilizzata nella replica snapshot e transazionale.  
  
## <a name="permissions"></a>Permissions  
 Le autorizzazioni di esecuzione vengono assegnate per impostazione predefinita al ruolo **public** . All'utente vengono restituite solo le informazioni relative alle sottoscrizioni create dall'utente stesso. Informazioni su tutte le sottoscrizioni vengono restituite ai membri del **sysadmin** al server di pubblicazione o i membri del ruolo predefinito del server di **db_owner** ruolo predefinito del database nel database di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [stored procedure sp_addsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  