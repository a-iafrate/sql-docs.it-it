---
title: Posizione del recupero successivo | Documenti Microsoft
description: Recupero righe - posizione del recupero successiva
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: b3e7bb16d9f2c04525a0646b9f4647fdd1e811e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="fetching-rows---next-fetch-position"></a>Recupero di righe - posizione del recupero successiva
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server mantiene tenere traccia della posizione del recupero successivo in modo che una sequenza di chiamate per il **GetNextRows** metodo (senza salti, modifiche di direzione o intermedi le chiamate al **FindNextRow** **Seek**, o **esecuzione di RestartPosition** metodi) legge l'intero set di righe senza ignorare o ripetizione di una riga. Posizione del recupero successivo viene modificata tramite la chiamata a **IRowset:: GetNextRows**, **IRowset:: RestartPosition**, o **IRowsetIndex:: Seek**, oppure chiamando **FindNextRow** con un valore null *pBookmark* valore. La chiamata **FindNextRow** con un valore diverso da null *pBookmark* valore non influisce sulla posizione del recupero successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di righe](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
