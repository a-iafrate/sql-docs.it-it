---
title: Utilizzare Microsoft Distributed Transaction Coordinator (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-how-to
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5e317fca877059bfbd1da8120a3bad3d5b2c2aab
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a>Utilizzare Microsoft Distributed Transaction Coordinator (ODBC).
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a>Per aggiornare due o più computer SQL Server mediante MS DTC  
  
1.  Connettersi a MS DTC utilizzando la funzione MS DTC OLE DtcGetTransactionManager. Per informazioni su MS DTC, vedere Microsoft Distributed Transaction Coordinator.  
  
2.  Chiamare SQL DriverConnect una volta per ogni connessione Microsoft® SQL Server™ che si desidera stabilire.  
  
3.  Chiamare la funzione MS DTC OLE ITransactionDispenser::BeginTransaction per iniziare una transazione MS DTC e ottenere un oggetto Transaction che rappresenta la transazione.  
  
4.  Chiamare [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) una o più volte per ogni connessione ODBC che si desidera integrare nella transazione MS DTC. Il secondo parametro [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) deve essere SQL_ATTR_ENLIST_IN_DTC mentre il terzo parametro deve essere l'oggetto Transaction, ottenuto nel passaggio 3.  
  
5.  Chiamare [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) una volta per ogni computer SQL Server da aggiornare.  
  
6.  Chiamare la funzione MS DTC OLE ITransaction::Commit per eseguire il commit della transazione MS DTC. L'oggetto Transaction non è più valido.  
  
 Per eseguire una serie di transazioni MS DTC, ripetere i passaggi da 3 a 6.  
  
 Per rilasciare il riferimento all'oggetto Transaction, chiamare la funzione MS DTC OLE ITransaction::Return.  
  
 Per usare una connessione ODBC con una transazione MS DTC e quindi usare la stessa connessione con una transazione di SQL Server locale, chiamare [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) con SQL_DTC_DONE.  
  
> [!NOTE]  
>  È inoltre possibile chiamare [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) e [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) per ogni computer SQL Server anziché come suggerito nei passaggi 4 e 5.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di transazioni & #40; ODBC & #41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
