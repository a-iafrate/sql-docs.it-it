---
title: Data Mining Extensions (DMX) di riferimento agli operatori | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- operators [DMX]
- DMX [Analysis Services], operators
- Data Mining Extensions [Analysis Services], operators
ms.assetid: a6d747c0-9ff0-475f-86cd-34bebd79c21a
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 1f9a7d4921ce1f5fd82eb832f9ed66550931a218
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-mining-extensions-dmx-operator-reference"></a>Guida di riferimento agli operatori DMX (Data Mining Extensions)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Il linguaggio di Data Mining Extensions (DMX) in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supporta gli operatori aritmetici, di assegnazione, confronto, logici e unari. Gli operatori supportati da DMX sono elencati nella tabella seguente.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[+ &#40;Aggiungi&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|Operatore aritmetico che esegue una somma tra due numeri.|  
|[- &#40;Sottrarre&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|Operatore aritmetico che sottrae un numero da un altro.|  
|[&#42;&#40;Moltiplica&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|Operatore aritmetico che esegue una moltiplicazione tra due numeri.|  
|[&#40;Dividere&#41; &#40;DMX&#41;](../dmx/divide-dmx.md)|Operatore aritmetico che divide un numero per un altro.|  
|[&#60;&#40;Minore di&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|Operatore di confronto. Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è minore di quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#62;&#40;Maggiore di&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|Operatore di confronto. Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è maggiore di quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[= &#40;Uguale a&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|Operatore di confronto. Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è uguale a quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#60;&#62;&#40;Non è uguale a&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|Operatore di confronto. Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è diverso da quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#60;= &#40;Minore o uguale a&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|Operatore di confronto. Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è minore o uguale a quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#62;= &#40;Maggiore o uguale a&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|Operatore di confronto. Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è maggiore o uguale a quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[E &AMP;#40;DMX&AMP;#41;](../dmx/and-dmx.md)|Operatore logico che esegue la congiunzione di due espressioni numeriche.|  
|[NON &AMP;#40;DMX&AMP;#41;](../dmx/not-dmx.md)|Operatore logico che esegue la negazione di un'espressione numerica.|  
|[O &AMP;#40;DMX&AMP;#41;](../dmx/or-dmx.md)|Operatore logico che esegue la disgiunzione di due espressioni numeriche.|  
|[+ &#40;Positivo&#41; &#40;DMX&#41;](../dmx/positive-dmx.md)|Operatore unario che restituisce il valore positivo di un'espressione numerica.|  
|[- &#40;Negativo&#41; &#40;DMX&#41;](../dmx/negative-dmx.md)|Operatore unario che restituisce il valore negativo di un'espressione numerica.|  
|[Doppia barra &#40;commento&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md)|Indica una stringa di testo che non deve essere eseguita da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. È possibile nidificare i commenti in un'istruzione DMX, includerli alla fine di una riga di codice o inserirli in una riga distinta.|  
|[- &#40;Commento&#41; &#40;DMX&#41; riepilogo](../dmx/comment-dmx-summary.md)|Indica una stringa di testo che non deve essere eseguita da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. È possibile nidificare i commenti in un'istruzione DMX, includerli alla fine di una riga di codice o inserirli in una riga distinta.|  
|[Barre a stella &#40;commento&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)|Indica una stringa di testo che non deve essere eseguita da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. È possibile nidificare i commenti in un'istruzione DMX, includerli alla fine di una riga di codice o inserirli in una riga distinta.|  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Data Mining &#40;DMX&#41; riferimento alla funzione](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Estensioni Data Mining &#40;DMX&#41; convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Estensioni Data Mining &#40;DMX&#41; gli elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Gli operatori &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
