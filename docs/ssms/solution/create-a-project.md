---
title: Creare un progetto | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.newproject
- vs.addnewproject
helpviewer_keywords:
- projects [SQL Server Management Studio], creating
ms.assetid: 7897be19-365b-4b06-bcf0-8a669f67a673
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 07eabcd5f183ff5ecba9d6718a8a51aae8a80503
ms.lasthandoff: 04/11/2017

---
# <a name="create-a-project"></a>Creazione di un progetto
È possibile creare uno o più progetti in una soluzione esistente.  
  
### <a name="to-create-a-new-project-and-add-it-to-a-solution"></a>Per creare un nuovo progetto e aggiungerlo a una soluzione  
  
1.  Selezionare la soluzione in Esplora soluzioni.  
  
2.  Nel menu **File** , fare clic su **Aggiungi**e scegliere **Nuovo progetto**.  
  
3.  Nella finestra di dialogo  **Nuovo progetto** fare clic su un tipo di progetto.  
  
    **Modelli**  
    Nella casella **Modelli** selezionare un modello. Sotto la casella **Modelli** viene visualizzata una breve descrizione del modello di progetto selezionato.  
  
    **Nome**  
    Immettere il nome del progetto script che si desidera creare. Nel percorso visualizzato nel campo **Percorso** viene inoltre creata una cartella con lo stesso nome del progetto. Per alcuni progetti, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] crea file di origine e altri file di supporto e li aggiunge alla nuova cartella di progetto.  
  
    > [!NOTE]  
    > Per alcuni tipi di progetto, la casella di testo **Name** non è disponibile perché il nome viene impostato automaticamente quando si specifica il percorso. Le applicazioni e i servizi Web ad esempio vengono posizionati su un server Web e i relativi nomi si basano sulla directory virtuale specificata su tale server.  
  
    I nomi non possono includere i caratteri seguenti:  
  
    -   Cancelletto (#)  
  
    -   Percentuale (%)  
  
    -   E commerciale (&)  
  
    -   Asterisco (*)  
  
    -   Barra verticale {|}  
  
    -   Barra rovesciata (\\)  
  
    -   Due punti (:)  
  
    -   Virgoletta (")  
  
    -   Minore di (\<)  
  
    -   Maggiore di (>)  
  
    -   Punto interrogativo (?)  
  
    -   Barra (/)  
  
    -   Spazi iniziali o finali (' ')  
  
    -   Nomi riservati di Microsoft Windows o MS-DOS, ad esempio "nul", "aux", "con", "com1", "lpt1" e così via  
  
    **Percorso**  
    Immettere il percorso in cui si desidera creare il progetto oppure sceglierne uno dall'elenco.  
  
    **Sfoglia**  
    Apre la finestra di dialogo **Percorso progetto** che consente di per selezionare una nuova directory in cui salvare il progetto.  
  
    **Soluzione**  
    Selezionare **Crea nuova soluzione** per creare una soluzione in Esplora soluzioni. Selezionare **Aggiungi a soluzione** per aggiungere il nuovo progetto alla soluzione attualmente aperta in Esplora soluzioni.  
  
    **Crea directory per soluzione**  
    Consente di abilitare la casella di testo **Nome soluzione** . Questa opzione consente di creare una nuova directory con il nome scelto per il progetto e la soluzione.  
  
    **Nome soluzione**  
    Immettere il nome della nuova soluzione in cui si desidera creare il progetto. Per impostazione predefinita, in questo campo è visualizzato lo stesso nome digitato nel campo **Nome** .  
  
    **Note** : per accedere a questa opzione, è necessario selezionare entrambe le caselle di controllo **Crea nuova soluzione** in **Soluzione** e **Crea directory per soluzione** . Alcuni modelli di progetto, ad esempio le applicazioni Web, non supportano questa opzione.  
  
    **Aggiungi al controllo del codice sorgente**  
    Se questa casella di controllo è selezionata, l'applicazione del controllo del codice sorgente si apre quando si fa clic su **OK**. Per continuare, immettere tutte le informazioni richieste dall'applicazione del controllo del codice sorgente. Per utilizzare questa opzione, è necessario disporre di un'applicazione client del controllo del codice sorgente.  
  
4.  Scegliere **OK**.  
  
È possibile stabilire un nome per il progetto script. I nomi delle cartelle vengono invece stabiliti da [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] e non possono essere modificati. È possibile configurare il percorso e l'unità per il set di cartelle comune mediante la finestra di dialogo **Aggiungi nuovo progetto** . Fare clic con il pulsante destro del mouse sull'icona della soluzione in **Esplora soluzioni**e scegliere **Aggiungi**. Il percorso predefinito per le cartelle dei progetti script è C:\Documents and Settings\\\*nomeutente*\Documenti\SQL Server Management Studio\Projects\\.  
  
## <a name="see-also"></a>Vedere anche  
[Esplora soluzioni](../../ssms/solution/solution-explorer.md)  
[Aggiunta di un progetto esistente a una soluzione](../../ssms/solution/add-an-existing-project-to-a-solution.md)  
[Aggiunta di nuovi elementi a un progetto](../../ssms/solution/add-new-items-to-a-project.md)  
[Aggiunta di elementi esistenti a un progetto](../../ssms/solution/add-existing-items-to-a-project.md)  
[Modifica del percorso predefinito per i progetti](../../ssms/solution/change-the-default-location-for-projects.md)  
[Rimozione o eliminazione di un elemento o di un progetto](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
[Eliminazione di una soluzione](../../ssms/solution/delete-a-solution.md)  
  
