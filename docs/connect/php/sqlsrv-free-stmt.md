---
title: sqlsrv_free_stmt | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_free_stmt
apitype: NA
helpviewer_keywords:
- sqlsrv_free_stmt
- API Reference, sqlsrv_free_stmt
ms.assetid: 3c71f432-36ad-41e1-8ac7-587c82539448
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8a57257fcaddfc1b5e520c99de0c217a7a57a6a1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvfreestmt"></a>sqlsrv_free_stmt
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Libera tutte le risorse associate all'istruzione specificata. L'istruzione non potrà essere usata nuovamente dopo la chiamata a questa funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_free_stmt( resource $stmt)  
```  
  
#### <a name="parameters"></a>Parametri  
*$stmt*: istruzione da chiudere.  
  
## <a name="return-value"></a>Valore restituito  
Valore booleano **true** a meno che la funzione non venga chiamata con un parametro non valido. Se la funzione viene chiamata con un parametro non valido, viene restituito **false** .  
  
> [!NOTE]  
> **Null** è un parametro valido per questa funzione. Permette alla funzione di essere chiamata più volte in uno script. Ad esempio, se si rilascia un'istruzione in una condizione di errore e si rilascia nuovamente alla fine dello script, la seconda chiamata a **sqlsrv_free_stmt** restituirà **true** perché la prima chiamata a **sqlsrv _ free_stmt** (nella condizione di errore) imposta la risorsa di istruzione su **null**.  
  
## <a name="example"></a>Esempio  
Nell'esempio seguente viene creata una risorsa di istruzione, viene eseguita una query semplice e viene eseguita una chiamata a **sqlsrv_free_stmt** per rilasciare tutte le risorse associate all'istruzione. Nell'esempio si presuppone che SQL Server e il [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) database vengono installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
$stmt = sqlsrv_query( $conn, "SELECT * FROM Person.Contact");  
if( $stmt )  
{  
     echo "Statement executed.\n";  
}  
else  
{  
     echo "Query could not be executed.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*-------------------------------  
     Process query results here.  
-------------------------------*/  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  

[sqlsrv_cancel](../../connect/php/sqlsrv-cancel.md)  
  
