---
title: 'Passaggio 6: Aggiunta e configurazione delle trasformazioni Ricerca | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
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
ms.assetid: 5c59f723-9707-4407-80ae-f05f483cf65f
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 41d236698902fde3dd771650c98fb8ce0117b73c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="lesson-1-6---adding-and-configuring-the-lookup-transformations"></a>Lezione 1-6 - Aggiunta e configurazione delle trasformazioni Ricerca
Dopo aver configurato l'origine file flat per l'estrazione di dati dal file di origine si definiranno le trasformazioni Ricerca necessarie per ottenere i valori di **CurrencyKey** e **DateKey**. Una trasformazione Ricerca esegue una ricerca tramite l'unione in join dei dati della colonna di input specificata con una colonna di un set di dati di riferimento. Il set di dati di riferimento può essere una vista o tabella esistente, una nuova tabella o il risultato di un'istruzione SQL. In questa esercitazione, la trasformazione Ricerca utilizza una gestione connessione OLE DB per connettersi al database che contiene i dati che costituiscono l'origine del set di dati di riferimento.  
  
> [!NOTE]  
> È anche possibile configurare la trasformazione Ricerca per collegarsi a una cache che contiene il set di dati di riferimento. Per altre informazioni, vedere [Trasformazione Ricerca](../integration-services/data-flow/transformations/lookup-transformation.md).  
  
In questa esercitazione verranno aggiunti al pacchetto e configurati i due componenti di trasformazione Ricerca seguenti:  
  
-   Una trasformazione per eseguire la ricerca di valori della colonna **CurrencyKey** della tabella delle dimensioni **DimCurrency** in base alla corrispondenza con i valori della colonna **CurrencyID** del file flat.  
  
-   Una trasformazione per eseguire una ricerca di valori della colonna **DateKey** della tabella delle dimensioni **DimDate** in base alla corrispondenza con i valori della colonna **CurrencyDate** del file flat.  
  
In entrambi i casi nella trasformazione Ricerca verrà utilizzata la gestione connessione OLE DB creata in precedenza.  
  
### <a name="to-add-and-configure-the-lookup-currency-key-transformation"></a>Per aggiungere e configurare la trasformazione Lookup Currency Key  
  
1.  Nella **Casella degli strumenti SSIS**espandere **Comune**, quindi trascinare **Ricerca** sull'area di progettazione della scheda **Flusso di dati** . Posizionare Ricerca proprio sotto l'origine **Extract Sample Currency Data**.  
  
2.  Fare clic sull'origine del file flat **Extract Sample Currency Data** e trascinare la freccia verde sulla trasformazione **Ricerca** appena aggiunta per collegare i due componenti.  
  
3.  Nell'area di progettazione **Flusso di dati** fare clic su **Ricerca** nella trasformazione **Ricerca** e cambiare il nome in **Lookup Currency Key**.  
  
4.  Fare doppio clic sulla trasformazione **Lookup Currency Key** per visualizzare l'Editor trasformazione Ricerca.  
  
5.  Nella pagina **Generale** effettuare le selezioni seguenti:  
  
    1.  Selezionare **Full cache**.  
  
    2.  Nell'area **Tipo di connessione** selezionare **Gestione connessione OLE DB**.  
  
6.  Nella pagina **Connessione** effettuare le selezioni seguenti:  
  
    1.  Nella finestra di dialogo **Gestione connessione OLE DB** assicurarsi che sia visualizzato **localhost.AdventureWorksDW2012** .  
  
    2.  Selezionare **Usa i risultati di una query SQL**, quindi digitare o copiare l'istruzione SQL seguente:  
  
        ```sql
        SELECT * FROM [dbo].[DimCurrency]
        WHERE [CurrencyAlternateKey]
        IN ('ARS', 'AUD', 'BRL', 'CAD', 'CNY',
            'DEM', 'EUR', 'FRF', 'GBP', 'JPY',
            'MXN', 'SAR', 'USD', 'VEB')
        ```  
  
7.  Nella pagina **Colonne** effettuare le selezioni seguenti:  
  
    1.  Nel pannello **Colonne di input disponibili** trascinare **CurrencyID** sul pannello **Colonne di ricerca disponibili** e rilasciarlo su **CurrencyAlternateKey**.  
  
    2.  Nell'elenco **Colonne di ricerca disponibili** selezionare la casella di controllo a sinistra di **CurrencyKey**.  
  
8.  Fare clic su **OK** per tornare all'area di progettazione **Flusso di dati** .  
  
9. Fare clic con il pulsante destro del mouse sulla trasformazione Lookup Currency Key e scegliere **Proprietà**.  
  
10. Nella finestra Proprietà verificare che la proprietà **LocaleID** sia impostata su **Inglese (Stati Uniti)** e che la proprietà **DefaultCodePage** sia impostata su **1252**.  
  
### <a name="to-add-and-configure-the--lookup-datekey-transformation"></a>Per aggiungere e configurare la trasformazione Lookup DateKey  
  
1.  Nella **Casella degli strumenti SSIS**trascinare **Ricerca** sull'area di progettazione **Flusso di dati** . Posizionare Ricerca proprio sotto la trasformazione **Lookup Currency Key** .  
  
2.  Fare clic sulla trasformazione **Lookup Currency Key** e trascinare la freccia verde sulla nuova trasformazione **Ricerca** per collegare i due componenti.  
  
3.  Nella finestra di dialogo **Selezione input e output** fare clic su **Output corrispondenza ricerca** nella casella di riepilogo **Output** e fare clic su **OK**.  
  
4.  Nell'area di progettazione **Flusso di dati** fare clic su **Ricerca** nella trasformazione **Ricerca** appena aggiunta e impostare il nome su **Lookup Date Key**.  
  
5.  Fare doppio clic sulla trasformazione **Lookup Date Key** .  
  
6.  Nella pagina **Generale** selezionare **Partial cache**.  
  
7.  Nella pagina **Connessione** effettuare le selezioni seguenti:  
  
    1.  Nella finestra di dialogo **Gestione connessione OLE DB** assicurarsi che sia visualizzato **localhost.AdventureWorksDW2012** .  
  
    2.  Nella casella **Usa una tabella o una vista** digitare o selezionare **[dbo].[DimDate]**.  
  
8.  Nella pagina **Colonne** effettuare le selezioni seguenti:  
  
    1.  Nel pannello **Colonne di input disponibili** trascinare **CurrencyDate** sul pannello **Colonne di ricerca disponibili** e rilasciarlo su **FullDateAlternateKey**.  
  
    2.  Nell'elenco **Colonne di ricerca disponibili** selezionare la casella di controllo a sinistra di **DateKey**.  
  
9. Nella pagina **Avanzate** rivedere le opzioni di memorizzazione nella cache.  
  
10. Fare clic su **OK** per tornare all'area di progettazione **Flusso di dati**.  
  
11. Fare clic con il pulsante destro del mouse sulla trasformazione Lookup Date Key e scegliere **Proprietà.**  
  
12. Nella finestra Proprietà verificare che la proprietà **LocaleID** sia impostata su **Inglese (Stati Uniti)** e che la proprietà **DefaultCodePage** sia impostata su **1252**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 7: Aggiunta e configurazione della destinazione OLE DB](../integration-services/lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
## <a name="see-also"></a>Vedere anche  
[Trasformazione Ricerca](../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
  
