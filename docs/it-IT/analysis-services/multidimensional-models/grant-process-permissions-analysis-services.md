---
title: Concedere le autorizzazioni di elaborazione (Analysis Services) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2cde8f68861eb47766b13cf95fb51a4fd2a6969
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="grant-process-permissions-analysis-services"></a>Concedere le autorizzazioni di elaborazione (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  L'amministratore può creare un ruolo dedicato alle operazioni di elaborazione di Analysis Services, consentendo di delegare tale attività specifica ad altri utenti o ad applicazioni usate per l'elaborazione automatica pianificata. Le autorizzazioni di elaborazione possono essere concesse a livello del database, del cubo, della dimensione o della struttura di data mining. A meno che non si usi un cubo o un database tabulare di grandi dimensioni è consigliabile concedere i diritti di elaborazione a livello di database, compresi tutti gli oggetti, anche quelli con dipendenze tra di loro.  
  
 Le autorizzazioni vengono concesse tramite i ruoli che associano gli oggetti alle autorizzazioni e gli account utente e di gruppo di Windows. Tenere presente che le autorizzazioni si sommano tra loro. Si supponga, ad esempio, uno scenario in cui un ruolo concede l'autorizzazione per l'elaborazione di un cubo, mentre un secondo ruolo concede allo stesso utente l'autorizzazione per l'elaborazione di una dimensione. Le autorizzazioni concesse dai due diversi ruoli si sommano, assegnando all'utente l'autorizzazione sia per l'elaborazione del cubo che per l'elaborazione della dimensione specifica all'interno del database.  
  
> [!IMPORTANT]  
>  Un utente il cui ruolo dispone solo delle autorizzazioni di elaborazione non sarà in grado di usare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per connettersi a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ed elaborare gli oggetti. Tali strumenti richiedono l'autorizzazione **Lettura definizione** per l'accesso ai metadati degli oggetti. Se non è possibile usare uno dei due strumenti, sarà necessario usare lo script XMLA per eseguire un'operazione di elaborazione.  
>   
>  È inoltre consigliabile concedere autorizzazioni **Lettura definizione** a scopo di test. Un utente che dispone di entrambe le autorizzazioni **Lettura definizione** ed **Elaborazione database** può elaborare gli oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]in modo interattivo. Per informazioni dettagliate, vedere [Concedere le autorizzazioni di lettura definizione per i metadati degli oggetti &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-read-definition-permissions-on-object-metadata-analysis-services.md) .  
  
## <a name="set-processing-permissions-at-the-database-level"></a>Impostare le autorizzazioni di elaborazione a livello di database  
 Questa sezione descrive come consentire l'elaborazione agli utenti non amministratori per tutti i cubi, le dimensioni, le strutture di data mining e i modelli di data mining all'interno del database.  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], aprire la cartella Database e selezionare un database.  
  
2.  Fare clic con il pulsante destro del mouse su **Ruoli** | **Nuovo ruolo**. Immettere un nome e una descrizione.  
  
3.  Nel riquadro **Generale** selezionare la casella di controllo **Elaborazione database** . Inoltre, selezionare **Lettura definizione** per consentire anche l'elaborazione interattiva tramite uno degli strumenti di SQL Server, ad esempio [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
4.  Nel riquadro **Appartenenza** aggiungere gli account utente e di gruppo di Windows con l'autorizzazione per l'elaborazione di qualsiasi oggetto all'interno del database.  
  
5.  Fare clic su **OK** per completare la definizione del ruolo.  
  
## <a name="set-processing-permissions-on-individual-objects"></a>Impostare le autorizzazioni di elaborazione per singoli oggetti  
 È possibile impostare le autorizzazioni di elaborazione per singoli cubi, dimensioni, strutture o modelli di data mining.  
  
 L'elaborazione può non riuscire se inavvertitamente si escludono gli oggetti che devono essere elaborati insieme, ad esempio se si abilita l'elaborazione per un cubo ma non per le dimensioni correlate. Poiché le dipendenze tra gli oggetti possono sfuggire, è sempre necessario eseguire test approfonditi quando si impostano le autorizzazioni di elaborazione per singoli oggetti.  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], aprire la cartella Database e selezionare un database.  
  
2.  Fare clic con il pulsante destro del mouse su **Ruoli** | **Nuovo ruolo**. Immettere un nome e una descrizione.  
  
3.  Nel riquadro **Generale** deselezionare la casella di controllo **Elaborazione database** . Le autorizzazioni di database non consentono di impostare le autorizzazioni per gli oggetti di livello inferiore visualizzando le opzioni per i ruoli in grigio o non selezionabili.  
  
     Tecnicamente, per i ruoli di elaborazione dedicati non sono necessarie le autorizzazioni di database. Tuttavia, senza l'autorizzazione **Lettura definizione** a livello di database non è possibile visualizzare il database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], rendendo il test più difficile.  
  
4.  Selezionare i singoli oggetti da elaborare:  
  
    -   Nel riquadro **Cubi** selezionare la casella di controllo **Elabora** per ciascun cubo.  
  
    -   Nel riquadro **Dimensioni** selezionare **Tutte le dimensioni del database**e quindi selezionare la casella di controllo **Elabora** per ciascuna dimensione. In alternativa, selezionare tutte le righe, quindi usare MAIUSC+clic per disattivare la selezione delle caselle di controllo.  
  
5.  Nel riquadro **Appartenenza** aggiungere gli account utente e di gruppo di Windows con l'autorizzazione per l'elaborazione di questi oggetti.  
  
6.  Fare clic su **OK** per completare la definizione del ruolo.  
  
## <a name="test-processing"></a>Testare l'elaborazione  
  
1.  Tenere premuto MAIUSC e fare clic con il pulsante destro del mouse su [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], scegliere **Esegui come altro utente** e connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] con un account di Windows assegnato al ruolo da testare.  
  
2.  Aprire la cartella Database e selezionare un database. Verranno visualizzati solo i database visibili ai ruoli di cui l'account è membro.  
  
3.  Fare clic con il pulsante destro del mouse su un cubo o una dimensione e scegliere **Elabora**. Scegliere un'opzione di elaborazione. Testare tutte le opzioni per tutte le combinazioni di oggetti. Se si verificano errori a causa di oggetti mancanti, aggiungere tali oggetti al ruolo.  
  
## <a name="set-processing-permissions-on-a-data-mining-structure"></a>Impostare le autorizzazioni di elaborazione per una struttura di data mining  
 È possibile creare un ruolo che conceda l'autorizzazione per l'elaborazione delle strutture di data mining, inclusa l'elaborazione di tutti i modelli di data mining.  
  
 Le autorizzazioni **Drill-through** e **Lettura definizione** usate per la visualizzazione di un modello e una struttura di data mining sono atomiche e possono essere aggiunte allo stesso ruolo o suddivise in ruoli diversi.  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], aprire la cartella Database e selezionare un database.  
  
2.  Fare clic con il pulsante destro del mouse su **Ruoli** | **Nuovo ruolo**. Immettere un nome e una descrizione. Nel riquadro **Generale** verificare che le caselle di controllo delle autorizzazioni di database siano deselezionate. Le autorizzazioni di database non consentono di impostare le autorizzazioni per gli oggetti di livello inferiore visualizzando le opzioni per i ruoli in grigio o non selezionabili.  
  
3.  Nel riquadro **Strutture di data mining** selezionare la casella di controllo **Elabora** per ciascuna struttura di data mining.  
  
4.  Nel riquadro **Appartenenza** aggiungere gli account utente e di gruppo di Windows con l'autorizzazione per l'elaborazione di qualsiasi oggetto all'interno del database.  
  
5.  Fare clic su **OK** per completare la definizione del ruolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Elaborare database, tabelle o partizioni &#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md)   
 [Elaborazione di un modello multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Concedere autorizzazioni per database & #40; Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)   
 [Concedere autorizzazioni di lettura definizione per i metadati degli oggetti & #40; Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
  
