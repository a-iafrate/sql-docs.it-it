---
title: Elemento Exception (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Exception Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Exception
- urn:schemas-microsoft-com:xml-analysis#Exception
- microsoft.xml.analysis.exception
helpviewer_keywords:
- Exception element
ms.assetid: 0be4cc2f-c03e-490a-a6f7-8b1ede5d09ba
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0c83900d85d698c5f9b2c0bdca2c197ab4ce05b1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="exception-element-xmla"></a>Elemento Exception (XMLA)
  Indica che un'eccezione ha restituita un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) o [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo.  
  
 **Namespace**`http://schemas.microsoft.com/analysisservices/2003/exception`  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
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
|Elementi padre|[radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Se si verifica un errore durante l'esecuzione di un **Discover** chiamata al metodo o un singolo comando XMLA in un **Execute** chiamata al metodo che impedisce il completamento, il metodo o un comando di **radice** elemento per tale metodo o il comando contiene un **eccezione** elemento e un **messaggi** elemento. Il **eccezione** elemento indica che si è verificato un errore che ha impedito il metodo o il comando completato correttamente l'esecuzione e **messaggi** elemento contiene l'elenco di messaggi di errore o avviso correlato all'errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Messages &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  