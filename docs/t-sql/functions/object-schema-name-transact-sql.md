---
title: OBJECT_SCHEMA_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- OBJECT_SCHEMA_NAME
- OBJECT_SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], names
- schemas [SQL Server], names
- displaying schema names
- database objects [SQL Server], names
- OBJECT_SCHEMA_NAME function
ms.assetid: 5ba90bb9-d045-4164-963e-e9e96c0b1e8b
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f92ef0d1771bd2627895e2e2c67f59aa92e184cc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="objectschemaname-transact-sql"></a>OBJECT_SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il nome dello schema di database per gli oggetti con ambito schema. Per un elenco degli oggetti con ambito schema, vedere [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
OBJECT_SCHEMA_NAME ( object_id [, database_id ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *object_id*  
 ID dell'oggetto da utilizzare. *object_id* è di tipo **int** e si presume che sia un oggetto con ambito schema nel database specificato o nel contesto del database corrente.  
  
 *database_id*  
 ID del database in cui l'oggetto deve essere cercato. *database_id* è di tipo **int**.  
  
## <a name="return-types"></a>Tipi restituiti  
 **sysname**  
  
## <a name="exceptions"></a>Eccezioni  
 Restituisce NULL in caso di errore o se un chiamante non dispone dell'autorizzazione necessaria per visualizzare l'oggetto. Se l'opzione AUTO_CLOSE del database di destinazione è impostata su ON, la funzione aprirà il database.  
  
 Un utente può visualizzare esclusivamente i metadati delle entità a sicurezza diretta di cui è proprietario o per cui ha ricevuto un'autorizzazione. Di conseguenza, le funzioni predefinite di creazione dei metadati come OBJECT_SCHEMA_NAME possono restituire NULL se l'utente non dispone di alcuna autorizzazione per l'oggetto. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ANY per l'oggetto. Per specificare l'ID di un database, è inoltre necessaria l'autorizzazione CONNECT per il database o l'abilitazione dell'account guest.  
  
## <a name="remarks"></a>Remarks  
 È possibile utilizzare funzioni di sistema nell'elenco di selezione, nella clausola WHERE e in tutti i casi in cui è consentita un'espressione. Per altre informazioni, vedere [Espressioni](../../t-sql/language-elements/expressions-transact-sql.md) e [WHERE](../../t-sql/queries/where-transact-sql.md).  
  
 Il set di risultati restituito da questa funzione di sistema utilizza le regole di confronto del database corrente.  
  
 Se non si specifica *database_id*, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] presuppone che *object_id* sia nel contesto del database corrente. Una query che fa riferimento a un valore di *object_id* in un altro database restituisce NULL oppure risultati errati. Ad esempio, nella query seguente il contesto del database corrente è [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. [!INCLUDE[ssDE](../../includes/ssde-md.md)] cerca di restituire un nome di schema di oggetto per l'ID di oggetto specificato in tale database anziché il database specificato nella clausola FROM della query. Verranno pertanto restituite informazioni errate.  
  
```  
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id)  
FROM master.sys.objects;  
  
```  
  
 Nell'esempio seguente viene specificato l'ID del database `master` nella funzione `OBJECT_SCHEMA_NAME` e vengono restituiti i risultati corretti.  
  
```  
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id, 1) AS schema_name  
FROM master.sys.objects;  
  
```  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-the-object-schema-name-and-object-name"></a>A. Restituzione del nome dello schema dell'oggetto e del nome dell'oggetto  
 Nell'esempio seguente vengono restituiti il nome dello schema dell'oggetto, il nome dell'oggetto e il testo SQL per tutti i piani di query memorizzati nella cache che non sono istruzioni ad hoc o preparate.  
  
```  
SELECT DB_NAME(st.dbid) AS database_name,   
    OBJECT_SCHEMA_NAME(st.objectid, st.dbid) AS schema_name,  
    OBJECT_NAME(st.objectid, st.dbid) AS object_name,   
    st.text AS query_statement  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
WHERE st.objectid IS NOT NULL;  
GO  
```  
  
### <a name="b-returning-three-part-object-names"></a>B. Restituzione dei nomi degli oggetti in tre parti  
 Nell'esempio seguente vengono restituiti il nome del database, dello schema e dell'oggetto, nonché tutte le altre colonne della vista a gestione dinamica `sys.dm_db_index_operational_stats` per tutti gli oggetti di tutti i database.  
  
```  
SELECT QUOTENAME(DB_NAME(database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_SCHEMA_NAME(object_id, database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_NAME(object_id, database_id))  
    , *   
FROM sys.dm_db_index_operational_stats(null, null, null, null);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni per i metadati &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [OBJECT_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/object-name-transact-sql.md)   
 [Entità a protezione diretta](../../relational-databases/security/securables.md)  
  
  
