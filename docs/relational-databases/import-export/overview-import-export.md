---
title: Importare ed esportare dati da SQL Server e dal database SQL di Microsoft Azure | Microsoft Docs
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 6e754198cf82a7ba0752fe8f20c3780a8ac551d7
ms.openlocfilehash: 3c41be0642b13b63367c5601b716b506808472e7
ms.contentlocale: it-it
ms.lasthandoff: 09/14/2017

---
# <a name="import-and-export-data-from-sql-server-and-azure-sql-database"></a>Importare ed esportare dati da SQL Server e dal database SQL di Microsoft Azure
È possibile usare diversi metodi per importare ed esportare dati da SQL Server e dal database SQL di Microsoft Azure. Tali metodi includono istruzioni Transact-SQL, strumenti da riga di comando e procedure guidate.

È anche possibile importare ed esportare dati in una vasta gamma di formati. Tali formati includono file flat, Excel, database relazionali principali e vari servizi cloud.

## <a name="methods-for-importing-and-exporting-data"></a>Metodi di importazione ed esportazione dei dati

### <a name="use-transact-sql-statements"></a>Usare istruzioni Transact-SQL
È possibile importare dati con i comandi `BULK INSERT` o `OPENROWSET(BULK...)`. In genere tali comandi vengono eseguiti in SQL Server Management Studio (SSMS). Per altre informazioni, vedere [Importare dati per operazioni bulk con BULK INSERT o OPENROWSET (BULK...)](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).

### <a name="use-bcp-from-the-command-prompt"></a>Usare BCP dal prompt dei comandi
È possibile importare ed esportare i dati con l'utilità della riga di comando BCP. Per altre informazioni, vedere [Importare ed esportare dati per operazioni bulk usando l'utilità BCP](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).

### <a name="use-the-sql-server-import-and-export-wizard"></a>Usare Importazione/Esportazione guidata SQL Server
È possibile importare o esportare dati da un'ampia gamma di origini e destinazioni con Importazione/Esportazione guidata SQL Server. Per usare la procedura guidata, è necessario avere installato SQL Server Integration Services (SSIS) o SQL Server Data Tools (SSDT). Per altre informazioni, vedere [Importare ed esportare dati con l'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

### <a name="design-your-own-import-or-export"></a>Progettare la propria importazione o esportazione
Se si vuole progettare un'importazione di dati personalizzata, è possibile usare le funzionalità o i servizi seguenti:
-   SQL Server Integration Services. Per altre informazioni, vedere [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md).
-   Azure Data Factory. Per altre informazioni, vedere [Introduzione a Azure Data Factory](https://docs.microsoft.com/azure/data-factory/data-factory-introduction).

## <a name="data-formats-for-import-and-export"></a>Formati dei dati per importazione ed esportazione

### <a name="supported-formats"></a>Formati supportati

È possibile importare ed esportare dati, file flat o un'ampia gamma di altri formati di file, database relazionali e servizi cloud. Per altre informazioni su queste opzioni per strumenti specifici, vedere gli argomenti seguenti
-   Per l'Importazione/Esportazione guidata SQL Server, vedere [Connettersi a origini dati con Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md).
-   Per SQL Server Integration Services, vedere [Connessioni in Integration Services (SSIS)](../../integration-services/connection-manager/integration-services-ssis-connections.md).
-   Per Azure Data Factory, vedere [Connettori di Azure Data Factory](https://docs.microsoft.com/en-us/azure/data-factory/data-factory-amazon-redshift-connector).

### <a name="commonly-used-data-formats"></a>Formati di dati di uso comune

Sono disponibili esempi e considerazioni speciali per alcuni formati di dati di uso comune. Per altre informazioni su tali formati di dati, vedere gli argomenti seguenti:
-   Per Excel, vedere [Importare da Excel](import-data-from-excel-to-sql.md).
-   Per JSON, vedere [Importare documenti JSON in SQL Server](../json/import-json-documents-into-sql-server.md).
-   Per XML, vedere [Importare ed esportare documenti XML](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md).
-   Per l'Archiviazione BLOB di Azure, vedere [Importare ed esportare da Archiviazione BLOB di Azure](examples-of-bulk-access-to-data-in-azure-blob-storage.md).

## <a name="next-steps"></a>Passaggi successivi
Se non si è certi su come cominciare l'attività di importazione o esportazione, valutare la possibilità di eseguire l'Importazione/esportazione guidata SQL Server. Per una breve introduzione, vedere [Iniziare con questo semplice esempio di importazione/esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).
