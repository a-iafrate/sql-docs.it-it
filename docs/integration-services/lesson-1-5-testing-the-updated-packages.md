---
title: 'Passaggio 5: Test dei pacchetti aggiornati | Microsoft Docs'
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
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 683e52e5-1c7e-49ab-9ffe-6a450a1c5776
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7208df70732d42a24f41728e19847f61d6a57645
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="lesson-1-5---testing-the-updated-packages"></a>Lezione 1-5 - Test dei pacchetti aggiornati
Prima di passare alla lezione successiva, nella quale si procederà alla creazione del pacchetto di distribuzione da utilizzare per installare i pacchetti dell'esercitazione nel computer di destinazione, è consigliabile testare i pacchetti. In questa attività verranno eseguiti i pacchetti DataTransfer.dtsx e LoadXMLData, precedentemente aggiunti al progetto Deployment Tutorial e opportunamente estesi mediante le configurazioni.  
  
Quando si eseguono i pacchetti, ogni file eseguibile in essi contenuto diventa di colore verde se l'esito è positivo. Se tutti i file eseguibili sono di colore verde, il pacchetto è stato completato correttamente. È inoltre possibile visualizzare lo stato di esecuzione dei pacchetti nella scheda **Stato** .  
  
Se i pacchetti non vengono eseguiti correttamente, è necessario correggerli prima di passare alla lezione successiva.  
  
### <a name="to-run-the-datatransfer-package"></a>Per eseguire il pacchetto DataTransfer  
  
1.  In Esplora soluzioni fare clic su DataTransfer.dtsx.  
  
2.  Scegliere **Avvia debug** dal menu **Debug**.  
  
3.  Al termine dell'esecuzione del pacchetto, scegliere **Arresta debug** dal menu **Debug**.  
  
### <a name="to-run-the-loadxmldata-package"></a>Per eseguire il pacchetto LoadXMLData  
  
1.  In Esplora soluzioni fare clic su LoadXMLData.dtsx.  
  
2.  Scegliere **Avvia debug** dal menu **Debug**.  
  
3.  Al termine dell'esecuzione del pacchetto, scegliere **Arresta debug** dal menu **Debug**.  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 2: Creare il pacchetto di distribuzione in SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
  
  
  
