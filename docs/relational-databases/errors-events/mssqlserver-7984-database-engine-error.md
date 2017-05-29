---
title: MSSQLSERVER_7984 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 7984 (Database Engine error)
ms.assetid: e3192f56-e4e2-41da-b132-65f1e7540b1a
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2d5f6e5010c18c2bed4169a0fe8fdaefb3b49d14
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver7984"></a>MSSQLSERVER_7984
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7984|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC2_PRE_CHECKS_BAD_PAGE_TYPE|  
|Testo del messaggio|Controlli preliminari su tabella di sistema: ID di oggetto O_ID. Pagina P_ID con tipo imprevisto PAGETYPE. Istruzione di controllo interrotta a causa di un errore irreversibile.|  
  
## <a name="explanation"></a>Spiegazione  
Nel livello dati dell'oggetto specificato è stata trovata una pagina con un tipo diverso da DATA_PAGE. L'errore viene generato durante la prima fase dei controlli del comando DBCC CHECKDB. Durante tale fase, DBCC CHECKDB esegue controlli primitivi nelle pagine dei dati delle tabelle di base di sistema critiche.  
  
> [!NOTE]  
> Non è possibile correggere eventuali errori rilevati nelle tabelle di sistema. Il comando DBCC CHECKDB verrà pertanto terminato immediatamente.  
  
## <a name="user-action"></a>Azione dell'utente  
  
### <a name="look-for-hardware-failure"></a>Individuare errori hardware  
Eseguire gli strumenti di diagnostica hardware e risolvere eventuali problemi. Esaminare inoltre il registro di sistema di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows e il registro delle applicazioni, nonché il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per stabilire se l'errore è dovuto a un problema hardware. Risolvere tutti i problemi relativi all'hardware indicati nei log.  
  
In caso di problemi persistenti che provocano il danneggiamento dei dati, provare a sostituire i vari componenti hardware per isolare il problema. Verificare che nel sistema non sia abilitata la memorizzazione nella cache in scrittura sul controller del disco. Se si ritiene che il problema sia dovuto alla memorizzazione nella cache in scrittura, rivolgersi al fornitore dell'hardware.  
  
Infine, potrebbe essere conveniente passare a un nuovo sistema hardware. A tale scopo può essere necessario riformattare le unità disco e reinstallare il sistema operativo.  
  
### <a name="restore-from-backup"></a>Eseguire un ripristino da backup  
Se il problema non è correlato all'hardware ed è disponibile un backup valido noto, ripristinare il database dal backup.  
  
### <a name="run-dbcc-checkdb"></a>Eseguire DBCC CHECKDB  
Non applicabile. L'errore non può essere corretto automaticamente. Se non è possibile ripristinare il database da un backup, contattare il Servizio Supporto Tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
