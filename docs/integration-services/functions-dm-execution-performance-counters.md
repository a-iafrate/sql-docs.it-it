---
title: dm_execution_performance_counters (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 1b38e8e3-c560-4b6e-b60e-bfd7cfcd4fdf
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d15f0865ccecd60dc6af558cafcd67e8646043a
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="functions---dmexecutionperformancecounters"></a>Funzioni - dm_execution_performance_counters
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Restituisce le statistiche sulle prestazioni per un'esecuzione in corso nel server [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
dm_execution_performance_counters [ @execution_id = ] execution_id  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @execution_id = ] *execution_id*  
 Identificatore univoco dell'esecuzione che contiene uno o più pacchetti. I pacchetti eseguiti con l'attività Esegui pacchetto vengono eseguiti nella stessa esecuzione del pacchetto padre.  
  
 Se non è specificato alcun ID esecuzione, vengono restituite le statistiche per più esecuzioni. Se si è un membro del ruolo del database **ssis_admin** , vengono restituite le statistiche sulle prestazioni per tutte le esecuzioni in corso.  Se non si è un membro del ruolo del database **ssis_admin** , vengono restituite le statistiche sulle prestazioni per le esecuzioni in corso per cui si dispone delle autorizzazioni di lettura. *execution_id* è di tipo **bigint**.  
  
## <a name="remarks"></a>Remarks  
 Nella tabella seguente sono elencati i valori dei nomi dei contatori restituiti dalla funzione dm_execution_performance_counter.  
  
|Nome contatore|Description|  
|------------------|-----------------|  
|Byte BLOB letti|Numero di byte dei dati BLOB (Binary Large Object) letti dal motore del flusso di dati in tutte le origini.|  
|Byte BLOB scritti|Numero di byte dei dati BLOB scritti dal motore del flusso di dati in tutte le destinazioni.|  
|File BLOB in uso|Numero di file BLOB attualmente utilizzati dal motore del flusso di dati per lo spooling.|  
|Memoria buffer|Quantità di memoria utilizzata dai buffer di Integration Services, inclusa la memoria fisica e quella virtuale.|  
|Buffer in uso|Numero di oggetti buffer, di qualsiasi tipo, attualmente utilizzati dal motore e da tutti i componenti del flusso di dati.|  
|Buffer con spooling|Numero di buffer scritti sul disco.|  
|Memoria lineare buffer|Quantità di memoria, in byte, utilizzata da tutti i buffer memoria lineare. I buffer memoria lineare sono blocchi di memoria utilizzati da un componente per l'archiviazione di dati.|  
|Buffer memoria lineare in uso|Numero di buffer memoria lineare utilizzati dal motore del flusso di dati. Tutti i buffer memoria lineare sono buffer privati.|  
|Memoria buffer privati|Quantità di memoria utilizzata da tutti i buffer privati. Un buffer privato è un buffer utilizzato da una trasformazione per un'attività temporanea.<br /><br /> Un buffer non è privato se il motore del flusso di dati crea il buffer per il supporto del flusso di dati.|  
|Buffer privati in uso|Numero di buffer utilizzati dalle trasformazioni pere un'attività temporanea.|  
|Righe lette|Numero totale di righe pronte l'esecuzione.|  
|Righe scritte|Numero totale di righe scritte dall'esecuzione.|  
  
## <a name="return"></a>Return  
 La funzione dm_execution_performance_counters restituisce una tabella con le colonne seguenti per un'esecuzione in corso. Le informazioni restituite riguardano tutti i pacchetti contenuti nell'esecuzione. In assenza di esecuzioni in corso, viene restituita una tabella vuota.  
  
|Nome colonna|Tipo di colonna|Description|Remarks|  
|-----------------|-----------------|-----------------|-------------|  
|execution_id|**BigInt**<br /><br /> **NULL** non è un valore valido.|Identificatore univoco per l'esecuzione che contiene il pacchetto.||  
|counter_name|**nvarchar(128)**|Nome del contatore.|Vedere la sezione **Osservazioni** relativa ai valori.|  
|counter_value|**BigInt**|Valore restituito dal contatore.||  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente la funzione restituisce le statistiche di un'esecuzione in corso con ID 34.  
  
```sql
select * from [catalog].[dm_execution_performance_counters] (34)  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente la funzione restituisce le statistiche di tutte le esecuzioni in corso nel server [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], a seconda delle autorizzazioni.  
  
```sql
select * from [catalog].[dm_execution_performance_counters] (NULL)  
  
```  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa funzione richiede una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY per l'istanza di esecuzione  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte le condizioni che causano la mancata riuscita della funzione.  
  
-   L'utente non dispone delle autorizzazioni MODIFY per l'esecuzione specificata.  
  
-   L'ID esecuzione specificato non è valido.  
  
  
