---
title: Creare viste su colonne XML | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b0225ca7a583e30cb0e237a90ca69314d5f841ae
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="create-views-over-xml-columns"></a>Creazione di viste
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Le colonne di tipo **xml** possono essere utilizzate per la creazione di viste. Nell'esempio seguente viene creata una vista nella quale il valore di una colonna di tipo `xml` viene recuperato utilizzando il metodo **value()** del tipo di dati **xml** .  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 Eseguire la query seguente sulla vista:  
  
```  
SELECT *   
FROM   MyView  
```  
  
 Risultato:  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 Notare i punti seguenti circa l'utilizzo del tipo di dati **xml** per creare viste:  
  
-   Il tipo di dati xml può essere creato in una vista materializzata. La vista materializzata non può essere basata su un metodo con tipo di dati XML, ma è possibile eseguirne il cast su una raccolta di XML Schema diversa dalla colonna di tipo xml nella tabella di base.  
  
-   Il tipo di dati **xml** non può essere utilizzato nelle viste partizionate distribuite.  
  
-   I predicati SQL in esecuzione sulla vista non saranno inseriti in XQuery per la definizione della vista.  
  
-   I metodi con tipo di dati XML in una vista non sono aggiornabili.  
  
  
