---
title: Categoria di eventi Transazioni | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: event-classes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cef031b31ed079aae639d8af764e2d36cf2b60d8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="transactions-event-category"></a>Categoria di eventi Transactions
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Le classi di eventi della categoria **Transactions** consentono di monitorare lo stato delle transazioni. I nomi delle classi di eventi con prefisso **TM:** sono utilizzati per tracciare le operazioni correlate alle transazioni che vengano inviate tramite l'interfaccia di gestione delle transazioni.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Classe di evento DTCTransaction](../../relational-databases/event-classes/dtctransaction-event-class.md)|Tiene traccia delle transazioni coordinate da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC). Si tratta delle transazioni distribuite tra due o più database o istanze di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Classe di evento SQLTransaction](../../relational-databases/event-classes/sqltransaction-event-class.md)|Tiene traccia delle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN e ROLLBACK TRAN.|  
|[Classe di evento TM: Begin Tran Completed](../../relational-databases/event-classes/tm-begin-tran-completed-event-class.md)|Indica il completamento di una richiesta BEGIN TRANSACTION.|  
|[Classe di evento TM: Begin Tran Starting](../../relational-databases/event-classes/tm-begin-tran-starting-event-class.md)|Indica l'avvio di una richiesta BEGIN TRANSACTION.|  
|[Classe di evento TM: Commit Tran Completed](../../relational-databases/event-classes/tm-commit-tran-completed-event-class.md)|Indica il completamento di una richiesta COMMIT TRANSACTION.|  
|[Classe di evento TM: Commit Tran Starting](../../relational-databases/event-classes/tm-commit-tran-starting-event-class.md)|Indica l'avvio di una richiesta COMMIT TRANSACTION.|  
|[Classe di evento TM: Promote Tran Completed](../../relational-databases/event-classes/tm-promote-tran-completed-event-class.md)|Indica il completamento di una richiesta PROMOTE TRANSACTION.|  
|[Classe di evento TM: Promote Tran Starting](../../relational-databases/event-classes/tm-promote-tran-starting-event-class.md)|Indica l'avvio di una richiesta PROMOTE TRANSACTION.|  
|[Classe di evento TM: Rollback Tran Completed](../../relational-databases/event-classes/tm-rollback-tran-completed-event-class.md)|Indica il completamento di una richiesta ROLLBACK TRANSACTION.|  
|[Classe di evento TM: Rollback Tran Starting](../../relational-databases/event-classes/tm-rollback-tran-starting-event-class.md)|Indica l'avvio di una richiesta ROLLBACK TRANSACTION.|  
|[Classe di evento TM: Save Tran Completed](../../relational-databases/event-classes/tm-save-tran-completed-event-class.md)|Indica il completamento di una richiesta SAVE TRANSACTION.|  
|[Classe di evento TM: Save Tran Starting](../../relational-databases/event-classes/tm-save-tran-starting-event-class.md)|Indica l'avvio di una richiesta SAVE TRANSACTION.|  
|[Classe di evento TransactionLog](../../relational-databases/event-classes/transactionlog-event-class.md)|Traccia l'inserimento delle transazioni in un log delle transazioni di database.|  
  
  
