---
title: 'Passaggio 3: Modifica della gestione connessione File Flat | Documenti Microsoft'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 525557f034199c5e6823c18ab9fdb7c3b505a434
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-2-3---modifying-the-flat-file-connection-manager"></a>Lezione 2-3-modifica della gestione connessione File Flat
In questa attività verrà modificata la gestione connessione file flat creata e configurata nella lezione 1. Al momento della creazione, la gestione connessione file flat era stata configurata per caricare staticamente un singolo file. Per abilitare Gestione connessione file flat affinché carichi i file in modo iterativo, è necessario modificare la proprietà ConnectionString della gestione connessione in modo che accetti la variabile `User:varFileName`definita dall'utente contenente il percorso del file da caricare in fase di esecuzione.  
  
La modifica della gestione connessione in modo da usare il valore della variabile `User::varFileName`definita dall'utente per popolare la proprietà ConnectionString consente alla gestione connessione di connettersi a file flat diversi. In fase di esecuzione, ogni iterazione del contenitore Ciclo Foreach determina l'aggiornamento dinamico della variabile `User::varFileName` . L'aggiornamento della variabile quindi consente alla gestione connessione di connettersi a un file flat diverso e all'attività Flusso di dati di elaborare un set di dati diverso.  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a>Per configurare la gestione connessione file flat in modo da utilizzare una variabile per la stringa di connessione  
  
1.  Nel riquadro **Gestioni connessioni** fare clic con il pulsante destro del mouse su **Sample Flat File Source Data**e scegliere **Proprietà**.  
  
2.  Nella finestra Proprietà fare clic sulla cella vuota relativa a **Espressioni**e fare clic sul pulsante con i puntini di sospensione **(…)**.  
  
3.  Nella colonna **Proprietà** della finestra di dialogo **Editor espressioni di proprietà** digitare o selezionare **ConnectionString**.  
  
4.  Nella colonna **Espressione** fare clic sul pulsante con i puntini di sospensione **(…)** per aprire la finestra di dialogo **Generatore di espressioni** .  
  
5.  Nella finestra di dialogo **Generatore di espressioni** espandere il nodo **Variabili** .  
  
6.  Trascinare la variabile **User::varFileName**sulla casella **Espressione** .  
  
7.  Fare clic su **OK** per chiudere la finestra di dialogo **Generatore di espressioni** .  
  
8.  Fare nuovamente clic su **OK** per chiudere la finestra di dialogo **Editor espressioni di proprietà** .  
  
## <a name="next-lesson-task"></a>Attività della lezione successiva  
[Passaggio 4: Test del pacchetto creato nella lezione 2 dell'esercitazione](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
  
