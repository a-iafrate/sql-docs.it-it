---
title: Elemento Storage (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Storage Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.storage
- urn:schemas-microsoft-com:xml-analysis#Storage
- http://schemas.microsoft.com/analysisservices/2003/engine#Storage
helpviewer_keywords:
- Storage element
ms.assetid: c3590af8-a24b-4fd3-b846-17edbd399b6d
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 244de0f7afe8edac8ca27e7813e4ea354f926dcc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="storage-element-xmla"></a>Elemento Storage (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Specifica la quantità massima di spazio di archiviazione, in byte, utilizzata dal [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md) comando per progettare aggregazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DesignAggregations>  
   ...  
   <Storage>...</Storage>  
   ...  
</DesignAggregations>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Long|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
