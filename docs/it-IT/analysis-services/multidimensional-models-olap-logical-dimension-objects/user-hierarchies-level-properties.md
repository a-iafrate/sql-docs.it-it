---
title: Proprietà - gerarchie utente di livello | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 903ece979d44dedd6353919af28bdb6c82986e16
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="user-hierarchies---level-properties"></a>Gerarchie utente, le proprietà del livello
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Nella tabella seguente vengono elencate e descritte le proprietà di un livello in una gerarchia definita dall'utente.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|Description|Contiene la descrizione del livello.|  
|HideMemberIf|Indica se e quando un membro di un livello deve essere nascosto per le applicazioni client. I possibili valori della proprietà sono i seguenti:<br /><br /> Never<br /> I membri non vengono mai nascosti. Si tratta del valore predefinito.<br /><br /> OnlyChildWithNoName<br /> Un membro viene nascosto quando il membro è l'unico figlio del relativo padre e il nome del membro è vuoto.<br /><br /> OnlyChildWithParentName<br /> Un membro viene nascosto quando il membro è l'unico figlio del relativo padre e il nome del membro è uguale a quello del relativo padre.<br /><br /> NoName<br /> Un membro viene nascosto quando il nome del membro è vuoto.<br /><br /> ParentName<br /> Un membro viene nascosto quando il nome del membro è uguale a quello del relativo padre.|  
|ID|Contiene l'identificatore univoco (ID) del livello.|  
|Nome|Contiene il nome descrittivo del livello. Per impostazione predefinita, il nome di un livello è uguale al nome dell'attributo di origine.|  
|SourceAttribute|Contiene il nome dell'attributo di origine sul quale si basa il livello.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà della gerarchia utente](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
