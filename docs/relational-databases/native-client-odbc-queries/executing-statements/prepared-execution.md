---
title: Esecuzione preparata | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- deferred statement preparation
- prepared execution [ODBC]
- SQLPrepare function
- ODBC applications, statements
- SQLExecute function
- statements [ODBC], prepared execution
ms.assetid: f3a9d32b-6cd7-4f0c-b38d-c8ccc4ee40c3
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 841de8200a7f09301fafa2fc38573b7895e8634f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="prepared-execution"></a>Esecuzione preparata
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  L'API ODBC definisce l'esecuzione preparata per ridurre l'overhead dell'analisi e della compilazione associato all'esecuzione ripetuta di un'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Nell'applicazione viene compilata una stringa di caratteri contenente un'istruzione SQL che viene eseguita in due fasi. Chiama [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360) una volta per l'istruzione analizzata e compilata in un piano di esecuzione mediante il [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Chiama quindi **SQLExecute** per ogni esecuzione del piano di esecuzione preparata. con conseguente risparmio dell'overhead correlato all'analisi e alla compilazione in ogni esecuzione. L'esecuzione preparata viene generalmente utilizzata dalle applicazioni per eseguire ripetutamente la stessa istruzione SQL con parametri.  
  
 Per la maggior parte dei database, l'esecuzione preparata è più veloce dell'esecuzione diretta per le istruzioni eseguite più di tre o quattro volte, sopratutto perché l'istruzione viene compilata una sola volta, mentre le istruzioni eseguite direttamente vengono compilate ogni volta che vengono eseguite. L'esecuzione preparata può inoltre offrire una riduzione del traffico di rete perché il driver può inviare all'origine dati un identificatore del piano di esecuzione e i valori dei parametri, anziché un'intera istruzione SQL, ogni volta che viene eseguita l'istruzione.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]viene ridotta la differenza di prestazioni tra l'esecuzione diretta e preparata tramite algoritmi migliorati per il rilevamento e il riutilizzo dei piani di esecuzione da **SQLExecDirect**. offrendo alle istruzioni eseguite direttamente alcuni dei vantaggi di prestazioni associati all'esecuzione preparata. Per ulteriori informazioni, vedere [esecuzione diretta](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md).  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è inoltre disponibile il supporto nativo per l'esecuzione preparata. Un piano di esecuzione si basa su **SQLPrepare** ed eseguito in un secondo momento quando **SQLExecute** viene chiamato. Poiché [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non è necessario compilare stored procedure temporanee **SQLPrepare**, non è previsto alcun overhead aggiuntivo nelle tabelle di sistema in **tempdb**.  
  
 Per motivi di prestazioni, la preparazione dell'istruzione viene posticipata finché **SQLExecute** viene chiamato o un'operazione di metaproprietà (ad esempio [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md) o [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) in ODBC) viene eseguita. Questo è il comportamento predefinito. Eventuali errori nell'istruzione da preparare saranno noti solo dopo l'esecuzione dell'istruzione o dell'operazione di metaproprietà. È possibile disattivare questo comportamento predefinito impostando l'attributo SQL_SOPT_SS_DEFER_PREPARE dell'istruzione specifica del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client su SQL_DP_OFF.  
  
 In caso di posticipata preparare, se si chiama **SQLDescribeCol** o **SQLDescribeParam** prima di chiamare **SQLExecute** genera un round trip aggiuntivo al server. In **SQLDescribeCol**, il driver rimuove la clausola WHERE della query e lo invia al server con SET FMTONLY ON per ottenere la descrizione delle colonne nel primo set di risultati restituiti dalla query. In **SQLDescribeParam**, il driver chiama il server per ottenere una descrizione delle espressioni o delle colonne a cui fa riferimento i marcatori di parametro nella query. Questo metodo presenta inoltre alcune restrizioni, ad esempio non è in grado di risolvere i parametri nelle sottoquery.  
  
 Un utilizzo eccessivo di **SQLPrepare** con il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client comporta una riduzione delle prestazioni, soprattutto quando è connesso a versioni precedenti di SQL Server. L'esecuzione preparata non deve essere utilizzata per le istruzioni eseguite una sola volta. L'esecuzione preparata è più lenta dell'esecuzione diretta per una singola esecuzione di un'istruzione perché richiede un round trip in rete aggiuntivo dal client al server. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene inoltre generata una stored procedure temporanea.  
  
 Le istruzioni preparate non possono essere utilizzate per creare oggetti temporanei in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Alcune applicazioni ODBC precedenti utilizzati **SQLPrepare** qualsiasi momento [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) è stato utilizzato. **SQLBindParameter** non richiedono l'uso di **SQLPrepare**, può essere utilizzato con **SQLExecDirect**. Ad esempio, utilizzare **SQLExecDirect** con **SQLBindParameter** per recuperare il codice restituito o di output da una stored procedure che viene eseguita una sola volta. Non utilizzare **SQLPrepare** con **SQLBindParameter** , a meno che la stessa istruzione viene eseguita più volte.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di istruzioni &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  