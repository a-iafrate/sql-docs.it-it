---
title: Elemento ReadSourceData (ASSL) | Documenti Microsoft
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
- ReadSourceData Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ReadSourceData element
ms.assetid: 7da4665a-fba3-4aae-8dee-678dc14d3b05
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b6cfc8b14993307ebd9130ac39cc20476a8e8e8a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="readsourcedata-element-assl"></a>Elemento ReadSourceData (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Determina i nomi univoci generati per le gerarchie contenute all'interno di [CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubePermission>  
   ...  
   <ReadSourceData>...</ReadSourceData>  
   ...  
</CubePermission>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nessuno*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Nessuno*|Non è consentito alcun accesso ai dati disponibili nella sessione di calcolo 0.|  
|*È consentito*|È consentito l'accesso ai dati disponibili nella sessione di calcolo 0.|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento che corrisponde all'elemento padre **ReadSourceData** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.CubePermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CUBE & #40; ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Elemento Dimension & #40; ASSL & #41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
