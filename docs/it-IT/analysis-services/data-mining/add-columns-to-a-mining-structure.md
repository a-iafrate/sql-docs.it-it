---
title: Aggiungere colonne a una struttura di Data Mining | Documenti Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 53b88835bc2efbc009c6d4e667ae585568a7f2d2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="add-columns-to-a-mining-structure"></a>Aggiungere colonne a una struttura di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  È possibile utilizzare Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per aggiungere colonne a una struttura di data mining dopo averla definita tramite la Creazione guidata modello di data mining. È possibile aggiungere qualsiasi colonna presente nella vista origine dati utilizzata per definire la struttura di data mining.  
  
> [!NOTE]  
>  È possibile aggiungere più copie di colonne in una struttura di data mining; tuttavia, è consigliabile evitare di utilizzare più di un'istanza della colonna all'interno dello stesso modello, in modo da evitare false correlazioni tra la colonna di origine e quella derivata.  
  
### <a name="to-add-a-column-to-a-mining-structure"></a>Per aggiungere una colonna a una struttura di data mining  
  
1.  Selezionare la scheda **Struttura di data mining** in Progettazione modelli di data mining.  
  
2.  Fare clic con il pulsante destro del mouse sulla struttura di data mining e scegliere **Aggiungi colonna**.  
  
     Verrà visualizzata la finestra di dialogo **Seleziona colonna** .  
  
3.  In **Tabella di origine**selezionare la tabella della vista origine dati in cui si trova la colonna.  
  
4.  In **Colonna di origine**selezionare la colonna che si desidera aggiungere alla struttura di data mining.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Se si aggiunge una colonna già esistente, nella struttura verrà inclusa una copia e al nome verrà aggiunto "1". È possibile specificare un nome più descrittivo per la colonna copiata digitandolo nella proprietà **Nome** della colonna della struttura di data mining.  
  
## <a name="see-also"></a>Vedere anche  
 [Data mining struttura attività e procedure](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
