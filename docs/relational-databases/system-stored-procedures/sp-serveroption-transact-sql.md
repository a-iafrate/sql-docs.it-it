---
title: sp_serveroption (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_serveroption_TSQL
- sp_serveroption
dev_langs:
- TSQL
helpviewer_keywords:
- 7343 (Database Engine error)
- sp_serveroption
ms.assetid: 47d04a2b-dbf0-4f15-bd9b-81a2efc48131
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 99f936f0a8d127dd33ebce8b86c0a958cafccf66
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="spserveroption-transact-sql"></a>sp_serveroption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta le opzioni per server remoti e server collegati.  
  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_serveroption [@server = ] 'server'   
      ,[@optname = ] 'option_name'       
      ,[@optvalue = ] 'option_value' ;  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@server =** ] **'***server***'**  
 Nome del server per il quale impostare l'opzione. *server* è di tipo **sysname**e non prevede alcun valore predefinito.  
  
 [  **@optname =** ] **'***option_name***'**  
 Opzione da impostare per il server specificato. *option_name* viene **varchar (** 35 **)**, non prevede alcun valore predefinito. *option_name* può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**regole di confronto compatibili**|Influisce sull'esecuzione delle query distribuite in server collegati. Se questa opzione è impostata su **true**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si presuppone che tutti i caratteri nel server collegato compatibili con il server locale, relativamente al set e regole di confronto di sequenza di caratteri (oppure di ordinamento). Ciò consente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di inviare al provider i confronti per colonne di tipo carattere. Se questa opzione non è impostata, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valuta sempre i confronti per le colonne di tipo carattere localmente.<br /><br /> Impostare questa opzione solo se nell'origine dei dati corrispondente al server collegato il set di caratteri e il tipo di ordinamento corrispondono a quelli del server locale.|  
|**Nome delle regole di confronto**|Specifica il nome delle regole di confronto utilizzate dall'origine dei dati remota se **utilizzare regole di confronto remote** è **true** e l'origine dati non è un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati. È necessario specificare il nome di uno dei set di regole di confronto supportate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Utilizzare questa opzione per accedere a un'origine dei dati OLE DB diversa da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]che utilizza regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Il server collegato deve supportare regole di confronto singole da utilizzare per tutte le colonne del server. Non impostare questa opzione quando il server collegato supporta più regole di confronto nella stessa origine dei dati oppure non è possibile stabilire se le regole di confronto del server collegato corrispondono a una delle regole di confronto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**Timeout connessione**|Secondi valuein di timeout per la connessione a un server collegato.<br /><br /> Se **0**, utilizzare il **sp_configure** predefinito.|  
|**Accesso ai dati**|Consente di attivare e disabilitare un server collegato per l'accesso a query distribuite. Può essere utilizzata solo per **sys** aggiunte tramite voci **sp_addlinkedserver**.|  
|**dist**|Server di distribuzione.|  
|**convalida differita dello schema**|Determina se lo schema delle tabelle remote viene controllato.<br /><br /> Se **true**, ignorare il controllo delle tabelle remote all'inizio della query dello schema.|  
|**pub**|Server di pubblicazione.|  
|**timeout query**|Timeout per le query eseguite nel server collegato.<br /><br /> Se **0**, utilizzare il **sp_configure** predefinito.|  
|**rpc**|Abilita l'esecuzione di chiamate RPC dal server specificato.|  
|**chiamate RPC in uscita**|Abilita l'esecuzione di chiamate RPC al server specificato.|  
|**sub**|Sottoscrittore.|  
|**system**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Utilizzare regole di confronto remote**|Determina se vengono utilizzate le regole di confronto di una colonna remota o di un server locale.<br /><br /> Se **true**, le regole di confronto delle colonne remote viene utilizzato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origini dati e regole di confronto specificate **nome regole di confronto** viene utilizzato per non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origini dati.<br /><br /> Se **false**, query distribuite vengono sempre utilizzate le regole di confronto predefinite del server locale, mentre **nome regole di confronto** e le regole di confronto delle colonne remote vengono ignorati. Il valore predefinito è **false**. (Il **false** valore è compatibile con la semantica delle regole di confronto utilizzata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.)|  
|**promozione delle transazioni remote proc**|Questa opzione consente di proteggere le azioni di una procedura da server a server tramite una transazione MS DTC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator). Quando questa opzione è impostata su TRUE (o ON) chiama una stored procedure remota viene avviata una transazione distribuita e integrazione della transazione in MS DTC. L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui viene chiamata la stored procedure remota corrisponde all'origine della transazione e ne controlla il completamento. Quando per la connessione viene successivamente eseguita un'istruzione COMMIT TRANSACTION o ROLLBACK TRANSACTION, l'istanza di controllo richiede che il completamento della transazione distribuita nei computer interessati venga gestito da MS DTC.<br /><br /> Dopo l'avvio di una transazione distribuita [!INCLUDE[tsql](../../includes/tsql-md.md)], è possibile chiamare stored procedure remote in altre istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definite come server collegati. Tutti i server collegati sono integrati nella transazione distribuita [!INCLUDE[tsql](../../includes/tsql-md.md)]. MS DTC garantisce inoltre che la transazione venga completata in ogni server collegato.<br /><br /> Se questa opzione è impostata su FALSE (o OFF), una transazione locale non sarà promossa a transazione distribuita durante una chiamata di procedura remota in un server collegato.<br /><br /> Se prima di effettuare una chiamata di una procedura da server a server la transazione è già una transazione distribuita, questa opzione non ha alcun effetto. La chiamata di procedura nel server collegato verrà eseguita nella stessa transazione distribuita.<br /><br /> Se prima di effettuare una chiamata di una procedura da server a server non vi sono transazioni attive nella connessione, questa opzione non ha alcun effetto. La procedura viene quindi eseguita nel server collegato senza transazioni attive.<br /><br /> Il valore predefinito per questa opzione è TRUE (o ON).|  
  
 [  **@optvalue =**] **'***option_value***'**  
 Specifica o meno il *option_name* deve essere abilitato (**TRUE** o **su**) o disabilitato (**FALSE** o **off**). *option_value* viene **varchar (** 10 **)**, non prevede alcun valore predefinito.  
  
 *option_value* può essere un numero intero non negativo per il **timeout connessione** e **timeout query** opzioni. Per il **nome regole di confronto** opzione *option_value* può essere un nome regole di confronto o NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Se il **regole di confronto compatibili** opzione è impostata su TRUE, **nome regole di confronto** viene impostata automaticamente su NULL. Se **nome regole di confronto** è impostata su un valore non null, **regole di confronto compatibili** viene impostata automaticamente su FALSE.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ALTER ANY LINKED SERVER per il server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene configurata la compatibilità delle regole di confronto tra un server collegato corrispondente a un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, e l'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Distributed query Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpserver & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
