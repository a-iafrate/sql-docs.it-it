---
title: Avviare Monitoraggio mirroring del database (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: database-mirroring
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- Database Mirroring Monitor [SQL Server], starting
- database mirroring [SQL Server], monitoring
ms.assetid: 53165335-97ca-4f88-8e78-22f1839dee98
caps.latest.revision: 20
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cacfac4a57267ac6addbf357aeeb7cb32323cd1d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="start-database-mirroring-monitor-sql-server-management-studio"></a>Avviare Monitoraggio mirroring del database (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Monitoraggio mirroring del database è un componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Monitoraggio avviato da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!NOTE]  
>  Il monitoraggio mirroring del database non è disponibile in tutte le edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
### <a name="to-launch-the-database-mirroring-monitor"></a>Per avviare Monitoraggio mirroring del database  
  
1.  Dopo aver attivato la connessione all'istanza del server principale, in Esplora oggetti fare clic sul nome del server per espandere l'albero.  
  
2.  Espandere **Database**e selezionare il database da monitorare.  
  
3.  Fare clic con il pulsante destro del mouse sul database, selezionare **Attività**e quindi fare clic su **Avvia Monitoraggio mirroring del database**.  
  
4.  Nella finestra di dialogo **Monitoraggio mirroring del database** fare clic su **Registra database con mirroring** per registrare uno o più database con mirroring.  
  
    > [!NOTE]  
    >  Quando si registra un database in un partner, automaticamente verrà registrato anche nell'altro partner. Se il server di monitoraggio dispone già delle credenziali per la connessione all'istanza dell'altro partner, eseguirà automaticamente la connessione. In caso contrario tenterà di eseguire la connessione tramite l'autenticazione di Windows. Se si vuole modificare le credenziali usate per la connessione alle istanze del server, fare clic su **Quando viene scelto OK visualizza la finestra di dialogo Gestione connessioni a istanze server**.  
  
 Per altre informazioni su Monitoraggio mirroring del database, vedere [Panoramica di Monitoraggio mirroring del database](../../database-engine/database-mirroring/database-mirroring-monitor-overview.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
  
