---
title: MSsubscription_agents (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSsubscription_agents
- MSsubscription_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_agents system table
ms.assetid: 86ad5891-0bef-4963-9381-7d5b45245a0c
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: fda3a53eae90bd9c21c25124cef2254451cb1ab1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mssubscriptionagents-transact-sql"></a>MSsubscription_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSsubscription_agents** tabella viene utilizzata dall'agente di distribuzione e trigger delle sottoscrizione aggiornabili per tenere traccia delle proprietà della sottoscrizione. Questa tabella è archiviata nel database di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID della riga|  
|**publisher**|**sysname**|Nome del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database di pubblicazione.|  
|**Pubblicazione**|**sysname**|Nome della pubblicazione.|  
|**subscription_type**|**int**|Tipo di sottoscrizione:<br /><br /> 0 = push<br /><br /> 1 = Pull.<br /><br /> 2 = Pull anonima.|  
|**queue_id**|**sysname**|L'ID del [!INCLUDE[msCoName](../../includes/msconame-md.md)] coda nel server di pubblicazione del messaggio. *il valore queue_id* è impostata su **SQL** per basato su SQL ad aggiornamento in coda.|  
|**update_mode**|**tinyint**|Tipo di aggiornamento:<br /><br /> **0** = sola lettura.<br /><br /> **1** = aggiornamento immediato.<br /><br /> **2** = aggiornamento in coda tramite MSMQ.<br /><br /> **3** = controllo immediato aggiornare con aggiornamento in coda come failover tramite MSMQ.<br /><br /> **4** = aggiornamento in coda tramite la coda SQL Server.<br /><br /> **5** = aggiornamento immediato con failover dell'aggiornamento in coda, tramite la coda SQL Server.|  
|**failover_mode**|**bit**|Se è stato specificato un aggiornamento di tipo failover, indica il tipo di failover selezionato:<br /><br /> **0** = controllo immediato aggiornamento è in uso. Il failover non è attivato.<br /><br /> **1** = in coda aggiornamento è in uso. Il failover è attivato. La coda viene usata per il failover viene specificata nel *update_mode* valore.|  
|**spid**|**int**|ID del processo di sistema per la connessione utilizzata dall'agente di distribuzione appena eseguito o in esecuzione.|  
|**login_time**|**datetime**|Data e ora della connessione dell'agente di distribuzione appena eseguito o in esecuzione.|  
|**allow_subscription_copy**|**bit**|Specifica se consentire o meno la copia del database di sottoscrizione.|  
|**attach_state**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**attach_version**|**binary(16)**|Identificatore univoco che rappresenta la versione di una sottoscrizione allegata.|  
|**last_sync_status**|**int**|Ultimo stato di esecuzione dell'agente di distribuzione appena eseguito o in esecuzione. I possibili valori sono i seguenti.<br /><br /> **1** = avviato.<br /><br /> **2** = ha avuto esito positivo.<br /><br /> **3** = in corso.<br /><br /> **4** = inattivo.<br /><br /> **5** = nuovo tentativo.<br /><br /> **6** = esito negativo.|  
|**last_sync_summary**|**sysname**|Ultimo messaggio dell'agente di distribuzione appena eseguito o in esecuzione. I possibili valori sono i seguenti.<br /><br /> **avviato.**<br /><br /> **Ha avuto esito positivo.**<br /><br /> **In corso.**<br /><br /> **Periodi di inattività.**<br /><br /> **Riprovare.**<br /><br /> **Esito negativo.**|  
|**last_sync_time**|**datetime**|La data e l'ora di *last_sync_summary* e *last_sync_status* colonne sono state aggiornate. Gli agenti di distribuzione pull o anonimi eseguiti come processi del servizio SQL Server Agent non aggiornano queste colonne. Vengono invece registrate informazioni cronologiche nella tabella di cronologia processo.|  
|**queue_server**|**sysname**|Solo per uso interno.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica di &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)  
  
  
