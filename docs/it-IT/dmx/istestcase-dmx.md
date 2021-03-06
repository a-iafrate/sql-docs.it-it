---
title: IsTestCase (DMX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- IsTestCase
dev_langs:
- DMX
helpviewer_keywords:
- IsTestCase function
ms.assetid: 7ff4b895-9bb4-4e26-ab1b-c9049cfc2291
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 8754f92f96740c02470081b12b8fe1056c2fe04a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="istestcase-dmx"></a>IsTestCase (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indica se un case viene utilizzato come case di testing per il modello o la struttura di data mining specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IsTestCase()  
```  
  
## <a name="result-type"></a>Tipo di risultato  
 Restituisce **true** se il case è una parte del set di dati di test; in caso contrario **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se si utilizza la Creazione guidata modello di data mining per creare una struttura di data mining e il modello di data mining correlato, per impostazione predefinita il 30% dei case viene riservato per l'utilizzo come set di dati di test. I case rimanenti dell'insieme di dati vengono utilizzati per il training del modello di data mining. Lo stesso set di dati di test può essere utilizzato con tutti i modelli basati sulla struttura stessa. Tuttavia, se si utilizza DMX per creare il modello di data mining, per impostazione predefinita tutti i dati vengono utilizzati per eseguire il training del modello e non viene creato alcun set di testing. Per abilitare la creazione di un set di dati di test, è necessario impostare i parametri della clausola WITH HOLDOUT.  
  
 È possibile determinare se un set di testing è stato creato in una particolare struttura di data mining visualizzando il valore delle proprietà <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> e <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A>.  
  
> [!NOTE]  
>  Se si desidera utilizzare le funzioni IsTrainingCase o IsTestCase per restituire i dettagli sui case in un determinato modello, è necessario attivare il drill-through sul modello. Per altre informazioni, vedere [Abilitazione del drill-through per un modello di data mining](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md).  
  
 Per restituire i case che fanno parte del set di dati di training, utilizzare la funzione [IsTrainingCase &#40;DMX&#41;](../dmx/istrainingcase-dmx.md).  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa il `Targeted Mailing` struttura di data mining creati nel [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). La query restituisce tutti i case nella struttura utilizzati per il testing.  
  
```  
SELECT *  
FROM [Targeted Mailing].CASES  
WHERE IsTestCase()  
```  
  
 Per ulteriori informazioni su come includere query sui case utilizzate nel data mining, vedere [SELECT FROM &#60;modello&#62;. CASI &#40;DMX&#41; ](../dmx/select-from-model-cases-dmx.md) e [SELECT FROM &#60;struttura&#62;. CASI](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Query di Data Mining](../analysis-services/data-mining/data-mining-queries.md)   
 [Set di training e set di dati di Testing](../analysis-services/data-mining/training-and-testing-data-sets.md)  
  
  
