---
title: Provider obbligatori per il Data Shaping | Documenti Microsoft
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
helpviewer_keywords:
- providers [ADO], data shaping
- data shaping [ADO], providers required
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 049f635c9566a72bb84a7cef18aa62b80746c21b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="required-providers-for-data-shaping"></a>Provider desiderati per il Data Shaping
Il data shaping in genere richiede due provider. Il provider del servizio, [Data shaping per OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), fornisce i dati di data shaping, funzionalità e un provider di dati, ad esempio il Provider OLE DB per SQL Server, che include le righe di dati per popolare il data shaping [Recordset ](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Il nome del provider di servizi (MSDataShape) può essere specificato come valore del [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto [Provider](../../../ado/reference/ado-api/provider-property-ado.md) proprietà o la parola chiave stringa di connessione "Provider = MSDataShape;".  
  
 Il nome del provider di dati può essere specificato come valore della **Provider di dati** proprietà dinamiche, che viene aggiunto al **connessione** oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta da il Data shaping per OLE DB o parola chiave della stringa di connessione "**Provider di dati = * * * provider*".  
  
 Nessun provider di dati è necessario se il **Recordset** non è popolata (ad esempio, come un creato **Recordset** in cui le colonne vengono create con la parola chiave NEW). In tal caso, specificare "**Provider di dati =** none;".  
  
## <a name="example"></a>Esempio  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Data Shaping di esempio](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)
