---
title: MSSQLSERVER_9955 | Microsoft Docs
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
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 274dfd7f0a8d54966a8788b6bb29a1389cd0c04b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver9955"></a>MSSQLSERVER_9955
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|9955|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|FTXT2_MSSEARCHACCESSDENY|  
|Testo del messaggio|Impossibile creare la named pipe '%ls' per comunicare con il daemon di filtri full-text (errore di Windows: %d). Una named pipe esiste già per il processo host del daemon di filtri, il sistema non dispone di risorse sufficienti oppure la ricerca del numero di identificazione di sicurezza (SID) per il gruppo account del daemon di filtri non è riuscita. Per risolvere il problema, interrompere eventuali processi del daemon di filtri full-text in esecuzione e, se necessario, riconfigurare l'account di servizio dell'utilità di avvio del daemon full-text.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio viene visualizzato quando in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è possibile creare una named pipe per comunicare con il daemon di filtri full-text. Una named pipe esiste già per il processo host del daemon di filtri, il sistema non dispone di risorse sufficienti oppure la ricerca del numero di identificazione di sicurezza (SID) per il gruppo account del daemon di filtri non è riuscita.  
  
## <a name="user-action"></a>Azione dell'utente  
Per risolvere il problema, interrompere eventuali processi del daemon di filtri full-text in esecuzione e, se necessario, riconfigurare l'account host del daemon full-text utilizzando Gestione configurazione SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
[Gestione configurazione SQL Server](~/relational-databases/sql-server-configuration-manager.md)  
[Impostare l'account del servizio dell'Utilità di avvio del daemon di filtri full-text](~/relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)  
[Ricerca full-text](~/relational-databases/search/full-text-search.md)  
  
