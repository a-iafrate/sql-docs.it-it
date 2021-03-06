---
title: sp_tables (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_tables
- sp_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables
ms.assetid: 787a2fa5-87a1-49bd-938b-6043c245f46b
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b0a4e8b4ae1b78da17beb1a5289a90782979ad3c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sptables-transact-sql"></a>sp_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Viene restituito un elenco di oggetti su cui è possibile eseguire una query nell'ambiente corrente, ovvero qualsiasi tabella o vista eccetto gli oggetti sinonimo.  
  
> [!NOTE]  
>  Per determinare il nome dell'oggetto di base di un sinonimo, eseguire una query di [Synonyms](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md) vista del catalogo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_tables [ [ @table_name = ] 'name' ]   
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @table_type = ] "type" ]   
     [ , [@fUsePattern = ] 'fUsePattern'];  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@table_name=** ] **'***name***'**  
 Tabella utilizzata per restituire informazioni del catalogo. *nome* viene **nvarchar (384)**, con un valore predefinito è NULL. La ricerca con caratteri jolly è supportata.  
  
 [  **@table_owner=** ] **'***proprietario***'**  
 Proprietario della tabella utilizzata per restituire informazioni sul catalogo. *proprietario* viene **nvarchar (384)**, con un valore predefinito è NULL. La ricerca con caratteri jolly è supportata. Se owner viene omesso, vengono applicate le regole di visibilità della tabella predefinite nel sistema DBMS sottostante.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se l'utente corrente è il proprietario di una tabella con il nome specificato, vengono restituite le colonne di tale tabella. Se owner viene omesso e l'utente corrente non è il proprietario di una tabella avente il nome specificato, viene eseguita la ricerca di una tabella avente il nome specificato e il cui proprietario corrisponde al proprietario del database. Se viene individuata, vengono restituite le colonne di tale tabella.  
  
 [  **@table_qualifier=** ] **'***qualificatore***'**  
 Nome del qualificatore di tabella. *qualificatore* viene **sysname**, con un valore predefinito è NULL. Vari prodotti DBMS supportano nomi in tre parti per le tabelle (*qualificatore ***.*** proprietario ***.*** nome*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa colonna rappresenta il nome del database. In altri prodotti rappresenta il nome del server dell'ambiente di database della tabella.  
  
 [ **,** [  **@table_type=** ] **"'***tipo***'**, **'** tipo **'"** ]  
 Elenco di valori separati da virgola che fornisce informazioni su tutte le tabelle dei tipi specificati. Questi includono **tabella**, **SYSTEMTABLE**, e **vista**. *tipo di* viene **varchar(100)**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  È necessario racchiudere ogni tipo di tabella tra virgolette singole e l'intero parametro tra virgolette doppie. I tipi di tabella devono essere specificati in maiuscolo. Se l'opzione SET QUOTED_IDENTIFIER è impostata su ON, è necessario sostituire le virgolette singole con quelle doppie e racchiudere l'intero parametro tra virgolette singole.  
  
 [  **@fUsePattern =** ] **'***fUsePattern***'**  
 Determina se il carattere di sottolineatura ( _ ), il simbolo di percentuale ( % ) e le parentesi quadre ( [ o ] ) vengono interpretate come caratteri jolly. I valori validi sono 0 (utilizzo dei criteri di ricerca disattivato) e 1 (utilizzo dei criteri di ricerca attivato). *fUsePattern* viene **bit**, con un valore predefinito è 1.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|Nome del qualificatore della tabella. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa colonna rappresenta il nome del database. Questo campo può essere NULL.|  
|**TABLE_OWNER**|**sysname**|Nome del proprietario della tabella. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa colonna rappresenta il nome dell'utente del database che ha creato la tabella. Questo campo restituisce sempre un valore.|  
|**TABLE_NAME**|**sysname**|Nome della tabella. Questo campo restituisce sempre un valore.|  
|**TABLE_TYPE**|**varchar (32)**|Tabella, tabella di sistema o vista.|  
|**SEZIONE OSSERVAZIONI**|**varchar(254)**|In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non viene restituito alcun valore per questa colonna.|  
  
## <a name="remarks"></a>Osservazioni  
 Per ottenere la massima interoperabilità, è consigliabile che nel client del gateway siano utilizzati solo i caratteri jolly standard SQL-92, ovvero i caratteri % e _.  
  
 Le informazioni sui privilegi relativi all'accesso in lettura o scrittura dell'utente corrente per una tabella specifica non vengono necessariamente verificate e di conseguenza l'accesso non è garantito. Questo set di risultati include non solo tabelle e viste, ma anche sinonimi e alias di gateway dei prodotti DBMS che supportano questi tipi. Se l'attributo server **sp_server_info** è Y nel set di risultati per **sp_server_info**, vengono restituite solo le tabelle accessibili dall'utente corrente.  
  
 **sp_tables** equivale a **SQLTables** in ODBC. I risultati restituiti vengono ordinati in base **TABLE_TYPE**, **TABLE_QUALIFIER**, **TABLE_OWNER**, e **TABLE_NAME**.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione SELECT per lo schema.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-a-list-of-objects-that-can-be-queried-in-the-current-environment"></a>A. Restituzione di un elenco di oggetti su cui è possibile eseguire query nell'ambiente corrente  
 Nell'esempio seguente viene restituito un elenco di oggetti su cui è possibile eseguire una query nell'ambiente corrente.  
  
```  
EXEC sp_tables ;  
```  
  
### <a name="b-returning-information-about-the-tables-in-a-specified-schema"></a>B. Restituzione di informazioni sulle tabelle in uno schema specificato  
 Nell'esempio seguente vengono restituite informazioni sulle tabelle appartenenti allo schema `Person` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_tables   
   @table_name = '%',  
   @table_owner = 'Person',  
   @table_qualifier = 'AdventureWorks2012';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-a-list-of-objects-that-can-be-queried-in-the-current-environment"></a>C. Restituzione di un elenco di oggetti su cui è possibile eseguire query nell'ambiente corrente  
 Nell'esempio seguente viene restituito un elenco di oggetti su cui è possibile eseguire una query nell'ambiente corrente.  
  
```  
EXEC sp_tables ;  
```  
  
### <a name="d-returning-information-about-the-tables-in-a-specified-schema"></a>D. Restituzione di informazioni sulle tabelle in uno schema specificato  
 L'esempio seguente restituisce informazioni sulle tabelle delle dimensioni di `AdventureWorksPDW201` database.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_tables   
   @table_name = 'Dim%',  
   @table_owner = 'dbo',  
   @table_qualifier = 'AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. Synonyms &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

