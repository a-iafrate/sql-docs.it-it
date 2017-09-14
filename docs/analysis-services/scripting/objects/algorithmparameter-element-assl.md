---
title: Elemento AlgorithmParameter (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AlgorithmParameter Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AlgorithmParameter
helpviewer_keywords:
- AlgorithmParameter element
ms.assetid: 73211495-065c-43c6-a486-be6044617263
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 33ef60da325d605250b5a429bc3fac14e8da01d7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="algorithmparameter-element-assl"></a>Elemento AlgorithmParameter (ASSL)
  Definisce un parametro per l'algoritmo utilizzato da un [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AlgorithmParameters>  
   <AlgorithmParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </AlgorithmParameter>  
</AlgorithmParameters>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AlgorithmParameters](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)|  
|Elementi figlio|[Nome](../../../analysis-services/scripting/properties/name-element-assl.md), [valore](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Un **AlgorithmParameter** è un parametro per un algoritmo del modello di data mining. Il **AlgorithmParameter** rappresenta il parametro come coppia nome/valore. Il set di parametri applicabili che un **AlgorithmParameter** può rappresentare è dipendente dall'algoritmo. Per ulteriori informazioni sui parametri per un algoritmo specifico, vedere la documentazione appropriata relativa all'algoritmo.  
  
 Parametri dell'algoritmo disponibili, incluse le informazioni di convalida e visualizzazione, possono essere recuperati dal [DMSCHEMA_MINING_SERVICE_PARAMETERS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md) set di righe dello schema.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AlgorithmParameter>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MiningModel &#40; ASSL &#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)   
 [Elemento Algorithm &#40; ASSL &#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)   
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  