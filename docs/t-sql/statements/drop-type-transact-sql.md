---
title: DROP TYPE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP TYPE
- DROP_TYPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [SQL Server], deleting
- UDTs [SQL Server], deleting
- alias data types [SQL Server], removing
- DROP TYPE statement
ms.assetid: 11bf83f9-0718-4238-a835-83d2eb14ae7b
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 063c94424466d3a4871098fc046060db94283d27
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="drop-type-transact-sql"></a>DROP TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Rimuove un tipo di dati alias o un tipo CLR definito dall'utente dal database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DROP TYPE [ IF EXISTS ] [ schema_name. ] type_name [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *IF EXISTS*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Rimuove in modo condizionale il tipo solo se esiste già.  
  
 *schema_name*  
 Nome dello schema a cui appartiene il tipo di dati alias o il tipo definito dall'utente.  
  
 *type_name*  
 Nome del tipo di dati alias o del tipo definito dall'utente che si desidera rimuovere.  
  
## <a name="remarks"></a>Remarks  
 L'istruzione DROP TYPE non verrà eseguita nei casi seguenti:  
  
-   Nel database sono presenti tabelle che contengono colonne con il tipo di dati alias o il tipo definito dall'utente. Per recuperare informazioni sulle colonne con tipo di dati alias o definito dall'utente, è possibile eseguire una query sulla vista del catalogo [sys.columns](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) o [sys.column_type_usages](../../relational-databases/system-catalog-views/sys-column-type-usages-transact-sql.md).  
  
-   Sono presenti colonne calcolate, vincoli CHECK e viste e funzioni associate a schema le cui definizioni fanno riferimento al tipo di dati alias o definito dall'utente. Per recuperare informazioni su tali riferimenti, è possibile eseguire una query sulla vista del catalogo [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md).  
  
-   Nel database sono stati creati trigger, funzioni o stored procedure e tali routine utilizzano variabili e parametri con tipo di dati alias o definito dall'utente. Per recuperare informazioni sui parametri con tipo di dati alias o definito dall'utente, è possibile eseguire una query sulla vista del catalogo [sys.parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md) o [sys.parameter_type_usages](../../relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL per *type_name* o l'autorizzazione ALTER per *schema_name*.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente si presuppone che il tipo denominato `ssn` sia già stato creato nel database corrente.  
  
```  
DROP TYPE ssn ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
