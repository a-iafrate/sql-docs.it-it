---
title: sp_databases (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_databases_TSQL
- sp_databases
dev_langs:
- TSQL
helpviewer_keywords:
- sp_databases
ms.assetid: 2a83b92a-9ecc-43c4-8ff4-e91e3a940b5a
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c9f60f43f2fb26b1e166770f3f0e5b923ef4937a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spdatabases-transact-sql"></a>sp_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elenca i database disponibili in un'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o accessibili tramite un gateway di database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_databases  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**DATABASE_NAME**|**sysname**|Nome del database. Nel [!INCLUDE[ssDE](../../includes/ssde-md.md)], questa colonna rappresenta il nome del database archiviata nel **Sys. Databases** vista del catalogo.|  
|**DATABASE_SIZE**|**int**|Dimensioni del database in kilobyte.|  
|**SEZIONE OSSERVAZIONI**|**varchar(254)**|In [!INCLUDE[ssDE](../../includes/ssde-md.md)] questo campo restituisce sempre NULL.|  
  
## <a name="remarks"></a>Osservazioni  
 I nomi di database restituiti possono essere utilizzati come parametri nell'istruzione USE per modificare il contesto del database corrente.  
  
 **sp_databases** non ha un equivalente in Open Database Connectivity (ODBC).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CREATE DATABASE, ALTER ANY DATABASE o VIEW ANY DEFINITION ed è necessario disporre dell'autorizzazione di accesso al database. Non è possibile negare l'autorizzazione VIEW ANY DEFINITION.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrata l'esecuzione di `sp_databases`.  
  
```sql  
USE master;  
GO  
EXEC sp_databases;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [HAS_DBACCESS &#40;Transact-SQL&#41;](../../t-sql/functions/has-dbaccess-transact-sql.md)  
  
  
