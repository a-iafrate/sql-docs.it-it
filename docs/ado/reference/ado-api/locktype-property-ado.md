---
title: Proprietà LockType (ADO) | Documenti Microsoft
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
- Recordset15::LockType
helpviewer_keywords:
- LockType property [ADO]
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35d413ea9bfaded1494270d837f433fc9546e0b4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="locktype-property-ado"></a>Proprietà LockType (ADO)
Indica il tipo di blocco applicato ai record durante la modifica.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) valore. Il valore predefinito è **adLockReadOnly**.  
  
## <a name="remarks"></a>Osservazioni  
 Impostare il **LockType** proprietà prima di aprire un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) per specificare il tipo di blocco che il provider deve utilizzare durante l'apertura del file. Leggere la proprietà per restituire il tipo di blocco in uso su un oggetto aperto **Recordset** oggetto.  
  
 I provider potrebbero non supportare tutti i tipi di blocco. Se un provider non supporta la richiesta **LockType** impostazione sostituirà un altro tipo di blocco. Per determinare la funzionalità di blocco disponibile in un **Recordset** oggetto, usare il [supporta](../../../ado/reference/ado-api/supports-method.md) metodo con **valori adUpdate** e **adUpdateBatch**.  
  
 Il **adLockPessimistic** impostazione non è supportata se il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) è impostata su **adUseClient**. Se è impostato un valore non supportato, verrà restituito alcun errore; è supportato il più vicino **LockType** verrà utilizzato.  
  
 Il **LockType** proprietà è di lettura/scrittura quando il **Recordset** è chiuso e di sola lettura quando è aperto.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** quando viene utilizzata su un lato client **Recordset** oggetto, il **LockType** proprietà può essere impostata solo su **adLockBatchOptimistic**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [CursorType, LockType ed esempio di proprietà EditMode (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType ed esempio di proprietà EditMode (VC + +)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Metodo CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Metodo UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
