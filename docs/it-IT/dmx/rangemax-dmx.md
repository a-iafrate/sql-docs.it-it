---
title: RangeMax (DMX) | Documenti Microsoft
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
- RangeMax
dev_langs:
- DMX
helpviewer_keywords:
- RangeMax function
ms.assetid: 6798d9d7-c3dc-40fb-bd8e-56cb1a6d0e5f
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: a7621501b61c1f6d798ebef945b4b1e3c34278a7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="rangemax-dmx"></a>RangeMax (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il limite superiore del bucket stimato individuato per una colonna discretizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Si applica a  
 Colonne scalari.  
  
## <a name="return-type"></a>Tipo restituito  
 Valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 Il **RangeMax** funzione può essere utilizzata [SELECT DISTINCT FROM &#60;modello &#62; &#40;DMX&#41; ](../dmx/select-distinct-from-model-dmx.md) query. Quando viene utilizzato con questo tipo di query, il riferimento alla colonna scalare può contenere colonne discrete o continue stimabili o di input.  
  
 Se usato con [SELECT FROM &#60;modello&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md), il **RangeMin**, **RangeMid**, e **RangeMax**  funzioni restituiscono i valori limite effettivi del bucket specificato. Se ad esempio si esegue una stima su una colonna discretizzata, la query restituirà il numero del bucket stimato nella colonna discretizzata. Il **RangeMin**, **RangeMid**, e **RangeMax** il bucket specificato dalla stima è descritto dalle funzioni. Quando il **RangeMax** funzione viene utilizzata con un'istruzione PREDICTION JOIN, il riferimento alla colonna scalare può contenere solo colonne discrete e stimabili.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti i valori minimi, massimi e medi della colonna continua Yearly Income nel modello di data mining TM Decision Tree.  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
  
