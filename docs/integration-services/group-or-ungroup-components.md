---
title: Raggruppare o separare componenti | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
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
- grouping containers
- tasks [Integration Services], grouping
- containers [Integration Services], grouping
- grouping tasks
ms.assetid: 34320838-c271-4f8c-90b3-1254690890bb
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9fd4deab1f2dde19f6d5ec91fe72f10a2e71135d
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="group-or-ungroup-components"></a>Raggruppare o separare componenti
  Le schede **Flusso di controllo**, **Flusso di dati**e **Gestori eventi** in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] supportano il raggruppamento comprimibile. Se un pacchetto include molti contenitori, è possibile che le schede contengano un numero di elementi talmente elevato da impedire di visualizzare contemporaneamente tutti gli elementi del flusso di controllo del pacchetto e di individuare l'elemento che si desidera utilizzare. La funzionalità raggruppamento comprimibile consente di risparmiare spazio nell'area di lavoro e semplificare la gestione di pacchetti di grandi dimensioni.  
  
 È possibile selezionare i componenti che si desidera raggruppare, eseguire il raggruppamento, quindi espandere o comprimere i gruppi in base alle proprie esigenze. Espandendo un gruppo sarà possibile accedere alle proprietà dei componenti inclusi. I vincoli di precedenza che connettono attività e contenitori vengono automaticamente inclusi nel gruppo.  
  
 Di seguito sono riportate alcune considerazioni per il raggruppamento di componenti.  
  
-   Per raggruppare componenti, il flusso di controllo, il flusso di dati o il gestore eventi deve contenere più di un componente.  
  
-   I gruppi possono inoltre essere nidificati, consentendo la creazione di sottogruppi. Nell'area di progettazione è possibile implementare più gruppi non nidificati, ma un componente può appartenere a un solo gruppo, a meno che i gruppi non siano nidificati.  
  
-   Quando si salva un pacchetto, in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] viene salvato anche il raggruppamento, ma quest'ultimo non ha alcun effetto sull'esecuzione del pacchetto. La possibilità di raggruppare componenti è una funzionalità della fase di progettazione e non influisce sul comportamento di un pacchetto in fase di esecuzione.  
  
### <a name="to-group-components"></a>Per raggruppare componenti  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo**, **Flusso di dati**o **Gestori eventi** .  
  
4.  Nell'area di progettazione della scheda selezionare i componenti da raggruppare, fare clic con il pulsante destro del mouse su un componente selezionato e quindi scegliere **Raggruppa**.  
  
5.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
### <a name="to-ungroup-components"></a>Per separare componenti  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo**, **Flusso di dati**o **Gestori eventi** .  
  
4.  Nell'area di progettazione della scheda selezionare il gruppo che contiene il componente da separare, fare clic con il pulsante destro del mouse e quindi scegliere **Separa**.  
  
5.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta o eliminazione di un'attività o un contenitore in un flusso di controllo](../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Connettere attività e contenitori tramite un vincolo di precedenza predefinito](http://msdn.microsoft.com/library/8f31f15f-98ff-4c35-b41f-8b8cfd148d75)  
  
  
