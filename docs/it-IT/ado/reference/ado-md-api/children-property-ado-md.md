---
title: Proprietà di elementi figlio (ADO MD) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member::Children
- Children
helpviewer_keywords:
- Children property [ADO MD]
ms.assetid: 61d36468-1ccd-467a-9cb5-17d0bfacc766
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 630ddeaf83b09dfe502cf07efd7a4185011cff41
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="children-property-ado-md"></a>Proprietà di elementi figlio (ADO MD)
Restituisce un [membri](../../../ado/reference/ado-md-api/members-collection-ado-md.md) raccolta per cui corrente [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) padre nella gerarchia.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **membri** raccolta ed è di sola lettura.  
  
## <a name="remarks"></a>Osservazioni  
 Il **figli** proprietà contiene un **membri** raccolta per cui corrente **membro** è il padre gerarchico. Livello di foglia **membro** oggetti presentano membri figlio **membri** insieme. Questa proprietà è supportata solo su **membro** oggetti appartenenti a un [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md) oggetto. Si verifica un errore quando questa proprietà viene fatto riferimento dal **membro** oggetti appartenenti a un [posizione](../../../ado/reference/ado-md-api/position-object-ado-md.md) oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Member (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà ChildCount (ADO MD)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
