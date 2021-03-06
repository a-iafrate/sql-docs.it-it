---
title: OPENQUERY (DMX) | Documenti Microsoft
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
- OPENQUERY
dev_langs:
- DMX
helpviewer_keywords:
- OPENQUERY statement
ms.assetid: fe57f3a3-a8e6-402c-995e-bd2fe28a7a7c
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: ed189fdef9d1d2d96d8100276d3a97779a08ac7b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ltsource-data-querygt---openquery"></a>&lt;query di dati di origine&gt; -OPENQUERY
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Sostituisce la query sui dati dell'origine con una query su un'origine dei dati esistente. Le istruzioni INSERT, SELECT FROM PREDICTION JOIN e SELECT FROM NATURAL PREDICTION JOIN supportano **OPENQUERY**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
OPENQUERY(<named datasource>, <query syntax>)  
```  
  
## <a name="arguments"></a>Argomenti  
 *origine dati denominata*  
 Un'origine dati esistente nel [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.  
  
 *Sintassi di query*  
 Sintassi di una query che restituisce un set di righe.  
  
## <a name="remarks"></a>Osservazioni  
 **OPENQUERY** fornisce un modo più sicuro per accedere ai dati esterni supportando autorizzazioni dell'origine dati. Poiché la stringa di connessione viene archiviata nell'origine dati, gli amministratori possono utilizzare le proprietà dell'origine dati per gestire l'accesso ai dati. Per ulteriori informazioni sulle origini dati, vedere [origini dati supportate &#40;SSAS - multidimensionale&#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md).  
  
 È possibile ottenere un elenco delle origini dati che sono disponibili in un server eseguendo una query di **MDSCHEMA_INPUT_DATASOURCES** set di righe dello schema. Per ulteriori informazioni sull'utilizzo **MDSCHEMA_INPUT_DATASOURCES**, vedere [set di righe MDSCHEMA_INPUT_DATASOURCES](../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md).  
  
 È inoltre possibile restituire un elenco di origini dati del database di Analysis Services corrente mediante la seguente query DMX:  
  
 `SELECT * FROM $system.MDSCHEMA_INPUT_DATASOURCES`  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa l'origine dati myDS sono già definita nel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database per creare una connessione al [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database e query di **vTargetMail** visualizzazione.  
  
```  
OPENQUERY (MyDS,'SELECT TOP 1000 * FROM vTargetMail')  
```  
  
## <a name="see-also"></a>Vedere anche  
 [&#60;query di origine dati&#62;](../dmx/source-data-query.md)   
 [Estensioni Data Mining &#40;DMX&#41; istruzioni Data Manipulation](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions & #40; DMX & #41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
