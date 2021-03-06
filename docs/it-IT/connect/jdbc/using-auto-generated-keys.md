---
title: Utilizzo automatico delle chiavi generate | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 55a062c7-45ce-40e3-9a6f-4a0f4da4e2a6
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e59b212e60d9bdc177ea310aa8a04978f6c72df
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-auto-generated-keys"></a>Utilizzo delle chiavi generate automaticamente
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta l'API di JDBC 3.0 facoltative per recuperare automaticamente generati degli identificatori di riga. Il valore principale di questa funzionalità è di consentire la disponibilità dei valori IDENTITY all'applicazione con la quale si sta aggiornando una tabella di database senza richiedere una query e un secondo round trip al server.  
  
 Poiché [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non supporta pseudocolonne per gli identificatori, funzionano solo gli aggiornamenti che sono necessario utilizzare la funzionalità delle chiavi generate automaticamente in una tabella che contiene una colonna IDENTITY. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] consente solo una singola colonna IDENTITY per tabella. Il set di risultati restituito da [getGeneratedKeys](../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe avrà una sola colonna, con il nome della colonna restituito di GENERATED_KEYS. Se le chiavi generate vengono richieste in una tabella che non contiene la colonna IDENTITY, il driver JDBC restituirà un set di risultati con valore Null.  
  
 Ad esempio, creare la tabella seguente nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio:  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
```  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, viene costruita un'istruzione SQL che consentirà di aggiungere dati alla tabella, quindi viene eseguita l'istruzione e viene visualizzato il valore della colonna IDENTITY.  
  
 [!code[JDBC#UsingAutoGeneratedKeys1](../../connect/jdbc/codesnippet/Java/using-auto-generated-keys_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle istruzioni con il driver JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
