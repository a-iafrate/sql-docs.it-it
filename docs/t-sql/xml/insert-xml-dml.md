---
title: insert (XML DML) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|xml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- XML DML [SQL Server]
- inserting nodes
- insert keyword [XML DML]
- insert XML DML statement
ms.assetid: 0c95c2b3-5cc2-4c38-9e25-86493096c442
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: eb4082d4b14c0287571dd620021444f2ad290aa9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="insert-xml-dml"></a>insert (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Inserisce uno o più nodi identificati da *Expression1* come nodi figlio o nodi di pari livello del nodo identificato da *Expression2*.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
insert   
      Expression1 (  
                 {as first | as last} into | after | before  
                                    Expression2  
                )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Expression1*  
 Identifica uno o più nodi da inserire. Può trattarsi di un'istanza XML costante, un riferimento a un'istanza del tipo di dati XML tipizzata della stessa raccolta di XML Schema in cui viene applicato il metodo modify, un'istanza del tipo di dati XML non tipizzata che usa una funzione **sql:column()**/**sql:variable()** autonoma o un'espressione XQuery. L'espressione può restituire un nodo, anche un nodo di testo, o una sequenza ordinata di nodi, ma non può essere risolta nel nodo radice (/). Se l'espressione restituisce un valore o una sequenza di valori, tali valori vengono inseriti come un nodo di testo nel quale ogni valore della sequenza è separato da uno spazio. Se si specificano più nodi come costante, i nodi vengono racchiusi tra parentesi e sono separati da virgole. Non è possibile inserire sequenze eterogenee, ad esempio una sequenza di elementi, attributi o valori. Se *Expression1* viene risolta in una sequenza vuota, non viene inserito nulla e non vengono restituiti errori.  
  
 into  
 I nodi identificati da *Expression1* vengono inseriti come discendenti diretti (nodi figlio) del nodo identificato da *Expression2*. Se il nodo in *Expression2* ha già uno o più nodi figlio, è necessario usare **as first** o **as last** per specificare la posizione in cui si intende aggiungere il nuovo nodo, ad esempio rispettivamente all'inizio o alla fine dell'elenco di nodi. Le parole chiave **as first** e **as last** vengono ignorate se si inseriscono attributi.  
  
 after  
 I nodi identificati da *Expression1* vengono inseriti come nodi di pari livello immediatamente dopo il nodo identificato da *Expression2*. Non è possibile usare la parola chiave **after** per inserire attributi, ad esempio per inserire un costruttore di attributi o per restituire un attributo da una query XQuery.  
  
 before  
 I nodi identificati da *Expression1* vengono inseriti come nodi di pari livello immediatamente prima del nodo identificato da *Expression2*. Non è possibile usare la parola chiave **before** se vengono inseriti attributi, ad esempio per inserire un costruttore di attributi o per restituire un attributo da una query XQuery.  
  
 *Expression2*  
 Identifica un nodo. I nodi identificati in *Expression1* vengono inseriti in relazione al nodo identificato da *Expression2*. Quest'ultima può essere un'espressione XQuery che restituisce un riferimento a un nodo esistente nel documento a cui viene fatto riferimento. Se vengono restituiti più nodi, l'inserimento avrà esito negativo. Se *Expression2* restituisce una sequenza vuota, non viene inserito nulla e non vengono restituiti errori. Se *Expression2* non è staticamente un singleton, viene restituito un errore statico. *Expression2* non può essere un'istruzione di elaborazione, un commento o un attributo. Si noti che *Expression2* deve fare riferimento a un nodo esistente nel documento e non a un nodo costruito.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-inserting-element-nodes-into-the-document"></a>A. Inserimento di nodi elemento nel documento  
 Nell'esempio seguente viene illustrato l'inserimento di elementi in un documento. Viene prima assegnato un documento XML a una variabile di tipo **xml**. Viene quindi illustrato l'inserimento di nodi elemento nel documento tramite numerose istruzioni XML DML **insert**. Dopo ogni inserimento, l'istruzione SELECT visualizza il risultato.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;         
SET @myDoc = '<Root>         
    <ProductDescription ProductID="1" ProductName="Road Bike">         
        <Features>         
        </Features>         
    </ProductDescription>         
</Root>'  ;       
SELECT @myDoc;     
-- insert first feature child (no need to specify as first or as last)         
SET @myDoc.modify('         
insert <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>   
into (/Root/ProductDescription/Features)[1]') ;  
SELECT @myDoc ;        
-- insert second feature. We want this to be the first in sequence so use 'as first'         
set @myDoc.modify('         
insert <Warranty>1 year parts and labor</Warranty>          
as first         
into (/Root/ProductDescription/Features)[1]         
')  ;       
SELECT @myDoc  ;       
-- insert third feature child. This one is the last child of <Features> so use 'as last'         
SELECT @myDoc         
SET @myDoc.modify('         
insert <Material>Aluminium</Material>          
as last         
into (/Root/ProductDescription/Features)[1]         
')         
SELECT @myDoc ;        
-- Add fourth feature - this time as a sibling (and not a child)         
-- 'after' keyword is used (instead of as first or as last child)         
SELECT @myDoc  ;       
set @myDoc.modify('         
insert <BikeFrame>Strong long lasting</BikeFrame>   
after (/Root/ProductDescription/Features/Material)[1]         
')  ;       
SELECT @myDoc;  
GO  
```  
  
 Si noti che in diverse espressioni di percorso dell'esempio è specificato "[1]" come requisito per la tipizzazione statica, in modo tale da garantire la presenza di un singolo nodo di destinazione.  
  
### <a name="b-inserting-multiple-elements-into-the-document"></a>B. Inserimento di più elementi nel documento  
 Nell'esempio seguente un documento viene prima assegnato a una variabile di tipo **xml**. Una sequenza di due elementi, che rappresenta le funzionalità del prodotto, viene quindi assegnata a una seconda variabile di tipo **xml**. Questa sequenza viene quindi inserita nella prima variabile.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc = N'<Root>             
<ProductDescription ProductID="1" ProductName="Road Bike">             
    <Features> </Features>             
</ProductDescription>             
</Root>';  
DECLARE @newFeatures xml;  
SET @newFeatures = N'<Warranty>1 year parts and labor</Warranty>            
<Maintenance>3 year parts and labor extended maintenance is available</Maintenance>';           
-- insert new features from specified variable            
SET @myDoc.modify('             
insert sql:variable("@newFeatures")             
into (/Root/ProductDescription/Features)[1] ')             
SELECT @myDoc;  
GO  
```  
  
### <a name="c-inserting-attributes-into-a-document"></a>C. Inserimento di attributi in un documento  
 Nell'esempio seguente viene illustrato l'inserimento di attributi in un documento. Viene prima assegnato un documento a una variabile di tipo **xml**. Viene quindi usata una serie di istruzioni XML DML **insert** per inserire gli attributi nel documento. Dopo ogni inserimento di un attributo, l'istruzione SELECT visualizza il risultato.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml ;            
SET @myDoc =   
'<Root>             
    <Location LocationID="10" >             
        <step>Manufacturing step 1 at this work center</step>             
        <step>Manufacturing step 2 at this work center</step>             
    </Location>             
</Root>' ;  
SELECT @myDoc  ;          
-- insert LaborHours attribute             
SET @myDoc.modify('             
insert attribute LaborHours {".5" }             
into (/Root/Location[@LocationID=10])[1] ') ;           
SELECT @myDoc  ;          
-- insert MachineHours attribute but its value is retrived from a sql variable @Hrs             
DECLARE @Hrs float ;            
SET @Hrs =.2   ;          
SET @myDoc.modify('             
insert attribute MachineHours {sql:variable("@Hrs") }             
into   (/Root/Location[@LocationID=10])[1] ');            
SELECT @myDoc;             
-- insert sequence of attribute nodes (note the use of ',' and ()              
-- around the attributes.             
SET @myDoc.modify('             
insert (              
           attribute SetupHours {".5" },             
           attribute SomeOtherAtt {".2"}             
        )             
into (/Root/Location[@LocationID=10])[1] ');             
SELECT @myDoc;  
GO  
```  
  
### <a name="d-inserting-a-comment-node"></a>D. Inserimento di un nodo di commento  
 In questa query viene prima assegnato un documento XML a una variabile di tipo **xml**. Viene quindi utilizzato il linguaggio XML DML per inserire un nodo di commento dopo il primo elemento <`step`>.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;             
SET @myDoc =   
'<Root>             
    <Location LocationID="10" >             
        <step>Manufacturing step 1 at this work center</step>             
        <step>Manufacturing step 2 at this work center</step>             
    </Location>             
</Root>' ;           
SELECT @myDoc;             
SET @myDoc.modify('             
insert <!-- some comment -->             
after (/Root/Location[@LocationID=10]/step[1])[1] ');            
SELECT @myDoc;  
GO  
```  
  
### <a name="e-inserting-a-processing-instruction"></a>E. Inserimento di un'istruzione di elaborazione  
 Nella query seguente, viene prima assegnato un documento XML a una variabile di tipo **xml**. Viene quindi utilizzata la parola chiave XML DML per inserire un'istruzione di elaborazione all'inizio del documento.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>   
    <Location LocationID="10" >   
        <step>Manufacturing step 1 at this work center</step>   
        <step>Manufacturing step 2 at this work center</step>   
    </Location>   
</Root>' ;  
SELECT @myDoc ;  
SET @myDoc.modify('   
insert <?Program = "Instructions.exe" ?>   
before (/Root)[1] ') ;  
SELECT @myDoc ;  
GO  
```  
  
### <a name="f-inserting-data-using-a-cdata-section"></a>F. Inserimento di dati tramite una sezione CDATA  
 Quando si inserisce testo che include caratteri non validi in XML, ad esempio < o >, è possibile utilizzare le sezioni CDATA per inserire i dati come illustrato nella query seguente. Nella query viene specificata una sezione CDATA che tuttavia viene aggiunta come un nodo di testo nel quale i caratteri non validi sono convertiti in entità, ad esempio '<' viene salvato come &lt;.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;             
SET @myDoc =   
'<Root>             
    <ProductDescription ProductID="1" ProductName="Road Bike">             
        <Features> </Features>             
    </ProductDescription>             
</Root>' ;            
SELECT @myDoc ;            
SET @myDoc.modify('             
insert <![CDATA[ <notxml> as text </notxml> or cdata ]]>   
into  (/Root/ProductDescription/Features)[1] ') ;   
SELECT @myDoc ;  
GO  
```  
  
 La query inserisce un nodo di testo nell'elemento <`Features`>:  
  
```  
<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features> <notxml> as text </notxml> or cdata </Features>  
</ProductDescription>  
</Root>       
```  
  
### <a name="g-inserting-text-node"></a>G. Inserimento di un nodo di testo  
 In questa query viene prima assegnato un documento XML a una variabile di tipo **xml**. Viene quindi utilizzato il linguaggio XML DML per inserire un nodo di testo come primo figlio dell'elemento <`Root`>. Per specificare il testo viene utilizzato il costruttore di testo.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc;  
set @myDoc.modify('  
 insert text{"Product Catalog Description"}   
 as first into (/Root)[1]  
');  
SELECT @myDoc;  
```  
  
### <a name="h-inserting-a-new-element-into-an-untyped-xml-column"></a>H. Inserimento di un nuovo elemento in una colonna xml non tipizzata  
 Nell'esempio seguente viene usato il linguaggio XML DML per aggiornare un'istanza XML archiviata in una colonna di tipo **xml**:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE T (i int, x xml);  
go  
INSERT INTO T VALUES(1,'<Root>  
    <ProductDescription ProductID="1" ProductName="Road Bike">  
        <Features>  
            <Warranty>1 year parts and labor</Warranty>  
            <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
        </Features>  
    </ProductDescription>  
</Root>');  
go  
-- insert a new element  
UPDATE T  
SET x.modify('insert <Material>Aluminium</Material> as first  
  into   (/Root/ProductDescription/Features)[1]  
');  
GO  
```  
  
 Anche in questo caso, quando viene inserito il nodo elemento <`Material`>, l'espressione di percorso deve restituire una singola destinazione. Questo requisito viene specificato in modo esplicito tramite l'aggiunta di [1] alla fine dell'espressione.  
  
```  
-- check the update  
SELECT x.query(' //ProductDescription/Features')  
FROM T;  
GO  
```  
  
### <a name="i-inserting-based-on-an-if-condition-statement"></a>I. Inserimento basato su un'istruzione che include la condizione IF  
 Nell'esempio seguente, una condizione IF viene specificata come parte di Expression1 nell'istruzione XML DML **insert**. Se la condizione è True, all'elemento <`WorkCenter`> viene aggiunto un attributo.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>  
    <Location LocationID="10" LaborHours="1.2" >  
        <step>Manufacturing step 1 at this work center</step>  
    <step>Manufacturing step 2 at this work center</step>  
    </Location>  
</Root>';  
SELECT @myDoc  
SET @myDoc.modify('  
insert  
if (/Root/Location[@LocationID=10])  
then attribute MachineHours {".5"}  
else ()  
    as first into   (/Root/Location[@LocationID=10])[1] ');  
SELECT @myDoc;  
GO  
```  
  
 L'esempio seguente è simile, eccetto che per il fatto che l'istruzione XML DML **insert** inserisce un elemento nel documento se la condizione è True, ovvero se l'elemento <`WorkCenter`> include un numero inferiore o uguale a due di elementi figlio <`step`>.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>  
    <Location LocationID="10" LaborHours="1.2" >  
        <step>Manufacturing step 1 at this work center</step>  
        <step>Manufacturing step 2 at this work center</step>  
    </Location>  
</Root>';  
SELECT @myDoc;  
SET @myDoc.modify('  
insert  
if (count(/Root/Location/step) <= 2)  
then element step { "This is a new step" }  
else ()  
    as last into   (/Root/Location[@LocationID=10])[1] ');  
SELECT @myDoc;  
GO  
```  
  
 Risultato:  
  
```  
<Root>  
 <WorkCenter WorkCenterID="10" LaborHours="1.2">  
  <step>Manufacturing step 1 at this work center</step>  
  <step>Manufacturing step 2 at this work center</step>  
  <step>This is a new step</step>  
 </WorkCenter>  
```  
  
### <a name="j-inserting-nodes-in-a-typed-xml-column"></a>J. Inserimento di nodi in una colonna xml tipizzata  
 In questo esempio vengono inseriti un elemento e un attributo in un codice XML delle istruzioni di produzione archiviato in una colonna **xml** tipizzata.  
  
 Viene prima creata una tabella (T) con una colonna **xml** tipizzata nel database AdventureWorks. Un'istanza del codice XML delle istruzioni di produzione viene quindi copiata dalla colonna Instructions della tabella ProductModel nella tabella T. Gli inserimenti vengono quindi applicati al codice XML nella tabella T.  
  
```  
USE AdventureWorks;  
GO            
DROP TABLE T;  
GO             
CREATE TABLE T(ProductModelID int primary key,    
Instructions xml (Production.ManuInstructionsSchemaCollection));  
GO  
INSERT T              
    SELECT ProductModelID, Instructions             
    FROM Production.ProductModel             
    WHERE ProductModelID=7;  
GO             
SELECT Instructions             
FROM T;  
-- now insertion begins             
--1) insert a new manu. Location. The <Root> specified as              
-- expression 2 in the insert() must be singleton.      
UPDATE T   
set Instructions.modify('   
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
insert <MI:Location LocationID="1000" >   
           <MI:step>New instructions go here</MI:step>   
         </MI:Location>   
as first   
into   (/MI:root)[1]   
') ;  
  
SELECT Instructions             
FROM T ;  
-- 2) insert attributes in the new <Location>             
UPDATE T             
SET Instructions.modify('             
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";             
insert attribute LaborHours { "1000" }             
into (/MI:root/MI:Location[@LocationID=1000])[1] ');   
GO             
SELECT Instructions             
FROM T ;  
GO             
--cleanup             
DROP TABLE T ;  
GO             
```  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio XML di manipolazione dei dati &#40;XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
