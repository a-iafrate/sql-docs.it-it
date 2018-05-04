---
title: Esecuzione di comandi contenenti parametri con valori di tabella | Documenti Microsoft
description: Esecuzione di comandi contenenti parametri con valori di tabella
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
- table-valued parameters, executing commands containing
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 0ddfd2e429ba9318f99561651b5c6ab1042eaa67
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="executing-commands-containing-table-valued-parameters"></a>Esecuzione di comandi contenenti parametri con valori di tabella
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Esegue un comando con parametri con valori di tabella avviene in due fasi:  
  
1.  Specifica dei tipi del parametro.  
  
2.  Associazione dei dati del parametro.  
  
## <a name="table-valued-parameter-specification"></a>Specifica del parametro con valori di tabella  
 Il tipo del parametro con valori di tabella può essere specificato dal consumer. Le informazioni relative al tipo includono il nome del tipo Contiene inoltre il nome dello schema, se il tipo di tabella definito dall'utente per il parametro con valori di tabella non è nello schema predefinito corrente per la connessione. A seconda del supporto di server, il consumer può specificare anche informazioni facoltative sui metadati, ad esempio l'ordine delle colonne e può indicare che tutte le righe di determinate colonne includano i valori predefiniti.  
  
 Per specificare un parametro con valori di tabella, il consumer chiama ISSCommandWithParamter::SetParameterInfo e facoltativamente chiama isscommandwithparameters:: Setparameterproperties. Per un parametro con valori di tabella, la *pwszDataSourceType* campo nella struttura DBPARAMBINDINFO ha un valore pari a DBTYPE_TABLE. Il *ulParamSize* campo è impostato su ~ 0 per indicare che la lunghezza è sconosciuta. Proprietà specifiche per i parametri con valori di tabella, ad esempio nome dello schema, nome del tipo, ordine delle colonne e le colonne predefinite, può essere impostata tramite isscommandwithparameters:: Setparameterproperties.  
  
## <a name="table-valued-parameter-binding"></a>Associazione del parametro con valori di tabella  
 Un parametro con valori di tabella può essere qualsiasi oggetto set di righe. Il provider legge da questo oggetto mentre invia parametri con valori di tabella al server durante l'esecuzione.  
  
 Per associare il parametro con valori di tabella, il consumer chiama IAccessor:: CreateAccessor. Il *wType* campo della struttura DBBINDING per il parametro con valori di tabella è impostato su DBTYPE_TABLE. Il *pObject* membro della struttura DBBINDING è non NULL e *pObject*del *iid* membro è impostato su IID_IRowset o qualsiasi altro oggetto set di righe di parametri con valori di tabella interfacce. I campi rimanenti nella struttura DBBINDING devono essere impostati esattamente come che si impostano per i BLOB di flusso.  
  
 Alle associazioni relative al parametro con valori di tabella e all'oggetto set di righe associato a un parametro con valori di tabella vengono applicate le restrizioni seguenti:  
  
-   Gli unici valori di stato consentiti per i dati di colonna dei set di righe di parametri con valori di tabella sono DBSTATUS_S_ISNULL e DBSTATUS_S_OK. DBSTATUS_S_DEFAULT genera un errore e il valore di stato associato viene impostato su DBSTATUS_E_BADSTATUS.  
  
-   Un parametro con valori di tabella può essere contrassegnato dallo stato DBSTATUS_S_DEFAULT. Gli unici valori validi sono DBSTATUS_S_DEFAULT e DBSTATUS_S_OK. Quando lo stato è impostato su DBSTATUS_S_DEFAULT, il valore del parametro con valori di tabella corrisponde a una tabella vuota.  
  
-   Le colonne di sola lettura nei parametri con valori di tabella (colonne Identity o calcolate) devono essere contrassegnate come predefinite tramite la proprietà SSPROP_PARAM_TABLE_DEFAULT_COLUMNS. Anche le colonne che presentano un valore predefinito devono essere contrassegnate come predefinite tramite la proprietà SSPROP_PARAM_TABLE_DEFAULT_COLUMNS per far sì che il valore predefinito venga utilizzato per i valori dei dati della colonna per un determinato parametro con valori di tabella. Il provider ignorerà i valori dei dati associati per le colonne contrassegnate come predefinite.  
  
-   I dati saranno inviati al server per le colonne con DBPROP_COL_AUTOINCREMENT o SSPROP_COL_COMPUTED, a meno che non sia impostata anche la proprietà SSPROP_PARAM_TABLE_DEFAULT.  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued Parameters &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utilizzare i valori di tabella parametri & #40; OLE DB & #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  