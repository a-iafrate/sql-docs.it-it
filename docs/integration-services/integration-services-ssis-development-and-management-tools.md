---
title: Strumenti di gestione e sviluppo di Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- studio environments [Integration Services]
- tools [Integration Services], Business Intelligence Development Studio
- Business Intelligence Development Studio, Integration Services in
- SQL Server Management Studio [Integration Services]
- SSIS, studio environments
- SQL Server Integration Services, studio environments
- tools [Integration Services], SQL Server Management Studio
ms.assetid: 4eb73e65-d9f3-4ac6-a408-abfa85afc537
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1a5190bd675c6ab9fac9b14090ed553eed3bef09
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="integration-services-ssis-development-and-management-tools"></a>Strumenti di gestione e sviluppo di Integration Services (SSIS)
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] include due strumenti per l'uso di pacchetti:  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per lo sviluppo di pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] richiesti da una soluzione aziendale. In[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] è disponibile il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in cui è possibile creare pacchetti.  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per la gestione dei pacchetti in un ambiente di produzione.  
  
## <a name="sql-server-data-tools"></a>SQL Server Data Tools  
 In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]è possibile effettuare le attività seguenti:  
  
-   Eseguire l'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per creare pacchetti di base per la copia dei dati da un'origine a una destinazione.  
  
-   Creare pacchetti che includono complessi flussi di controllo, flussi di dati, logica guidata dagli eventi e funzionalità di registrazione.  
  
-   Testare ed eseguire il debug dei pacchetti usando le funzionalità di monitoraggio e risoluzione dei problemi di Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] e le funzionalità di debug di [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
-   Creare configurazioni che aggiornano le proprietà e gli oggetti dei pacchetti in fase di esecuzione.  
  
-   Creare un'utilità di distribuzione tramite cui installare i pacchetti e le relative dipendenze in altri computer.  
  
-   Salvare copie dei pacchetti nel database msdb di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], nell'archivio pacchetti di [!INCLUDE[ssIS](../includes/ssis-md.md)] e nel file system.  
  
 Per altre informazioni su [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], vedere [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx).  
  
## <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 In[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] è disponibile il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che consente di gestire pacchetti, monitorare i pacchetti in esecuzione e determinare l'impatto e la derivazione dei dati per gli oggetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]è possibile effettuare le attività seguenti:  
  
-   Creare cartelle per organizzare i pacchetti in modo utile all'organizzazione.  
  
-   Eseguire pacchetti archiviati nel computer locale tramite l'Utilità di esecuzione pacchetti.  
  
-   Eseguire l'Utilità di esecuzione pacchetti per generare una riga di comando da usare per l'esecuzione dell'utilità del prompt dei comandi **dtexec** (dtexec.exe).  
  
-   Importare ed esportare pacchetti da e verso il database msdb di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], l'archivio pacchetti [!INCLUDE[ssIS](../includes/ssis-md.md)] e il file system.  
