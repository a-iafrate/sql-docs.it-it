---
title: Delete (metodo) (insiemi ADOX) | Documenti Microsoft
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
- Views::Delete
- Groups::Delete
- Indexes::raw_Delete
- Columns::raw_Delete
- Tables::Delete
- Keys::Delete
- Users::Delete
- Users::raw_Delete
- Keys::raw_Delete
- Procedures::raw_Delete
- Views::raw_Delete
- Indexes::Delete
- Procedures::Delete
- Groups::raw_Delete
- Tables::raw_Delete
- Columns::Delete
helpviewer_keywords:
- delete method [ADOX]
ms.assetid: e6b6e3a4-8952-4d79-81f4-51019c338374
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0422a3c6edec88649e837ce8090986d963752e31
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="delete-method-adox-collections"></a>Delete (metodo) (ADOX raccolte)
Rimuove un oggetto da una raccolta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Parametri  
 *Nome*  
 Oggetto **Variant** che specifica il nome o la posizione ordinale (indice) dell'oggetto da eliminare.  
  
## <a name="remarks"></a>Osservazioni  
 Si verifica un errore se il *nome* non esiste nella raccolta.  
  
 Per [tabelle](../../../ado/reference/adox-api/tables-collection-adox.md) e [utenti](../../../ado/reference/adox-api/users-collection-adox.md) raccolte, si verifica un errore se il provider non supporta l'eliminazione di tabelle o gli utenti, rispettivamente. Per [procedure](../../../ado/reference/adox-api/procedures-collection-adox.md) e [viste](../../../ado/reference/adox-api/views-collection-adox.md) raccolte, **eliminare** avrà esito negativo se il provider non supporta i comandi di persistenza.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Raccolta di oggetti Column (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Raccolta di oggetti Group (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Raccolta di oggetti Index (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Raccolta di oggetti Key (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Raccolta di oggetti Procedure (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|[Raccolta di oggetti Table (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[Raccolta di oggetti User (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[Raccolta di oggetti View (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure di esempio del metodo Delete (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Esempio di metodo Delete oggetti View (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
