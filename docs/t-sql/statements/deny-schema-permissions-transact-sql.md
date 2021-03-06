---
title: DENY (autorizzazioni per schemi) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], schemas
- schemas [SQL Server], permissions
- permissions [SQL Server], schemas
- DENY statement, schemas
ms.assetid: 300a67c4-d226-4653-9e9f-7ae4d53fcf33
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b966b2f6fa61e3a1f5a60ce048fbfbf69bb9fb7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="deny-schema-permissions-transact-sql"></a>DENY (autorizzazioni per schemi) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Nega autorizzazioni per uno schema.  
  

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DENY permission  [ ,...n ] } ON SCHEMA :: schema_name  
    TO database_principal [ ,...n ]   
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *permission*  
 Specifica un'autorizzazione che può essere negata per uno schema. Per un elenco di queste autorizzazioni, vedere la sezione Osservazioni di seguito in questo argomento.  
  
 ON SCHEMA **::** schema *_name*  
 Specifica lo schema per cui viene negata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 *database_principal*  
 Specifica l'entità a cui viene negata l'autorizzazione. *database_principal* può essere una delle entità seguenti:  
  
-   Utente del database  
-   Ruolo del database  
-   Ruolo applicazione  
-   Utente del database di cui è stato eseguito il mapping a un account di accesso di Windows  
-   Utente del database di cui è stato eseguito il mapping a un gruppo di Windows  
-   Utente del database di cui è stato eseguito il mapping a un certificato  
-   Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica  
-   Utente del database sul quale non viene eseguito il mapping ad alcuna entità server  
  
CASCADE  
 Indica che l'autorizzazione negata viene negata anche ad altre entità alle quali è stata concessa da questa entità.  
  
*denying_principal*  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di negare l'autorizzazione. *denying_principal* può essere una delle entità seguenti:  
  
-   Utente del database  
-   Ruolo del database  
-   Ruolo applicazione  
-   Utente del database di cui è stato eseguito il mapping a un account di accesso di Windows  
-   Utente del database di cui è stato eseguito il mapping a un gruppo di Windows  
-   Utente del database di cui è stato eseguito il mapping a un certificato  
-   Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica  
-   Utente del database sul quale non viene eseguito il mapping ad alcuna entità server  
  
## <a name="remarks"></a>Remarks  
 Uno schema è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile negare per uno schema, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione dello schema|Autorizzazione dello schema in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|-----------------------|----------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SCHEMA|  
|CONTROL|CONTROL|CONTROL|  
|CREATE SEQUENCE|ALTER|ALTER ANY SCHEMA|  
|Elimina|CONTROL|Elimina|  
|EXECUTE|CONTROL|EXECUTE|  
|INSERT|CONTROL|INSERT|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|CONTROL|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL per lo schema. Se si utilizza l'opzione AS, l'entità specificata deve essere proprietaria dello schema.  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SCHEMA &#40;Transact-SQL&#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.fn_my_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  
