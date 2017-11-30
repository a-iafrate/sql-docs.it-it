---
title: Attributi ed elementi XSD di Mapping esplicito a tabelle e colonne | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- sql:field
- row mapping [SQLXML]
- attribute mapping [SQLXML], explicit mapping
- field annotation
- XSD schemas [SQLXML], mapping attributes and elements
- names [SQLXML]
- relation annotation
- table/view mapping [SQLXML], explicit mapping
- sql:relation
- mapping schema [SQLXML], explicit mapping
- annotated XSD schemas, mapping attributes and elements
- column mapping [SQLXML]
- element mapping [SQLXML], explicit mapping
- table mapping [SQLXML], explicit mapping
- element/attribute mapping [SQLXML]
ms.assetid: 7a5ebeb6-7322-4141-a307-ebcf95976146
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5a83de0653a25fa2bf055c003a13600a67e37bb9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns"></a>Attributi ed elementi XSD di Mapping esplicito a tabelle e colonne
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Quando si utilizza uno schema XSD per fornire una vista XML del database relazionale, gli elementi e attributi dello schema devono essere mappati a tabelle e colonne del database. Le righe della tabella/vista di database vengono mappate agli elementi del documento XML. I valori di colonna del database vengono mappati agli attributi o agli elementi.  
  
 Quando vengono specificate query XPath nello schema XSD con annotazioni, i dati relativi agli elementi e agli attributi dello schema vengono recuperati dalle tabelle e dalle colonne alle quali vengono mappati. Per ottenere un solo valore dal database, per il mapping specificato nello schema XSD devono essere indicati sia la relazione che il campo. Se il nome di un elemento/attributo non è lo stesso nome come nome tabella/vista o una colonna a cui viene eseguito il mapping, il **SQL: relation** e **SQL: field** le annotazioni vengono utilizzate per specificare il mapping tra un elemento o attributo in un documento XML e la tabella (vista) o la colonna in un database.  
  
## <a name="sql-relation"></a>sql-relation  
 Il **SQL: relation** annotazione viene aggiunta per eseguire il mapping di un nodo XML nello schema XSD a una tabella di database. Il nome di una tabella (vista) viene specificato come valore della **SQL: relation** annotazione.  
  
 Quando **SQL: relation** specificato in un elemento, l'ambito di questa annotazione si applica a tutti gli attributi e gli elementi figlio che sono descritti nella definizione del tipo complesso di tale elemento, quindi fornire un collegamento in scrittura annotazioni.  
  
 Il **SQL: relation** annotazione è utile anche quando gli identificatori che sono validi in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non sono validi in XML. "Order Details", ad esempio, è un nome di tabella valido in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ma non in XML. In questi casi, il **SQL: relation** annotazione può essere utilizzata per specificare il mapping, ad esempio:  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a>sql-field  
 Il **campo sql** annotazione esegue il mapping di un elemento o attributo a una colonna di database. Il **SQL: field** annotazione viene aggiunta a un nodo XML nello schema di mapping a una colonna di database. Non è possibile specificare **SQL: field** su un elemento di contenuto vuoto.  
  
## <a name="examples"></a>Esempi  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare alcuni requisiti. Per ulteriori informazioni, vedere [requisiti per esecuzione esempi SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a>A. Specifica delle annotazioni sql:relation e sql:field  
 In questo esempio, lo schema XSD è costituito un  **\<contatto >** elemento di tipo complesso con  **\<FName >** e  **\<LName >** gli elementi figlio e **ContactID** attributo.  
  
 Il **SQL: relation** annotazione mappe di  **\<contatto >** elemento alla tabella Person. Contact nel database AdventureWorks. Il **SQL: field** annotazione mappe di  **\<FName >** elemento alla colonna FirstName e  **\<LName >** elemento LastName colonna.  
  
 Viene specificata alcuna annotazione per la **ContactID** attributo. Il risultato ottenuto è un mapping predefinito dell'attributo alla colonna con lo stesso nome.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome MySchema-annotated.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file con il nome MySchema-annotatedT.xml nella stessa directory in cui è stato salvato il file MySchema-annotated.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="MySchema-annotated.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso della directory specificato per lo schema di mapping MySchema-annotated.xml è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema-annotated.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Di seguito è riportato il set di risultati parziale:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
 <Contact ContactID="1">   
    <FName>Gustavo</FName>   
    <LName>Achong</LName>   
 </Contact>   
  .....  
</ROOT>  
```  
  
  