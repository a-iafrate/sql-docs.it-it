---
title: Append (metodo) (ADOX colonne) | Documenti Microsoft
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
- Columns::raw_Append
- Columns::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e53965f9a8c5602459a08f5c47e5719741bb648
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="append-method-adox-columns"></a>Append (metodo) (ADOX colonne)
Aggiunge un nuovo [colonna](../../../ado/reference/adox-api/column-object-adox.md) dell'oggetto per il [colonne](../../../ado/reference/adox-api/columns-collection-adox.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>Parametri  
 *Colonna*  
 Il **colonna** oggetto da accodare o il nome della colonna per creare e aggiungere.  
  
 *Tipo*  
 Facoltativa. Oggetto **lungo** valore che specifica il tipo di dati della colonna. Il *tipo* parametro corrisponde al [tipo](../../../ado/reference/adox-api/type-property-column-adox.md) proprietà di un **colonna** oggetto.  
  
 *DefinedSize*  
 Facoltativa. Oggetto **lungo** valore che specifica la dimensione della colonna. Il *DefinedSize* parametro corrisponde al [DefinedSize](../../../ado/reference/adox-api/definedsize-property-adox.md) proprietà di un **colonna** oggetto.  
  
> [!NOTE]
>  Si verifica un errore quando si accoda un **colonna** per il **colonne** raccolta di un [indice](../../../ado/reference/adox-api/index-object-adox.md) se il **colonna** non esiste un [Tabella](../../../ado/reference/adox-api/table-object-adox.md) già aggiunto al [tabelle](../../../ado/reference/adox-api/tables-collection-adox.md) insieme.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta di oggetti Column (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Le colonne e tabelle aggiungere metodi, esempio di proprietà Name (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Chiavi Aggiungi metodo, tipo di chiave, RelatedColumn, RelatedTable e UpdateRule proprietà esempio (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Esempio di proprietà ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Append (metodo) (ADOX gruppi)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (metodo) (ADOX indici)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (metodo) (ADOX chiavi)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (metodo) (ADOX procedure)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (metodo) (ADOX tabelle)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (metodo) (ADOX utenti)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Metodo Append (oggetti View ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)
