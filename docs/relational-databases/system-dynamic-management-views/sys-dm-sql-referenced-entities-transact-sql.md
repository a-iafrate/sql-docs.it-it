---
title: Sys.dm sql_referenced_entities (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 11/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_sql_referenced_entities_TSQL
- dm_sql_referenced_entities
- sys.dm_sql_referenced_entities
- sys.dm_sql_referenced_entities_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_sql_referenced_entities dynamic management function
ms.assetid: 077111cb-b860-4d61-916f-bac5d532912f
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 25c80c8239653415486d18d0773c45076668ca18
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmsqlreferencedentities-transact-sql"></a>sys.dm_sql_referenced_entities (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni entità definita dall'utente a cui si fa riferimento per nome nella definizione dell'entità di riferimento specificata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Una dipendenza tra due entità viene creata quando un'entità definita dall'utente, detta il *fa riferimento a entità*, viene visualizzato in base al nome in un'espressione SQL persistente di un'altra entità definita dall'utente, chiamata di *entità di riferimento* . Ad esempio, se una stored procedure è l'entità di riferimento specificata, questa funzione restituisce tutte le entità definite dall'utente indicate nella stored procedure, ad esempio tabelle, viste, tipi definiti dall'utente (UDT) o altre stored procedure.  
  
 È possibile utilizzare questa funzione a gestione dinamica per creare un report sui seguenti tipi di entità indicati dall'entità di riferimento specificata:  
  
-   Entità associate allo schema  
  
-   Entità non associate allo schema  
  
-   Entità tra database e tra server  
  
-   Dipendenze a livello di colonna relative alle entità associate e non associate allo schema  
  
-   Tipi definiti dall'utente [alias e CLR definito dall'utente]  
  
-   raccolte di XML Schema  
  
-   Funzioni di partizione  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
sys.dm_sql_referenced_entities (  
    ' [ schema_name. ] referencing_entity_name ' , ' <referencing_class> ' )  
  
<referencing_class> ::=  
{  
    OBJECT  
  | DATABASE_DDL_TRIGGER  
  | SERVER_DDL_TRIGGER  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 [ *schema_name*. ] *referencing_entity_name*  
 Nome dell'entità di riferimento. *schema_name* è obbligatorio quando la classe di riferimento è OBJECT.  
  
 *schema_name.referencing_entity_name* viene **nvarchar(517)**.  
  
 *< Classe_riferimento >* :: = {oggetto | DATABASE_DDL_TRIGGER | SERVER_DDL_TRIGGER}  
 Classe dell'entità di riferimento specificata. È possibile specificare solo una classe per istruzione.  
  
 *< classe_riferimento >* viene **nvarchar(60)**.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|referencing_minor_id|**int**|ID di colonna quando l'entità di riferimento è una colonna, in caso contrario, 0. Non ammette i valori Null.|  
|referenced_server_name|**sysname**|Nome del server dell'entità a cui viene fatto riferimento.<br /><br /> Questa colonna viene popolata per le dipendenze tra server eseguite specificando un nome valido composto da quattro parti. Per informazioni sui nomi composti da più parti, vedere [convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).<br /><br /> Valore NULL per le dipendenze non associate a schemi per cui è stato fatto riferimento all'entità senza specificare un nome in quattro parti.<br /><br /> Valore NULL per le entità associate a schemi perché devono essere nello stesso database e pertanto possono essere definite solo utilizzando due parti (*Object*) nome.|  
|referenced_database_name|**sysname**|Nome del database dell'entità a cui viene fatto riferimento.<br /><br /> Questa colonna viene popolata per i riferimenti tra database o tra server eseguiti specificando un nome valido composto da tre o quattro parti.<br /><br /> Valore NULL per i riferimenti non associati a schemi che vengono specificati utilizzando un nome composto da una o due parti.<br /><br /> Valore NULL per le entità associate a schemi perché devono essere nello stesso database e pertanto possono essere definite solo utilizzando due parti (*Object*) nome.|  
|referenced_schema_name|**sysname**|Schema a cui appartiene l'entità a cui viene fatto riferimento.<br /><br /> Valore NULL per i riferimenti non associati a schemi in cui è stato fatto riferimento all'entità senza specificare il nome dello schema.<br /><br /> Il valore non è mai NULL per riferimenti associati a schemi.|  
|referenced_entity_name|**sysname**|Nome dell'entità a cui viene fatto riferimento. Non ammette i valori Null.|  
|referenced_minor_name|**sysname**|Nome della colonna quando l'entità a cui viene fatto riferimento è una colonna; in caso contrario, NULL. referenced_minor_name è NULL, ad esempio, nella riga che elenca l'entità stessa cui viene fatto riferimento.<br /><br /> Un'entità a cui viene fatto riferimento è una colonna, se il nome nell'entità di riferimento identifica una colonna o se l'entità padre viene utilizzata in un'istruzione SELECT *.|  
|referenced_id|**int**|ID dell'entità a cui viene fatto riferimento. Quando referenced_minor_id è diverso da 0, referenced_id è l'entità in cui viene definita la colonna.<br /><br /> Il valore è sempre NULL per i riferimenti tra server.<br /><br /> NULL per riferimenti tra database quando non è possibile determinare l'ID perché il database è offline o l'entità non può essere associata.<br /><br /> Valore NULL per i riferimenti all'interno del database se non è possibile determinare l'ID. Per i riferimenti non associati a schema, l'ID non può essere risolto quando l'entità di riferimento non esiste nel database o quando la risoluzione dei nomi è dipendente dal chiamante.  Nel secondo caso, is_caller_dependent viene impostato su 1.<br /><br /> Il valore non è mai NULL per riferimenti associati a schemi.|  
|referenced_minor_id|**int**|ID della colonna quando l'entità a cui viene fatto riferimento è una colonna; in caso contrario, 0. referenced_minor_is è 0, ad esempio, nella riga che elenca l'entità stessa cui viene fatto riferimento.<br /><br /> Per i riferimenti non associati a schemi, le dipendenze della colonna vengono indicate solo quando è possibile associare tutte le entità cui viene fatto riferimento. Se non è possibile associare una di tali entità, non viene segnalata alcuna dipendenza a livello di colonna e il valore di referenced_minor_id è 0. Vedere l'esempio D.|  
|referenced_class|**tinyint**|Classe dell'entità con riferimenti.<br /><br /> 1 = Oggetto o colonna<br /><br /> 6 = Tipo<br /><br /> 10 = Raccolta di XML Schema<br /><br /> 21 = Funzione di partizione|  
|referenced_class_desc|**nvarchar(60)**|Descrizione della classe dell'entità a cui viene fatto riferimento.<br /><br /> OBJECT_OR_COLUMN<br /><br /> TYPE<br /><br /> XML_SCHEMA_COLLECTION<br /><br /> PARTITION_FUNCTION|  
|is_caller_dependent|**bit**|Indica che l'associazione di schemi per l'entità cui viene fatto riferimento si verifica in fase di esecuzione. Di conseguenza, la risoluzione dell'ID dell'entità dipende dallo schema del chiamante. Ciò avviene quando l'entità cui viene fatto riferimento è una stored procedure, una stored procedure estesa o una funzione definita dall'utente chiamata all'interno di un'istruzione EXECUTE.<br /><br /> 1 = L'entità cui viene fatto riferimento è dipendente dal chiamante e viene risolta in fase di esecuzione. In questo caso, il valore di referenced_id è NULL.<br /><br /> 0 = L'ID dell'entità a cui viene fatto riferimento non è dipendente dal chiamante. Il valore è sempre 0 per i riferimenti associati a schemi e tra database e tra server che indicano in modo esplicito un nome schema. Ad esempio, un riferimento a un'entità nel formato `EXEC MyDatabase.MySchema.MyProc` non è dipendente dal chiamante. Tuttavia, un riferimento nel formato `EXEC MyDatabase..MyProc` è dipendente dal chiamante.|  
|is_ambiguous|**bit**|Indica il riferimento è ambiguo e può essere risolto in fase di esecuzione per una funzione definita dall'utente, un tipo definito dall'utente (UDT) o un riferimento xquery a una colonna di tipo **xml**. Si supponga, ad esempio, che l'istruzione `SELECT Sales.GetOrder() FROM Sales.MySales` sia definita in una stored procedure. Durante l'esecuzione della stored procedure non è possibile sapere se `Sales.GetOrder()` è una funzione definita dall'utente nello schema `Sales` o una colonna `Sales` di tipo definito dall'utente con un metodo `GetOrder()`.<br /><br /> 1 = Il riferimento a una funzione definita dall'utente o al metodo del tipo definito dall'utente (UDT) della colonna è ambiguo.<br /><br /> 0 = Il riferimento non è ambiguo o l'entità può essere associata correttamente quando la funzione viene chiamata.<br /><br /> Il valore è sempre 0 per i riferimenti associati allo schema.|  
|is_selected|**bit**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1=Colonna o oggetto selezionato.|  
|is_updated|**bit**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1= Colonna o oggetto modificato.|  
|is_select_all|**bit**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1= Oggetto utilizzato in una clausola SELECT * (solo a livello di oggetto).|  
|is_all_columns_found|**bit**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = È possibile trovare tutte le dipendenze delle colonne per l'oggetto.<br /><br /> 0 = Impossibile trovare le dipendenze delle colonne per l'oggetto.|
|is_insert_all|**bit**|**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = l'oggetto viene utilizzato in un'istruzione INSERT senza un elenco di colonne (a livello di oggetto solo).|  
|is_incomplete|**bit**|**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = oggetto o colonna presenta un errore di associazione ed è pertanto incompleta.|
  
## <a name="exceptions"></a>Eccezioni  
 In una delle seguenti condizioni, restituisce un set di risultati vuoto:  
  
-   Viene specificato un oggetto di sistema.  
  
-   L'entità specificata non è presente nel database corrente.  
  
-   L'entità specificata non fa riferimento ad alcuna entità.  
  
-   Viene passato un parametro non valido.  
  
 Restituisce un errore quando l'entità di riferimento specificata è una stored procedure numerata.  
  
 Restituisce l'errore 2020 quando le dipendenze della colonna non possono essere risolte. Questo errore non impedisce alla query di restituire dipendenze a livello di oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione può essere eseguita nel contesto di qualsiasi database per restituire le entità che fanno riferimento a un trigger DDL a livello di server.  
  
 Nella tabella seguente sono elencati i tipi di entità per i quali vengono create e gestite le informazioni sulle dipendenze. Le informazioni sulle dipendenze non vengono create né gestite per regole, impostazioni predefinite, tabelle temporanee, stored procedure temporanee o oggetti di sistema.  
  
|Tipo di entità|Entità di riferimento|Entità con riferimenti|  
|-----------------|------------------------|-----------------------|  
|Tabella|Sì*|Sì|  
|Visualizza|Sì|Sì|  
|Stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)]**|Sì|Sì|  
|stored procedure CLR|no|Sì|  
|Funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] definita dall'utente|Sì|Sì|  
|Funzione CLR definita dall'utente|no|Sì|  
|Trigger CLR (DML e DDL)|no|no|  
|Trigger DML [!INCLUDE[tsql](../../includes/tsql-md.md)]|Sì|no|  
|Trigger DDL [!INCLUDE[tsql](../../includes/tsql-md.md)] a livello di database|Sì|no|  
|Trigger DDL [!INCLUDE[tsql](../../includes/tsql-md.md)] a livello di server|Sì|no|  
|Stored procedure estese|no|Sì|  
|Coda|no|Sì|  
|Sinonimo|no|Sì|  
|Tipo (alias e tipo di CLR definito dall'utente)|no|Sì|  
|Raccolta di XML Schema|no|Sì|  
|Funzione di partizione|no|Sì|  
  
 \* Una tabella viene registrata come un'entità di riferimento solo quando si fa riferimento a un [!INCLUDE[tsql](../../includes/tsql-md.md)] module, tipo definito dall'utente o raccolta di XML schema nella definizione di una colonna calcolata, un vincolo CHECK o un vincolo predefinito.  
  
 ** Le stored procedure numerate con un valore intero maggiore di 1 non vengono registrate come entità di riferimento o a cui viene fatto riferimento.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione SELECT per sys.dm_sql_referenced_entities e l'autorizzazione VIEW DEFINITION per l'entità di riferimento. Per impostazione predefinita, l'autorizzazione SELECT è concessa al ruolo public. È richiesta l'autorizzazione VIEW DEFINITION per il database o un'autorizzazione ALTER ANY DATABASE DDL TRIGGER per il database corrente quando l'entità di riferimento è un trigger DDL a livello di database. È richiesta l'autorizzazione VIEW ANY DEFINITION per il server quando l'entità di riferimento è un trigger DDL a livello di server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-entities-that-are-referenced-by-a-database-level-ddl-trigger"></a>A. Restituzione di entità cui fa riferimento un trigger DDL a livello di database  
 Nell'esempio seguente vengono restituite le entità (tabelle e colonne) cui fa riferimento il trigger DDL `ddlDatabaseTriggerLog` a livello di database.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT referenced_schema_name, referenced_entity_name, referenced_minor_name,   
    referenced_minor_id, referenced_class_desc  
FROM sys.dm_sql_referenced_entities ('ddlDatabaseTriggerLog', 'DATABASE_DDL_TRIGGER');  
GO  
```  
  
### <a name="b-returning-entities-that-are-referenced-by-an-object"></a>B. Restituzione di entità cui fa riferimento un oggetto  
 Nell'esempio seguente vengono restituite le entità cui fa riferimento la funzione `dbo.ufnGetContactInformation` definita dall'utente.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT referenced_schema_name, referenced_entity_name, referenced_minor_name,   
    referenced_minor_id, referenced_class_desc, is_caller_dependent, is_ambiguous  
FROM sys.dm_sql_referenced_entities ('dbo.ufnGetContactInformation', 'OBJECT');  
GO  
```  
  
### <a name="c-returning-column-dependencies"></a>C. Restituzione delle dipendenze della colonna  
 Nell'esempio seguente viene creata la tabella `Table1` con la colonna calcolata `c` definita come somma delle colonne `a` e `b`. Viene quindi chiamata la vista `sys.dm_sql_referenced_entities`. La vista restituisce due righe, una per ogni colonna definita nella colonna calcolata.  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE TABLE dbo.Table1 (a int, b int, c AS a + b);  
GO  
SELECT referenced_schema_name AS schema_name,  
    referenced_entity_name AS table_name,  
    referenced_minor_name AS referenced_column,  
    COALESCE(COL_NAME(OBJECT_ID(N'dbo.Table1'),referencing_minor_id), 'N/A') AS referencing_column_name  
FROM sys.dm_sql_referenced_entities ('dbo.Table1', 'OBJECT');  
GO

-- Remove the table.  
DROP TABLE dbo.Table1;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 schema_name table_name referenced_column referencing_column  
 ----------- ---------- ----------------- ------------------  
 dbo         Table1     a                 c  
 dbo         Table1     b                 c  
```

### <a name="d-returning-non-schema-bound-column-dependencies"></a>D. Restituzione delle dipendenze delle colonne non associate a schemi  
 Nell'esempio seguente viene eliminata `Table1` e vengono create `Table2` e la stored procedure `Proc1`. La procedura fa riferimento a `Table2` e alla tabella `Table1` inesistente. La vista `sys.dm_sql_referenced_entities` viene eseguita con la stored procedure specificata come entità di riferimento. Il set di risultati indica una riga per `Table1` e 3 righe per `Table2`. Poiché `Table1` non è presente, le dipendenze della colonna non possono essere risolte e viene restituito l'errore 2020. La colonna `is_all_columns_found` restituisce 0 per `Table1`, a indicare che sono presenti colonne che non è stato possibile individuare.  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.Table1', 'U' ) IS NOT NULL   
    DROP TABLE dbo.Table1;  
GO  
CREATE TABLE dbo.Table2 (c1 int, c2 int);  
GO  
CREATE PROCEDURE dbo.Proc1 AS  
    SELECT a, b, c FROM Table1;  
    SELECT c1, c2 FROM Table2;  
GO  
SELECT referenced_id, referenced_entity_name AS table_name, referenced_minor_name AS referenced_column_name, is_all_columns_found  
FROM sys.dm_sql_referenced_entities ('dbo.Proc1', 'OBJECT');  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 referenced_id table_name   referenced_column_name  is_all_columns_found  
 ------------- ------------ ----------------------- --------------------  
 935674381     Table2       NULL                    1  
 935674381     Table2       C1                      1  
 935674381     Table2       C2                      1  
 NULL          Table1       NULL                    0  

 Msg 2020, Level 16, State 1, Line 1The dependencies reported for entity "dbo.Proc1" might not include references to all columns. This is either because the entity references an object that does not exist or because of an error in one or more statements in the entity.  Before rerunning the query, ensure that there are no errors in the entity and that all objects referenced by the entity exist.
 ```
  
### <a name="e-demonstrating-dynamic-dependency-maintenance"></a>E. Dimostrazione della gestione delle dipendenze dinamiche  
 Nell'esempio seguente viene esteso l'esempio D per illustrare la gestione dinamica delle dipendenze. Nell'esempio viene prima ricreata `Table1`, eliminata nell'esempio D. Viene quindi rieseguita la vista `sys.dm_sql_referenced_entities` con la stored procedure specificata come entità di riferimento. Il set di risultati indica che vengono restituite entrambe le tabelle e le rispettive colonne definite nella stored procedure. Inoltre, la colonna `is_all_columns_found` restituisce 1 per tutti gli oggetti e le colonne.  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE TABLE Table1 (a int, b int, c AS a + b);  
GO   
SELECT referenced_id, referenced_entity_name AS table_name, referenced_minor_name as column_name, is_all_columns_found  
FROM sys.dm_sql_referenced_entities ('dbo.Proc1', 'OBJECT');  
GO  
DROP TABLE Table1, Table2;  
DROP PROC Proc1;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 referenced_id table_name   referenced_column_name  is_all_columns_found  
 ------------- ------------ ----------------------- --------------------  
 935674381     Table2       NULL                    1 
 935674381     Table2       c1                      1 
 935674381     Table2       c2                      1 
 967674495     Table1       NULL                    1 
 967674495     Table1       a                       1  
 967674495     Table1       b                       1  
 967674495     Table1       c                       1  
 ```
 
### <a name="f-returning-object-or-column-usage"></a>F. Restituzione dell'utilizzo di oggetti e colonne  
 Nell'esempio seguente vengono restituiti gli oggetti e le dipendenze delle colonne della stored procedure `HumanResources.uspUpdateEmployeePersonalInfo`. Questa procedura consente di aggiornare le colonne `NationalIDNumber`, `BirthDate,``MaritalStatus`, e `Gender` del `Employee` tabella basata su un oggetto specificato `BusinessEntityID` valore. Un'altra stored procedure, `upsLogError`, viene definita in un blocco TRY…CATCH per acquisire tutti gli errori di esecuzione. Le colonne `is_selected`, `is_updated` e `is_select_all` restituiscono informazioni sul modo in cui tali oggetti e colonne vengono utilizzati all'interno dell'oggetto di riferimento. La tabella e le colonne modificate vengono indicate con il valore 1 nella colonna is_updated. Viene selezionata solo la colonna `BusinessEntityID` e la stored procedure `uspLogError` non viene né selezionata né modificata.  
  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```sql  
SELECT referenced_entity_name AS table_name, referenced_minor_name as column_name, is_selected, is_updated, is_select_all  
FROM sys.dm_sql_referenced_entities ('HumanResources.uspUpdateEmployeePersonalInfo', 'OBJECT');  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 table_name    column_name         is_selected is_updated is_select_all  
 ------------- ------------------- ----------- ---------- -------------  
 uspLogError   NULL                0           0          0  
 Employee      NULL                0           1          0  
 Employee      BusinessEntityID    1           0          0  
 Employee      NationalIDNumber    0           1          0  
 Employee      BirthDate           0           1          0  
 Employee      MaritalStatus       0           1          0  
 Employee      Gender              0           1          0
 ```
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
  
