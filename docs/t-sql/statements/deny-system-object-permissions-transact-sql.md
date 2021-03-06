---
title: DENY - autorizzazioni per oggetti di sistema (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
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
- DENY statement, system objects
- encryption [SQL Server], system objects
- system objects [SQL Server]
- cryptography [SQL Server], system objects
ms.assetid: 4e43f954-0982-470b-a239-08a13c61563a
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1428cbd738588266c6090053dc8987724fbbf7a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="deny-system-object-permissions-transact-sql"></a>DENY - autorizzazioni per oggetti di sistema (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Nega le autorizzazioni per oggetti di sistema come stored procedure, stored procedure estese, funzioni e viste.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DENY { SELECT | EXECUTE } ON [ sys.]system_object TO principal   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **sys.**]  
 Il qualificatore **sys** è obbligatorio solo per riferimenti a viste del catalogo e viste a gestione dinamica (DMV).  
  
 *system_object*  
 Specifica l'oggetto per cui viene negata l'autorizzazione.  
  
 *principal*  
 Specifica l'entità da cui viene revocata l'autorizzazione.  
  
## <a name="remarks"></a>Remarks  
 È possibile utilizzare questa istruzione per negare le autorizzazioni per particolari stored procedure, stored procedure estese, funzioni con valori di tabella, funzioni scalari, viste, viste del catalogo, viste di compatibilità, viste INFORMATION_SCHEMA, viste a gestione dinamica e tabelle di sistema installate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ognuno di questi oggetti di sistema esiste come record univoco nel database delle risorse (**mssqlsystemresource**). Il database delle risorse è di sola lettura. Un collegamento all'oggetto è esposto in forma di record nello schema **sys** di tutti i database.  
  
 I nomi di procedure non qualificati vengono risolti dal processo predefinito di risoluzione dei nomi nel database delle risorse. Il qualificatore **sys** è pertanto obbligatorio solo quando si specificano viste del catalogo e DMV.  
  
> [!CAUTION]  
>  La negazione di autorizzazioni per gli oggetti di sistema causerà errori nelle applicazioni che dipendono da tali oggetti. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilizza le viste del catalogo e potrebbe funzionare in modo imprevisto se si modificano le autorizzazioni predefinite per le viste del catalogo.  
  
 Non è supportata la negazione di autorizzazioni per i trigger e le colonne di oggetti di sistema.  
  
 Le autorizzazioni per gli oggetti di sistema vengono mantenute in caso di aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Gli oggetti di sistema sono visibili nella vista del catalogo [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) . Le autorizzazioni per gli oggetti di sistema sono visibili nella vista del catalogo [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) nel database **master** .  
  
 La query seguente restituisce informazioni sulle autorizzazioni degli oggetti di sistema:  
  
```  
SELECT * FROM master.sys.database_permissions AS dp   
    JOIN sys.system_objects AS so  
    ON dp.major_id = so.object_id  
    WHERE dp.class = 1 AND so.parent_object_id = 0 ;  
GO  
```  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene negata l'autorizzazione `EXECUTE` per `xp_cmdshell` a `public`.  
  
```  
DENY EXECUTE ON sys.xp_cmdshell TO public;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [GRANT - autorizzazioni per oggetti di sistema &#40;Transact-SQL&#41;](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)   
 [REVOKE - autorizzazioni per oggetti di sistema &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)  
  
  
