---
title: sp_changemergefilter (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changemergefilter_TSQL
- sp_changemergefilter
helpviewer_keywords:
- sp_changemergefilter
ms.assetid: e08fdfdd-d242-4e85-817b-9f7a224fe567
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 332cb7bd6d4afa477064bd014e36dc2e5b6e8aa7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spchangemergefilter-transact-sql"></a>sp_changemergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di modificare alcune proprietà del filtro di merge. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_changemergefilter [ @publication= ] 'publication'  
        , [ @article= ] 'article'  
        , [ @filtername= ] 'filtername'  
        , [ @property= ] 'property'  
        , [ @value= ] 'value'  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@article=** ] **'***articolo***'**  
 Nome dell'articolo. *articolo* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@filtername=** ] **'***filtername***'**  
 Nome corrente del filtro. *FilterName* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@property=** ] **'***proprietà***'**  
 Nome della proprietà da modificare. *proprietà* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@value=**] **'***valore***'**  
 Nuovo valore della proprietà specificata. *valore*viene **nvarchar(1000)**, non prevede alcun valore predefinito.  
  
 Nella tabella seguente vengono descritte le proprietà degli articoli e i valori corrispondenti.  
  
|Proprietà|Value|Description|  
|--------------|-----------|-----------------|  
|**filter_type**|**1**|Filtro join.<br /><br /> Questa opzione è necessaria per supportare i Sottoscrittori [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
||**2**|Relazione tra record logici.|  
||**3**|Il filtro join è anche una relazione tra record logici.|  
|**FilterName**||Nome del filtro.|  
|**join_articlename**||Nome dell'articolo di join.|  
|**join_filterclause**||Clausola di filtro.|  
|**join_unique_key**|**true**|Il join è basato su una chiave univoca.|  
||**false**|Il join non è basato su una chiave univoca.|  
  
 [ **@force_invalidate_snapshot =** ] *force_invalidate_snapshot*  
 Segnala che l'azione eseguita da questa stored procedure potrebbe invalidare uno snapshot esistente. *force_invalidate_snapshot* è un **bit**, con un valore predefinito **0**.  
  
 **0** specifica che le modifiche apportate all'articolo di merge non invalidano lo snapshot non è valido. Se la stored procedure rileva che la modifica richiede un nuovo snapshot, viene generato un errore e non viene apportata alcuna modifica.  
  
 **1** significa che le modifiche apportate all'articolo di merge potrebbero invalidare lo snapshot non è valido e se sono disponibili sottoscrizioni che richiedono un nuovo snapshot, concede l'autorizzazione per lo snapshot esistente deve essere contrassegnato come obsoleto e di generarne uno nuovo.  
  
 [  **@force_reinit_subscription =** ] *force_reinit_subscription*  
 Segnala che l'azione eseguita dalla stored procedure potrebbe richiedere la reinizializzazione delle sottoscrizioni esistenti. *force_reinit_subscription* è un **bit** con valore predefinito è **0**.  
  
 **0** specifica che le modifiche apportate all'articolo di merge non causano la reinizializzazione della sottoscrizione. Se la stored procedure rileva che la modifica richiede la reinizializzazione delle sottoscrizioni esistenti, viene generato un errore e non viene apportata alcuna modifica.  
  
 **1** significa che le modifiche apportate all'articolo di merge causa reinizializzazione delle sottoscrizioni esistenti e concede l'autorizzazione per la reinizializzazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_changemergefilter** viene utilizzata nella replica di tipo merge.  
  
 Per modificare il filtro in un articolo di merge, è necessario ricreare lo snapshot, se disponibile. Questa operazione viene eseguita impostando il **@force_invalidate_snapshot** a **1**. È inoltre necessario reinizializzare le eventuali sottoscrizioni esistenti dell'articolo. Questa operazione viene eseguita impostando il **@force_reinit_subscription** a **1**.  
  
 Per utilizzare record logici, è necessario che la pubblicazione e gli articoli soddisfino alcuni requisiti. Per altre informazioni, vedere [Raggruppare modifiche alle righe correlate con record logici](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_changemergefilter**.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica delle proprietà di pubblicazioni e articoli](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
