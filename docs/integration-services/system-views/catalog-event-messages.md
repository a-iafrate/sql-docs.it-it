---
title: catalog.event_messages | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: a31a654f-31e9-4da1-aabf-182b07848e36
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3480f3abcfb08f20fb49b07e4d7d88571c138a98
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="catalogeventmessages"></a>catalog.event_messages
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Consente di visualizzare informazioni sui messaggi registrati durante le operazioni.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|Event_message_ID|BIGINT|ID univoco del messaggio dell'evento.|  
|Operation_id|BIGINT|Tipo di operazione.<br /><br /> Per un elenco dei tipi di operazioni, vedere [catalog.operations &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md).|  
|Message_time|datetimeoffset(7)|Ora di creazione del messaggio.|  
|Message_type|SMALLINT|Tipo di messaggio visualizzato. Per altre informazioni sui tipi di messaggi, vedere [catalog.operation_messages &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md).|  
|Message_source_type|SMALLINT|Origine del messaggio.|  
|message|nvarchar(max)|Testo del messaggio.|  
|Extended_info_id|BIGINT|ID di informazioni aggiuntive correlate al messaggio dell'operazione, individuato nella vista [catalog.extended_operation_info &#40;Database SSISDB&#41;](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md).|  
|Package_name|nvarchar(260)|Nome del file del pacchetto.|  
|Event_name|nvarchar(1024)|Evento di run-time associato al messaggio.|  
|Message_source_name|nvarchar(4000)|Componente del pacchetto che rappresenta l'origine del messaggio.|  
|Message_source_id|nvarchar(38)|ID univoco dell'origine del messaggio.|  
|Subcomponent_name|nvarchar(4000)|Componente flusso di dati che corrisponde all'origine del messaggio.<br /><br /> Se vengono restituiti messaggi dal motore [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], nella colonna viene visualizzato SSIS.Pipeline.|  
|Package_path|nvarchar(max)|Percorso univoco del componente all'interno del pacchetto.|  
|Execution_path|nvarchar(max)|Percorso completo dal pacchetto padre al punto in cui viene eseguito il componente.<br /><br /> In questo percorso vengono anche acquisite le iterazioni di un componente.|  
|threadID|INT|ID per il thread in esecuzione al momento della registrazione del messaggio.|  
|Message_code|INT|Codice associato al messaggio.|  
  
## <a name="remarks"></a>Remarks  
 In questa vista vengono visualizzati i tipi di origine del messaggio seguenti.  
  
|**message_source_type**|Description|  
|-------------------------------|-----------------|  
|10|API della voce, ad esempio stored procedure CLR e T-SQL|  
|20|Processo esterno utilizzato per eseguire il pacchetto (ISServerExec.exe)|  
|30|Oggetti a livello di pacchetto|  
|40|Attività Flusso di controllo|  
|50|Contenitori del flusso di controllo|  
|60|Attività Flusso di dati|  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per l'operazione  
  
-   Appartenenza al ruolo del database **ssis_admin**.  
  
-   Appartenenza al ruolo del server **sysadmin**.  
  
## <a name="see-also"></a>Vedere anche  
 [catalog.event_message_context](../../integration-services/system-views/catalog-event-message-context.md)  
  
  
