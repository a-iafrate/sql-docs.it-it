---
title: MSSQLSERVER_1458 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75bd002a0834c5d8bd3b43407f4ba2d156f2ce0d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver1458"></a>MSSQLSERVER_1458
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1458|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBM_FAILREDO_ON_PRIMARY|  
|Testo del messaggio|La copia principale del database '%.*ls' ha rilevato l'errore % d, con stato% d e gravità% d. Il mirroring del database è stato sospeso. Risolvere il problema e riprendere il mirroring.|  
  
## <a name="explanation"></a>Spiegazione  
Il messaggio indica che il database principale ha rilevato un errore che ha causato la sospensione del mirroring del database.  
  
## <a name="user-action"></a>Azione dell'utente  
Nella maggior parte dei casi per la risoluzione di questo errore non è richiesto l'intervento dell'utente. Se il problema persiste, è in genere sufficiente riavviare l'istanza del database o del server per correggerlo. Per ulteriori informazioni, ricercare nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di ogni partner l'errore associato che ha preceduto la visualizzazione del messaggio.  
  
## <a name="see-also"></a>Vedere anche  
[Monitoraggio del mirroring del database &#40;SQL Server&#41;](~/database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
