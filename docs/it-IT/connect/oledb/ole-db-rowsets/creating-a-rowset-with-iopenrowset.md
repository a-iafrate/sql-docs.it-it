---
title: Creazione di un set di righe con IOpenRowset | Documenti Microsoft
description: Creazione di un set di righe con IOpenRowset interfaccia del Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 4e41561c8d60a076e282051b021dbb64306e2e8f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Creazione di un set di righe con IOpenRowset
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server supporta il **IOpenRowset:: OPENROWSET** (metodo) con le restrizioni seguenti:  
  
-   Una tabella di base o una vista deve essere specificato in un database (DBID) ID struttura che la *pTableID* punta al parametro.  
  
-   Il DBID *eKind* membro deve indicare DBKIND_NAME.  
  
-   Il DBID *uName* membro deve specificare il nome di una tabella di base esistente o una vista come una stringa di caratteri Unicode.  
  
-   Il *pIndexID* parametro di **OpenRowset** deve essere NULL.  
  
 Il set di risultati di **IOpenRowset:: OPENROWSET** contiene un singolo set di righe. Set di risultati che contengono un singolo set di righe possono essere supportati da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cursori. Il supporto del cursore consente allo sviluppatore di utilizzare i meccanismi di concorrenza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
