---
title: Oggetto CubeDef (ADO MD) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CubeDef
helpviewer_keywords:
- CubeDef object [ADO MD]
ms.assetid: feb2581c-fc41-471c-bb69-29f8a55fda70
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31e2bf587c19ab8088b0ab702be60fde54247aec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="cubedef-object-ado-md"></a>Oggetto CubeDef (ADO MD)
Rappresenta un cubo da uno schema multidimensionale, contenente un set di dimensioni correlate.  
  
## <a name="remarks"></a>Osservazioni  
 Raccolte e le proprietà di un **CubeDef** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Identificare un **CubeDef** con il [nome](../../../ado/reference/ado-md-api/name-property-ado-md.md) proprietà.  
  
-   Restituisce una stringa che descrive il cubo con il [descrizione](../../../ado/reference/ado-md-api/description-property-ado-md.md) proprietà.  
  
-   Restituire le dimensioni che costituiscono il cubo con il [dimensioni](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md) insieme.  
  
-   Ottenere informazioni aggiuntive sul **CubeDef** con ADO standard [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
 Il **proprietà** insieme contiene le proprietà specifiche del provider. Nella tabella seguente sono elencate le proprietà che potrebbero essere disponibili. L'elenco di proprietà effettivo può variare in base all'implementazione del provider. Vedere la documentazione del provider per un elenco completo delle proprietà disponibili.  
  
|Nome|Description|  
|----------|-----------------|  
|CatalogName|Il nome del catalogo a cui appartiene il cubo.|  
|CreatedOn|Data e ora di creazione del cubo.|  
|CubeGUID|Cubo GUID.|  
|CubeName|Nome del cubo.|  
|CubeType|Tipo del cubo.|  
|DataUpdatedBy|ID utente della persona che esegue l'ultimo aggiornamento dei dati.|  
|Description|Una descrizione significativa del cubo.|  
|LastSchemaUpdate|Data e ora dell'ultimo aggiornamento dello schema.|  
|SchemaName|Il nome dello schema a cui appartiene il cubo.|  
|SchemaUpdatedBy|ID utente della persona che esegue l'ultimo aggiornamento dello schema.|  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Oggetto del catalogo (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [Insieme CubeDefs (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [Raccolta di dimensioni (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
