---
title: 'Passaggio 3: Modello di prova di connessione a SQL tramite pyodbc | Documenti Microsoft'
ms.custom: 
ms.date: 08/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bfd6e52-817d-4f0a-a33d-11466e3f0484
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b71b6e4f40e4f1910d825071b8a0d86db4987624
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-pyodbc"></a>Passaggio 3: Modello di connessione a SQL tramite pyodbc prova

In questo esempio deve essere considerato un modello solo di prova.  Il codice di esempio è semplificato per maggiore chiarezza e non rappresenta necessariamente le procedure consigliate da Microsoft.  

**Eseguire script di esempio riportato di seguito** creare un file denominato test.py e aggiungere ogni frammento di codice mentre Prosegui. 

```
> python test.py
```
  
## <a name="step-1--connect"></a>Passaggio 1: connettersi  
  
```python

import pyodbc 
server = 'tcp:myserver.database.windows.net' 
database = 'mydb' 
username = 'myusername' 
password = 'mypassword' 
cnxn = pyodbc.connect('DRIVER={ODBC Driver 13 for SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
cursor = cnxn.cursor()

```  
  
  
## <a name="step-2--execute-query"></a>Passaggio 2: Esecuzione di query  
  
Il cursor.executefunction consente di recuperare un set di risultati da una query sul Database SQL. Questa funzione è essenzialmente accetta tutte le query e restituisce un set di risultati che è possibile eseguire un'iterazione con l'utilizzo di cursor.fetchone()
  
  
```python
#Sample select query
cursor.execute("SELECT @@version;") 
row = cursor.fetchone() 
while row: 
    print row[0] 
    row = cursor.fetchone()

```  
  
## <a name="step-3--insert-a-row"></a>Passaggio 3: Inserire una riga  
  
In questo esempio verrà visualizzato come eseguire un [inserire](https://msdn.microsoft.com/library/ms174335.aspx) istruzione in modo sicuro, passare parametri che la protezione dell'applicazione da [attacchi SQL injection](https://technet.microsoft.com/library/ms161953(v=sql.105).aspx) vulnerabilità e recuperare il generatoautomaticamente[Chiave primaria](https://msdn.microsoft.com/library/ms179610.aspx) valore.    
  
  
```python

#Sample insert query
cursor.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New 20', 'SQLEXPRESS New 20', 0, 0, CURRENT_TIMESTAMP )") 
row = cursor.fetchone()

while row: 
    print 'Inserted Product key is ' + str(row[0]) 
    row = cursor.fetchone()
```  
  `      
  ## <a name="next-steps"></a>Passaggi successivi  
  
Per ulteriori informazioni, vedere il [Centro per sviluppatori Python](https://azure.microsoft.com/en-us/develop/python/).