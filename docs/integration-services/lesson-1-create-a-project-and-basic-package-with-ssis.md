---
title: 'Lezione 1: Creare un progetto e un pacchetto di base con SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4d501dc2b06c68726466d90d14587218c03d4d0d
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="lesson-1-create-a-project-and-basic-package-with-ssis"></a>Lezione 1: Creare un progetto e un pacchetto di base

 > Per contenuti relativi a versioni precedenti di SQL Server, vedere [Lezione 1: Creazione del progetto e del pacchetto di base](https://msdn.microsoft.com/library/ms170419(SQL.120).aspx).

In questa lezione verrà creato un pacchetto ETL semplice tramite cui vengono estratti i dati da un'unica origine file flat, trasformati i dati usando due componenti di trasformazione Ricerca e scritti i dati in questione nella tabella dei fatti **FactCurrency** di **AdventureWorksDW2012**. In questa lezione si imparerà a creare nuovi pacchetti, aggiungere e configurare connessioni origine e destinazione dati e usare nuovi componenti flusso di controllo e flusso di dati.  
  
> [!IMPORTANT]  
> Per eseguire questa esercitazione, è necessario il database di esempio **AdventureWorksDW2012** . Per altre informazioni sull'installazione e la distribuzione di **AdventureWorksDW2012**, vedere gli [esempi di Reporting Services su CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="understanding-the-package-requirements"></a>Informazioni sui requisiti del pacchetto  
Per questa esercitazione è richiesto Microsoft SQL Server Data Tools.  
  
Per altre informazioni sull'installazione di SQL Server Data Tools, vedere [Scaricare SQL Server Data Tools (SSDT)](http://msdn.microsoft.com/data/hh297027).  
  
Prima di creare un pacchetto è necessario conoscere bene la formattazione usata nei dati di origine e nella destinazione. Dopo avere acquisito familiarità con questi due formati di dati sarà possibile definire le trasformazioni necessarie per eseguire il mapping tra i dati di origine e la destinazione.  
  
### <a name="looking-at-the-source"></a>Esame dell'origine  
In questa esercitazione vengono usati i dati valutari contenuti nel file flat SampleCurrencyData.txt. I dati di origine sono contenuti nelle quattro colonne seguenti: il tasso medio della valuta, un codice valuta, un codice data e il tasso di fine giornata.  
  
Di seguito viene riportato un esempio dei dati di origine contenuti nel file SampleCurrencyData.txt:  
  
<pre>1.00070049USD9/3/05 0:001.001201442  
1.00020004USD9/4/05 0:001  
1.00020004USD9/5/05 0:001.001201442  
1.00020004USD9/6/05 0:001  
1.00020004USD9/7/05 0:001.00070049  
1.00070049USD9/8/05 0:000.99980004  
1.00070049USD9/9/05 0:001.001502253  
1.00070049USD9/10/05 0:000.99990001  
1.00020004USD9/11/05 0:001.001101211  
1.00020004USD9/12/05 0:000.99970009</pre>  
  
Quando si usano dati di origine di file flat, è importante capire in che modo Gestione connessione file flat interpreta i relativi dati. Se l'origine del file flat è Unicode, tutte le colonne vengono definite nella gestione connessione file flat come [DT_WSTR] con una larghezza predefinita di 50. Se l'origine del file flat è con codifica ANSI, le colonne sono definite come [DT_STR] con una larghezza di 50. Le impostazioni predefinite sono liberamente modificabili per adattare al meglio i tipi di colonna ai dati. Per farlo, è necessario esaminare il tipi di dati della destinazione di scrittura dei dati e scegliere il tipo corretto all'interno di Gestione connessione file flat.  
  
### <a name="looking-at-the-destination"></a>Esame della destinazione  
La destinazione finale dei dati di origine è la tabella dei fatti **FactCurrency** di **AdventureWorksDW**. La tabella dei fatti **FactCurrency** presenta quattro colonne e ha relazioni con due tabelle delle dimensioni, come mostrato nella tabella seguente.  
  
|Nome colonna|Tipo di dati|Tabella di ricerca|Colonna di ricerca|  
|---------------|-------------|----------------|-----------------|  
|AverageRate|FLOAT|None|None|  
|CurrencyKey|int (FK)|DimCurrency|CurrencyKey (PK)|  
|DateKey|int (FK)|DimDate|DateKey (PK)|  
|EndOfDayRate|FLOAT|None|None|  
  
### <a name="mapping-source-data-to-be-compatible-with-the-destination"></a>Mapping dei dati di origine per la compatibilità con la destinazione  
L'analisi dei formati dei dati di origine e di destinazione indica che per i valori **CurrencyKey** e **DateKey** saranno necessarie le ricerche. Tramite le trasformazioni mediante le quali verranno svolte queste ricerche si otterranno i valori **CurrencyKey** e **DateKey** usando le chiavi alternative ottenute dalle tabelle delle dimensioni **DimCurrency** e **DimDate** .  
  
|Colonna file flat|Nome tabella|Nome colonna|Tipo di dati|  
|--------------------|--------------|---------------|-------------|  
|0|FactCurrency|AverageRate|FLOAT|  
|1|DimCurrency|CurrencyAlternateKey|nchar (3)|  
|2|DimDate|FullDateAlternateKey|Data|  
|3|FactCurrency|EndOfDayRate|FLOAT|  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
In questa lezione sono incluse le attività seguenti:  
  
-   [Passaggio 1: Creazione di un nuovo progetto di Integration Services](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [Passaggio 2: Aggiunta e configurazione di una gestione connessione file flat](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [Passaggio 3: Aggiunta e configurazione di una gestione connessione OLE DB](../integration-services/lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [Passaggio 4: Aggiunta di un'attività Flusso di dati al pacchetto](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [Passaggio 5: Aggiunta e configurazione dell'origine file flat](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [Passaggio 6: Aggiunta e configurazione delle trasformazioni Ricerca](../integration-services/lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [Passaggio 7: Aggiunta e configurazione della destinazione OLE DB](../integration-services/lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [Passaggio 8: Semplificazione della comprensione del pacchetto della lezione 1](../integration-services/lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [Passaggio 9: Test del pacchetto creato nella lezione 1 dell'esercitazione](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Inizio della lezione  
[Passaggio 1: Creazione di un nuovo progetto di Integration Services](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
