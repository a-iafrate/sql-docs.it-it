---
title: Proprietà PageCount (ADO) | Documenti Microsoft
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
- Recordset15::PageCount
helpviewer_keywords:
- PageCount property [ADO]
ms.assetid: b601b56c-0ac4-44ee-bc91-c3d2d104f00a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31eecabefdc56da6f4a252e974cc8ff97f9190c8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="pagecount-property-ado"></a>Proprietà PageCount (ADO)
Indica il numero di pagine di dati di [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto contiene.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **lungo** valore che indica il numero di pagine di **Recordset**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **PageCount** proprietà per determinare il numero di pagine di dati di **Recordset** oggetto. *Pagine* sono gruppi di record la cui dimensione è uguale al [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) impostazione della proprietà. Anche se l'ultima pagina incompleta perché sono presenti record minore rispetto di **PageSize** valore, viene conteggiata come una pagina aggiuntiva nel **PageCount** valore. Se il **Recordset** oggetto non supporta questa proprietà, il valore sarà -1 per indicare che il **PageCount** non è possibile determinare.  
  
 Vedere il **PageSize** e [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) le proprietà di altre funzionalità della pagina su.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà PageSize (VB), PageCount e AbsolutePage](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [Esempio di proprietà PageSize (VC + +), AbsolutePage e PageCount](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Proprietà AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [Proprietà PageSize (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [Proprietà RecordCount (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
