---
title: SET ANSI_DEFAULTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET ANSI_DEFAULTS
- ANSI_DEFAULTS
- SET_ANSI_DEFAULTS_TSQL
- ANSI_DEFAULTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ANSI_DEFAULTS option
- SET ANSI_DEFAULTS statement
ms.assetid: bd721d97-6e23-488b-8c8c-c0453d5b3b86
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c343bc81ab744836db2a2e18ed3cd2890500d048
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-ansidefaults-transact-sql"></a>SET ANSI_DEFAULTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Controlla un gruppo di impostazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che specificano collettivamente alcune funzionalità standard di ISO.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>Sintassi

```
-- Syntax for SQL Server

SET ANSI_DEFAULTS { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_DEFAULTS ON
```

## <a name="remarks"></a>Remarks  
 SET ANSI_DEFAULTS è un'impostazione sul lato server non modificata dal client. Il client gestisce apposite impostazioni che per impostazione predefinita costituiscono l'opposto delle impostazioni del server. L'impostazione del server non deve essere modificata dagli utenti. Per modificare il comportamento del client, gli utenti devono utilizzare SQL_COPT_SS_PRESERVE_CURSORS. Per altre informazioni, vedere [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Quando è attivata (ON), questa opzione attiva le seguenti impostazioni di ISO:  
  
|||  
|-|-|  
|SET ANSI_NULLS|SET CURSOR_CLOSE_ON_COMMIT|  
|SET ANSI_NULL_DFLT_ON|SET IMPLICIT_TRANSACTIONS|  
|SET ANSI_PADDING|SET QUOTED_IDENTIFIER|  
|SET ANSI_WARNINGS||  
  
 L'insieme di queste opzioni SET ISO standard definisce l'ambiente di elaborazione della query per l'intera durata della sessione di lavoro dell'utente o dell'esecuzione di un trigger o di una stored procedure. Queste opzioni SET tuttavia non includono tutte le opzioni necessarie per la conformità allo standard ISO.  
  
 Quando si utilizzano indici in colonne calcolate e viste indicizzate, quattro delle opzioni predefinite, ovvero ANSI_NULLS, ANSI_PADDING, ANSI_WARNINGS e QUOTED_IDENTIFIER, devono essere impostate su ON. Queste opzioni predefinite fanno parte delle sette opzioni SET a cui devono essere assegnati i valori richiesti durante la creazione e la modifica degli indici in colonne calcolate e viste indicizzate. Le altre opzioni SET sono ARITHABORT (ON), CONCAT_NULL_YIELDS_NULL (ON) e NUMERIC_ROUNDABORT (OFF). Per altre informazioni sulle impostazioni dell'opzione SET necessarie per viste indicizzate e indici nelle colonne calcolate, vedere "Considerazioni sull'uso delle istruzioni SET" nell'argomento [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md).  
  
 Il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client e il provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impostano automaticamente l'opzione ANSI_DEFAULTS su ON al momento della connessione. Il driver e il provider impostano quindi le opzioni CURSOR_CLOSE_ON_COMMIT e IMPLICIT_TRANSACTIONS su OFF. È possibile configurare le opzioni SET CURSOR_CLOSE_ON_COMMIT e SET IMPLICIT_TRANSACTIONS impostandole su OFF nelle origini dei dati ODBC, negli attributi di connessione ODBC o nelle proprietà di connessione OLE DB che sono state impostate nell'applicazione prima della connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'opzione predefinita per SET ANSI_DEFAULTS è OFF per le connessioni di applicazioni DB-Library.  
  
 Quando si imposta l'opzione SET ANSI_DEFAULTS, l'opzione SET QUOTED_IDENTIFIER viene impostata in fase di analisi, mentre le opzioni seguenti vengono impostate in fase di esecuzione:  
  
|||  
|-|-|  
|SET ANSI_NULLS|SET ANSI_WARNINGS|  
|SET ANSI_NULL_DFLT_ON|SET CURSOR_CLOSE_ON_COMMIT|  
|SET ANSI_PADDING|SET IMPLICIT_TRANSACTIONS|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene impostata l'opzione `SET ANSI_DEFAULTS ON` e viene utilizzata l'istruzione `DBCC USEROPTIONS` per visualizzare le impostazioni su cui ha effetto.  
  
```  
-- SET ANSI_DEFAULTS ON.  
SET ANSI_DEFAULTS ON;  
GO  
-- Display the current settings.  
DBCC USEROPTIONS;  
GO  
-- SET ANSI_DEFAULTS OFF.  
SET ANSI_DEFAULTS OFF;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DBCC USEROPTIONS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-useroptions-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_NULL_DFLT_ON &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)   
 [SET CURSOR_CLOSE_ON_COMMIT &#40;Transact-SQL&#41;](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)   
 [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)  
  
  
