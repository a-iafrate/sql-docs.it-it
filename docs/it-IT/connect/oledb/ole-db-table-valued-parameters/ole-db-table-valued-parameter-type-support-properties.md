---
title: Supporto dei tipi OLE DB parametro con valori di tabella (proprietà) | Documenti Microsoft
description: Supporto tipo di parametro OLE DB Table-Valued (proprietà)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (properties)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: dbe4ff9ac8ccd23a4825ab0487d5fc5084ea64ae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-table-valued-parameter-type-support-properties"></a>Supporto dei tipi di parametri con valori di tabella OLE DB (proprietà)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In questo argomento sono incluse informazioni sulle proprietà e i set di proprietà OLE DB associati a oggetti set di righe di parametri con valori di tabella.  
  
## <a name="properties"></a>Proprietà  
 Di seguito è riportato l'elenco delle proprietà esposte tramite il metodo IRowsetInfo::GetPropeties per gli oggetti set di righe di parametri con valori di tabella. Si noti che tutte le proprietà dei set di righe di parametri con valori di tabella sono di sola lettura. Pertanto, il tentativo di impostare le proprietà tramite IOpenRowset:: OPENROWSET o ITableDefinitionWithConstraints::CreateTableWithConstraints metodi in base ai valori non predefiniti si verificherà un errore e non verrà creato alcun oggetto.  
  
 Le proprietà non implementate nell'oggetto set di righe di parametri con valori di tabella non sono incluse nell'elenco. Per un elenco completo delle proprietà, vedere la documentazione di OLE DB in Windows Data Access Components.  
  
|ID proprietà|Value|  
|-----------------|-----------|  
|DBPROP_ABORTPRESERVE|VARIANT_TRUE|  
|DBPROP_ACCESSORDER|DBPROPVAL_AO_RANDOM|  
|DBPROP_BLOCKINGSTORAGEOBJECTS|VARIANT_TRUE|  
|DBPROP_BOOKMARKS<br /><br /> DBPROP_LITERALBOOKMARKS|L/S: Sola lettura<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: i segnalibri non sono consentiti negli oggetti set di righe di parametri con valori di tabella.|  
|DBPROP_BOOKMARKSKIPPED|VARIANT_FALSE|  
|DBPROP_BOOKMARKTYPE|DBPROPVAL_BMK_NUMERIC|  
|DBPROP_CANHOLDROWS|VARIANT_FALSE|  
|DBPROP_CHANGEINSERTEDROWS|VARIANT_TRUE|  
|DBPROP_COLUMNRESTRICT|VARIANT_FALSE|  
|DBPROP_COMMANDTIMEOUT|0|  
|DBPROP_COMMITPRESERVE|VARIANT_TRUE|  
|DBPROP_DEFERRED|VARIANT_FALSE|  
|DBPROP_DELAYSTORAGEOBJECTS|VARIANT_FALSE|  
|DBPROP_IAccessor<br /><br /> DBPROP_IColumnsInfo<br /><br /> DBPROP_IConvertType<br /><br /> DBPROP_IRowset<br /><br /> DBPROP_IRowsetInfo,<br /><br /> DBPROP_IColumnsRowset|VARIANT_TRUE|  
|DBPROP_IConnectionPointContainer<br /><br /> DBPROP_IMultipleResults<br /><br /> DBPROP_IRowsetUpdate<br /><br /> DBPROP_IRowsetIdentity<br /><br /> DBPROP_IRowsetLocate<br /><br /> DBPROP_IRowsetScroll<br /><br /> DBPROP_IRowsetResynch|VARIANT_FALSE|  
|DBPROP_IRowsetChange|VARIANT_TRUE<br /><br /> Nota: L'oggetto set di righe di parametri con valori di tabella supporta le interfacce IRowsetChange.<br /><br /> Un set di righe creato tramite DBPROP_IRowsetChange uguale a VARIANT_TRUE indica comportamenti basati sulla modalità di aggiornamento immediato.<br /><br /> Tuttavia, se le colonne BLOB vengono associate come oggetti ISequentialStream, il consumer deve mantenerli per la durata dell'oggetto set di righe di parametri con valori di tabella.|  
|DBPROP_ISupportErrorInfo|VARIANT_TRUE|  
|DBPROP_ISequentialStream|VARIANT_TRUE|  
|DBPROP_IMMOBILEROWS|VARIANT_TRUE|  
|DBPROP_LITERALIDENTITY|VARIANT_TRUE|  
|DBPROP_LOCKMODE|DBPROPVAL_LM_NONE|  
|DBPROP_MAXOPENROWS|0|  
|DBPROP_MAXPENDINGROWS|0|  
|DBPROP_MAXROWS|0|  
|DBPROP_NOTIFICATIONPHASES|0|  
|DBPROP_NOTIFYCOLUMNSET DBPROP_NOTIFYROWDELETE DBPROP_NOTIFYROWFIRSTCHANGE DBPROP_NOTIFYROWINSERT DBPROP_NOTIFYROWRESYNCH DBPROP_NOTIFYROWSETRELEASE DBPROP_NOTIFYROWSETFETCH-POSITIONCHANGE DBPROP_NOTIFYROWUNDOCHANGE DBPROP_NOTIFYROWUNDODELETE DBPROP_NOTIFYROWUNDOINSERT DBPROP_NOTIFYROWUPDATE|0|  
|DBPROP_OTHERINSERT DBPROP_OTHERUPDATEDELETE|VARIANT_FALSE|  
|DBPROP_OWNINSERT<br /><br /> DBPROP_OWNUPDATEDELETE|VARIANT_TRUE|  
|DBPROP_QUICKRESTART|VARIANT_TRUE|  
|DBPROP_REENTRANTEVENTS|VARIANT_FALSE|  
|DBPROP_REMOVEDELETED|VARIANT_TRUE|  
|DBPROP_RETURNPENDINGINSERTS|VARIANT_TRUE|  
|DBPROP_ROWRESTRICT|VARIANT_FALSE|  
|DBPROP_ROWTHREADMODEL|DBPROPVAL_RT_FREETHREAD|  
|DBPROP_SERVERCURSOR|VARIANT_FALSE|  
|DBPROP_SERVERDATAONINSERT|VARIANT_FALSE|  
|DBPROP_STRONGIDENTITY|VARIANT_TRUE|  
|DBPROP_TRANSACTEDOBJECT|VARIANT_FALSE|  
|DBPROP_UNIQUEROWS|VARIANT_FALSE|  
|DBPROP_UPDATABILITY|DBPROPVAL_UP_CHANGE &#124; DBPROPVAL_UP_DELETE &#124; DBPROPVAL_UP_INSERT|  
  
## <a name="property-sets"></a>Set di proprietà  
 I set di proprietà seguenti supportano i parametri con valori di tabella.  
  
### <a name="dbpropsetsqlservercolumn"></a>DBPROPSET_SQLSERVERCOLUMN  
 Questa proprietà viene utilizzata dal consumer nel processo di creazione di un oggetto set di righe di parametri con valori di tabella utilizzando ITableDefinitionWithConstraints::CreateTableWithConstraints per ogni colonna della struttura DBCOLUMNDESC, se necessario.  
  
|ID proprietà|Valore proprietà|  
|-----------------|--------------------|  
|SSPROP_COL_COMPUTED|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Tipo: VT_BOOL<br /><br /> Descrizione: se impostata su VARIANT_TRUE, indica che la colonna è una colonna calcolata. VARIANT_FALSE indica che non si tratta di una colonna calcolata.|  
  
### <a name="dbpropsetsqlserverparameter"></a>DBPROPSET_SQLSERVERPARAMETER  
 Queste proprietà vengono lette dal consumer durante l'individuazione di informazioni sul tipo di parametro con valori di tabella nelle chiamate a ISSCommandWithParamters::GetParameterProperties e impostate dall'utente durante l'impostazione di proprietà specifiche sul parametro con valori di tabella tramite isscommandwithparameters:: Setparameterproperties.  
  
 Tali proprietà vengono descritte in modo dettagliato nella tabella seguente.  
  
|ID proprietà|Valore proprietà|  
|-----------------|--------------------|  
|SSPROP_PARAM_TYPE_TYPENAME|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VT_EMPTY<br /><br /> Tipo: VT_BSTR<br /><br /> Descrizione: i consumer utilizzano questa proprietà per ottenere o impostare il nome del tipo di parametro con valori di tabella.<br /><br /> Questa proprietà può essere utilizzata anche con i tipi CLR definiti dall'utente.<br /><br /> Questa proprietà può essere specificata facoltativamente per fornire un nome del tipo di tabella per un parametro con valori di tabella (in caso di comando della sintassi di ODBC). Questa proprietà è obbligatoria per le query SQL ad hoc con parametri.|  
|SSPROP_PARAM_TYPE_SCHEMANAME|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VT_EMPTY<br /><br /> Tipo: VT_BSTR<br /><br /> Descrizione: i consumer utilizzano questa proprietà per ottenere o impostare il nome dello schema del tipo di parametro con valori di tabella.<br /><br /> Questa proprietà può essere utilizzata anche con i tipi CLR definiti dall'utente.|  
|SSPROP_PARAM_TYPE_CATALOGNAME|L/S: Sola lettura<br /><br /> Impostazione predefinita: VT_EMPTY<br /><br /> Tipo: VT_BSTR<br /><br /> Descrizione: i consumer utilizzano questa proprietà per ottenere il nome del catalogo del tipo di parametro con valori di tabella.<br /><br /> Questa proprietà può essere utilizzata anche con i tipi CLR definiti dall'utente. Non è corretto impostare questa proprietà, in quanto i tipi definiti dall'utente devono essere inclusi nello stesso database in cui si trovano i parametri con valori di tabella che li utilizzano.|  
|SSPROP_PARAM_TABLE_DEFAULT_COLUMNS|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VT_EMPTY<br /><br /> Type: VT_UI2 &#124; VT_ARRAY<br /><br /> Descrizione: i consumer utilizzano questa proprietà per specificare quale set di colonne nel set di righe deve essere considerato quello predefinito. Per tali colonne non verrà inviato alcun valore. Durante il recupero di dati dall'oggetto set di righe del consumer, il provider non richiede un'associazione per tali colonne.<br /><br /> Ogni elemento della matrice deve essere un numero ordinale di una colonna nell'oggetto set di righe. Numeri ordinali non validi producono errori in fase di esecuzione del comando.|  
|SSPROP_PARAM_TABLE_COLUMN_ORDER|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VT_EMPTY<br /><br /> Type: VT_UI2 &#124; VT_ARRAY<br /><br /> Descrizione: questa proprietà viene utilizzata dal consumer per fornire un hint al server per indicare il tipo di ordinamento dei dati della colonna. Il provider non esegue alcuna convalida e presuppone che il consumer sia conforme alla specifica fornita. Il server utilizza questa proprietà per eseguire ottimizzazioni.<br /><br /> Le informazioni sull'ordine delle colonne per ogni colonna vengono rappresentate da una coppia di elementi nella matrice. Il primo elemento nella coppia è il numero della colonna. Il secondo elemento nella coppia sarà 1 per l'ordine crescente o 2 per l'ordine decrescente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto tipo di parametro con valori di tabella OLE DB](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [Utilizzare i valori di tabella parametri & #40; OLE DB & #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
