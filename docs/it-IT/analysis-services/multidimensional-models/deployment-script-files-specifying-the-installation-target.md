---
title: Specifica la destinazione di installazione | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ef168e39d162aabeb6cb6eb46ce3ab61216af288
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="deployment-script-files---specifying-the-installation-target"></a>File di Script di distribuzione - specifica la destinazione di installazione
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuzione guidata di legge le informazioni sulla destinazione di installazione dal \< *nome progetto*>. deploymenttargets file. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]tale file viene creato quando si compila il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilizza il database e il server specificato nella **distribuzione** pagina del  *\<nome progetto >* **pagine delle proprietà** la finestra di dialogo per creare il \< *nome progetto*> file con estensione targets.  
  
## <a name="modifying-the-installation-target-for-deployment"></a>Modifica della destinazione di installazione per la distribuzione  
 In alcuni casi potrebbe essere necessario distribuire un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] su un database o un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diversi da quelli specificati nella pagina **Distribuzione** . Potrebbe essere utile ad esempio distribuire il progetto su un server di prova prima della distribuzione e successivamente distribuire il progetto su un server di produzione dopo il completamento delle prove. Quando il progetto è completato e testato, potrebbe essere opportuno distribuirlo su più server di produzione in un cluster con bilanciamento del carico di rete o su un server dell'area di gestione temporanea e un server di produzione.  
  
 Per distribuire un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] su un database o un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diversi, è possibile modificare la destinazione di installazione nel file di input utilizzando uno dei metodi descritti nella procedura seguente.  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>Per modificare la destinazione di installazione dopo la generazione dei file di input.  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modo interattivo. Nella pagina **Destinazione installazione** , specificare una nuova destinazione per il database e l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
     -oppure-  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso il prompt dei comandi e impostarla in modo che venga eseguita in modalità file di risposte. Per altre informazioni sulla modalità file di risposte, vedere [Esecuzione della Distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     -oppure-  
  
-   Modificare il \< *nome progetto*>. deploymenttargets file utilizzando un editor di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica opzioni di distribuzione di ruoli e partizioni](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)   
 [Specificare le impostazioni di configurazione per la distribuzione della soluzione](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)   
 [Specifica le opzioni di elaborazione](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  
