---
title: Altre informazioni sull'oggetto Recordset persistenza | Documenti Microsoft
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
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: a9b287f5-04b0-4514-8143-f67879ca9842
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a5c0d8bda0d3d881dfcb1dfd99706b28e5fb733
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="more-about-recordset-persistence"></a>Ulteriori informazioni su persistenza Recordset
L'oggetto Recordset ADO supporta l'archiviazione del contenuto di un **Recordset** oggetto in un file utilizzando il relativo [salvare](../../../ado/reference/ado-api/save-method.md) metodo. Il file salvato in modo permanente può esistere in un locale di unità, server, o come un URL per un sito Web del sito. In un secondo momento, il file può essere ripristinato con il [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo del **Recordset** oggetto o [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) metodo il [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
 Inoltre, il [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) metodo converte un **Recordset** oggetto a un form in cui le colonne e righe sono delimitate con caratteri specificati dall'utente.  
  
 Per rendere persistente un **Recordset**, innanzitutto convertirlo in un modulo che può essere archiviato in un file. **Recordset** oggetti possono essere archiviati in formato proprietario di avanzata dei dati viene (ADTG) o formato Extensible Markup Language (XML) open. Vengono illustrati esempi ADTG nella sezione successiva. Per ulteriori informazioni sul formato XML, vedere [salvataggio di record in formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 Salvare le modifiche in sospeso nel file persistente. Questa operazione consente di eseguire una query che restituisce un **Recordset** oggetto, le modifiche di **Recordset**, Salva le modifiche in sospeso, ripristina il **Recordset**e quindi Aggiorna l'origine dati con salvato le modifiche in sospeso.  
  
 Per informazioni sull'archiviazione in modo permanente **flusso** degli oggetti, vedere [flussi e persistenza](../../../ado/guide/data/streams-and-persistence.md).  
  
 Per un esempio di **Recordset** persistenza, vedere lo Scenario di persistenza XML Recordset.  
  
## <a name="example"></a>Esempio  
  
### <a name="save-a-recordset"></a>Salvare un oggetto Recordset:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Save "c:\yourFile.adtg", adPersistADTG  
```  
  
### <a name="open-a-persisted-file-with-recordsetopen"></a>Aprire un file persistente con Open:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg", "Provider=MSPersist",,,adCmdFile  
```  
  
 Facoltativamente, se il **Recordset** does non dispone di una connessione attiva, è possibile accettare tutti i valori predefiniti e di codice seguente:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg"  
```  
  
### <a name="open-a-persisted-file-with-connectionexecute"></a>Aprire un file persistente con Connection:  
  
```  
Dim conn as New ADODB.Connection  
Dim rs as ADODB.Recordset  
conn.Open "Provider=MSPersist"  
Set rs = conn.execute("c:\yourFile.adtg")  
```  
  
### <a name="open-a-persisted-file-with-rdsdatacontrol"></a>Aprire un file persistente con RDS. DataControl:  
 In questo caso, il **Server** non è impostata.  
  
```  
Dim dc as New RDS.DataControl  
dc.Connection = "Provider=MSPersist"  
dc.SQL = "c:\yourFile.adtg"  
dc.Refresh  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo GetString (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)   
 [Provider di persistenza Microsoft OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Flussi e persistenza](../../../ado/guide/data/streams-and-persistence.md)
