---
title: Set di righe dello schema modificati per i parametri con valori di tabella OLE DB | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 05ee24d3f373cb891f6387f5f128de0845227c5e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>Set di righe dello schema modificati per i parametri con valori di tabella OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Di seguito sono elencati i set di righe dello schema che sono stati modificati o aggiunti per il supporto dei parametri con valori di tabella.  
  
|Set di righe dello schema|Description|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|Alla fine del set di righe sono state aggiunte due nuove colonne denominate SS_TYPE_CATALOG_NAME e SS_TYPE_SCHEMANAME. Tali colonne potrebbero essere riutilizzate per i tipi futuri. Le colonne TYPE_NAME e LOCAL_TYPE_NAME conterranno il nome del tipo TABLE dei parametri con valori di tabella. La colonna DATA_TYPE avrà il valore DBTYPE_TABLE = 143 per i parametri con valori di tabella.|  
|DBSCHEMA_TABLE_TYPES|Questo set di righe è stato aggiunto per supportare i parametri con valori di tabella. È identico a DBSCHEMA_TABLES, con l'eccezione che restituisce metadati solo per i tipi di tabella, anziché per tabelle, viste o sinonimi. La colonna TABLE_TYPE avrà il valore TABLE TYPE.|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|Questo set di righe è stato aggiunto per supportare i parametri con valori di tabella. È identico a DBSCHEMA_PRIMARY_KEYS, con l'eccezione che restituisce chiavi primarie solo per i tipi di tabella, anziché per tabelle, viste o sinonimi.|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|Questo set di righe è stato aggiunto per supportare i parametri con valori di tabella. È identico a DBSCHEMA_COLUMNS, con l'eccezione che restituisce metadati di colonna solo per i tipi di tabella, anziché per tabelle, viste o sinonimi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued Parameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utilizzare i valori di tabella parametri & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
