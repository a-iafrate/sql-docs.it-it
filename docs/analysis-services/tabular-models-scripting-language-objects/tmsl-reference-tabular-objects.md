---
title: Le definizioni degli oggetti nella tabella del modello Scripting Language (TMSL) | Documenti Microsoft
ms.custom: ''
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 486f0507-cec6-4672-b947-0bb61d1cbc46
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e7433ce926f37bac67fe8ba50e14c4e7324bb218
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="tmsl-reference---tabular-objects"></a>Riferimento TMSL - oggetti tabulari
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Le applicazioni di creare, utilizzare o amministrare i database tabulari o che si connettono a un'istanza di SQL Server 2016 Analysis Services in modalità tabulare, è possibile utilizzare il protocollo Tabular Model Scripting Language (TMSL) per comandi e le rappresentazioni di oggetti in formato JSON.  
  
 Questo articolo sono descritti i principali oggetti dello schema TMSL utilizzati negli script generati da SQL Server Management Studio, SQL Server Data Tools (SSDT) e PowerShell per AMO.  
  
 Le definizioni degli oggetti in JSON e utilizzati in comandi TMSL come Create, Alter ed eliminare. Vedere [comandi Tabular Model Scripting Language &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) per un elenco dei comandi.  
  
## <a name="main-objects"></a>Oggetti principali  
 Nella tabella seguente è riportato l'elenco degli oggetti più comunemente usati nello script TMSL.  
  
|||  
|-|-|  
|[Oggetto di database &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|Definisce un database tabulare con livello di compatibilità 1200 o superiore, in base a un modello dello stesso livello.|  
|[Oggetto del modello &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|Definisce un modello tabulare a livello di compatibilità 1200 o superiore.|  
|[Oggetto di origini dati &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|Definisce una connessione a un'origine dati utilizzata durante l'importazione per caricare il modello o per pass-through query quando il modello è in modalità DirectQuery.|  
|[Oggetto tabelle &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|Specifica le tabelle del modello.|  
|[Oggetto di partizioni &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|Definisce l'archiviazione dei set di righe di tabella, incluse le tabelle calcolate.|  
|[Oggetto le relazioni &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|Definisce le relazioni tra tabelle.|  
|[Oggetto di ruoli &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|Definisce le autorizzazioni, appartenenza e i filtri di sicurezza che controllano l'accesso ai dati e operazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento al linguaggio di scripting per modelli tabulari &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
