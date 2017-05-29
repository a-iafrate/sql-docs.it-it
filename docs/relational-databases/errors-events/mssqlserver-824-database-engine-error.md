---
title: MSSQLSERVER_824 | Microsoft Docs
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
- 824 (Database Engine error)
ms.assetid: 2aa22246-2712-4fdb-9744-36e7e6f3175e
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 95ecf5e2bf8a43eb46e14281d356a2b029b0b490
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver824"></a>MSSQLSERVER_824
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|824|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|B_HARDSSERR|  
|Testo del messaggio|SQL Server ha rilevato un errore di I/O logico legato alla consistenza. Errore %1!s! durante un'operazione di %S_MSG della pagina %S_PGID nel database con ID %d all'offset %#016I64x nel file '%ls'.  Per informazioni più dettagliate, vedere i messaggi aggiuntivi nel log degli errori di SQL Server e nel registro eventi di sistema.|  
  
## <a name="explanation"></a>Spiegazione  
Questo errore indica che, sebbene Windows segnali che la pagina è stata correttamente letta dal disco, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha individuato un errore nella pagina. Questo errore è simile all'errore 823, con la sola differenza che Windows non ha rilevato l'errore. Indica in genere un problema relativo al sottosistema di I/O, ad esempio un'unità disco danneggiata, problemi relativi al firmware del disco, un driver di dispositivo difettoso e così via. Per altre informazioni sugli errori di I/O, vedere il capitolo 2 della pagina relativa alle [nozioni fondamentali sull'I/O in Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=69370).  
  
## <a name="user-action"></a>Azione dell'utente  
  
### <a name="look-for-hardware-failure"></a>Individuare errori hardware  
Eseguire gli strumenti di diagnostica hardware e risolvere eventuali problemi. Esaminare inoltre il registro di sistema e il registro applicazioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, nonché il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per stabilire se l'errore è dovuto a un problema hardware. Risolvere tutti i problemi relativi all'hardware indicati nei log.  
  
In caso di problemi persistenti che provocano il danneggiamento dei dati, provare a sostituire i vari componenti hardware per isolare il problema. Verificare che nel sistema non sia abilitata la memorizzazione nella cache in scrittura sul controller del disco. Se si ritiene che il problema sia dovuto alla memorizzazione nella cache in scrittura, rivolgersi al fornitore dell'hardware.  
  
Infine, potrebbe essere conveniente passare a un nuovo sistema hardware. A tale scopo può essere necessario riformattare le unità disco e reinstallare il sistema operativo.  
  
### <a name="restore-from-backup"></a>Eseguire un ripristino da backup  
Se il problema non è correlato all'hardware ed è disponibile un backup valido noto, ripristinare il database dal backup.  
  
Provare a cambiare i database per utilizzare l'opzione PAGE_VERIFY CHECKSUM. Per informazioni su PAGE_VERIFY, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="see-also"></a>Vedere anche  
[Gestire la tabella suspect_pages &#40;SQL Server&#41;](~/relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
