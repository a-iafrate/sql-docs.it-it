---
title: Elemento MeasureGroups (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 44aa103a297c3131e769136d2c5f6e936c746f37
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="measuregroups-element-assl"></a>Elemento MeasureGroups (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la raccolta di [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) elementi associati all'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or CubeBinding, Perspective -->  
   ...  
   <MeasureGroups>  
      <MeasureGroup>...</MeasureGroup> <!-- parent: Cube -->  
      <MeasureGroup xsi:type="MeasureGroupBinding">...</MeasureGroup> <!-- parent: CubeBinding -->  
      <MeasureGroup xsi:type="PerspectiveMeasureGroup">...</MeasureGroup> <!-- parent: Perspective -->  
   </MeasureGroups>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cubo](../../../analysis-services/scripting/objects/cube-element-assl.md), [CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md), [prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
|Elementi figlio|Vedere la tabella.|  
  
|Predecessore o padre|Elemento figlio|  
|------------------------|-------------------|  
|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md)|[Gruppo di misure](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|[CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)|[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) di tipo [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|[Prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md)|[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) di tipo [PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.MeasureGroupCollection> o <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroupCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
