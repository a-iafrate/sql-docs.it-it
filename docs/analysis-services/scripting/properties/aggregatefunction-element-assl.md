---
title: Elemento AggregateFunction (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AggregateFunction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregateFunction
helpviewer_keywords:
- AggregateFunction element
ms.assetid: 880b6bd0-d62a-4221-831c-39f748ee84f2
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e0ed42e0e1803fbd2dab49ca5098cb880459ea5d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="aggregatefunction-element-assl"></a>Elemento AggregateFunction (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce il tipo di funzione di aggregazione usata da un [misura](../../../analysis-services/scripting/objects/measure-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Measure>  
   ...  
   <AggregateFunction>...</AggregateFunction>  
   ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Sum*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Misura](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Sum*|La misura viene aggregata utilizzando il **somma** (funzione).|  
|*Count*|La misura viene aggregata utilizzando il **conteggio** (funzione).|  
|*Min*|La misura viene aggregata utilizzando il **Min** (funzione).|  
|*Max*|La misura viene aggregata utilizzando il **Max** (funzione).|  
|*DistinctCount*|La misura viene aggregata utilizzando il **DistinctCount** (funzione).|  
|*Nessuno*|Non viene eseguita alcuna aggregazione della misura.|  
|*ByAccount*|La misura viene aggregata in base al tipo di conto.|  
|*AverageOfChildren*|La misura viene aggregata restituendo la media dei relativi membri figlio.|  
|*FirstChild*|La misura viene aggregata restituendone il primo membro figlio.|  
|*LastChild*|La misura viene aggregata restituendone l'ultimo membro figlio.|  
|*FirstNonEmpty*|La misura viene aggregata restituendone il primo membro non vuoto.|  
|*LastNonEmpty*|La misura viene aggregata restituendone l'ultimo membro non vuoto.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **AggregateFunction** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
