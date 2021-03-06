---
title: I parametri con valori di tabella (OLE DB) | Documenti Microsoft
description: Parametri con valori di tabella (OLE DB)
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
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 91478e575fdde15b6bbd1f82185f7c32d5e38daa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="table-valued-parameters-ole-db"></a>Parametri con valori di tabella (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In questa sezione viene descritto il supporto per i parametri con valori di tabella nel Driver OLE DB per SQL Server. Per ulteriori informazioni, vedere [Table-Valued Parameters &#40;il Driver OLE DB per SQL Server&#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md). Per un esempio, vedere [utilizzare parametri &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Osservazioni  
 Attualmente, è possibile inviare dati a riga multipla al server come parametri per una procedura con set di parametri (parametro DBPARAMS in **ICommand:: Execute**). Con i set di parametri, ogni elemento del set deve essere inviato al server in una richiesta di chiamata di procedura remota (RPC) separata. I parametri con valori di tabella forniscono funzionalità simili, ma offrono una maggiore integrazione con il server. Riduce il numero di richieste RPC e consente di eseguire operazioni basate su set nel server.  
  
 I parametri con valori di tabella sono supportati nel Driver OLE DB per SQL Server come OLE DB **set di righe** oggetti. Qualsiasi **set di righe** oggetto può essere fornito dal consumer (vale a dire, l'applicazione client usando il Driver OLE DB per SQL Server) come segnaposto per i parametri con valori di tabella. I parametri con valori di tabella vengono considerati come gli altri tipi di parametro di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il Driver OLE DB per SQL Server fornisce la creazione, l'individuazione, specifica, associazione e le interfacce dello schema.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Creazione di un set di righe di parametri con valori di tabella](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)  
  
-   [Individuazione dei tipi di parametro con valori di tabella](../../oledb/ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)  
  
-   [Esecuzione di comandi contenenti parametri con valori di tabella](../../oledb/ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)  
  
-   [Inserimento di dati in parametri con valori di tabella](../../oledb/ole-db-table-valued-parameters/inserting-data-into-table-valued-parameters.md)  
  
-   [Set di righe dello schema modificati per i parametri con valori di tabella OLE DB](../../oledb/ole-db-table-valued-parameters/schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [Supporto dei tipi di parametro con valori di tabella OLE DB](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)  
  
-   [Supporto tipo di parametro con valori di tabella OLE DB &#40;metodi&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [Supporto tipo di parametro con valori di tabella OLE DB &#40;proprietà&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per la programmazione di SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [Utilizzare i valori di tabella parametri & #40; OLE DB & #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
