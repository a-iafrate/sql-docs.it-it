---
title: Il tipo di dati ProactiveCachingQueryBinding (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ProactiveCachingQueryBinding Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ProactiveCachingQueryBinding data type
ms.assetid: c1b06e50-9e68-40db-bdab-fc2cb3a8ff64
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fd6779a713d3a2134c4a3b52e06883843d5aa040
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="proactivecachingquerybinding-data-type-assl"></a>Tipo di dati ProactiveCachingQueryBinding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati derivato che rappresenta le informazioni per il [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) elemento relative alle modifiche di origine dati in tabelle e viste identificate tramite l'esecuzione delle query specificate che richiedono la ricompilazione della cache.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCachingQueryBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <RefreshInterval>...</RefreshInterval>  
   <QueryNotification>...</QueryNotification>  
</ProactiveCachingQueryBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[QueryNotification](../../../analysis-services/scripting/objects/querynotification-element-assl.md), [RefreshInterval](../../../analysis-services/scripting/properties/refreshinterval-element-assl.md)|  
|Elementi derivati|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sul **ProactiveCachingBinding** tipo, inclusa una tabella della gerarchia di ereditarietà del **ProactiveCachingBinding** tipi, vedere [dati ProactiveCachingBinding Tipo &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md).  
  
 Per ulteriori informazioni sul **associazione** tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del **associazione** tipo e la gerarchia di ereditarietà dei **associazione**  sui tipi, vedere [associazione tipo di dati &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e associazioni & #40; SSAS multidimensionale & #41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ProactiveCachingQueryBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
