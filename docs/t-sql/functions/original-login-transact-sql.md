---
title: ORIGINAL_LOGIN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ORIGINAL_LOGIN_TSQL
- ORIGINAL_LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], context switches
- context switching [SQL Server], login names
- original login names [SQL Server]
- ORIGINAL_LOGIN function
- names [SQL Server], logins
ms.assetid: ddfb0991-cde3-4b97-a5b7-ee450133f160
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a41a7f9aa080fe6e9c3e4617f7583fdd22e087a8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="originallogin-transact-sql"></a>ORIGINAL_LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il nome dell'account di accesso utilizzato per la connessione all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile utilizzare questa funzione per restituire l'identità dell'account di accesso originale in sessioni in cui si verificano numerosi cambi di contesto espliciti o impliciti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ORIGINAL_LOGIN( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **sysname**  
  
## <a name="remarks"></a>Remarks  
 Questa funzione può essere utile per il controllo dell'identità del contesto di connessione originale. A differenza di funzioni quali [SESSION_USER](../../t-sql/functions/session-user-transact-sql.md) e [CURRENT_USER](../../t-sql/functions/current-user-transact-sql.md) che restituiscono il contesto di esecuzione corrente, ORIGINAL_LOGIN restituisce l'identità dell'account di accesso usato per la prima connessione all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in tale sessione.  
  
 Restituisce NULL nel [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il contesto di esecuzione della sessione corrente viene cambiato dal chiamante delle istruzioni in `login1`. Le funzioni `SUSER_SNAME` e `ORIGINAL_LOGIN` vengono utilizzate per restituire rispettivamente l'utente della sessione corrente, ovvero l'utente su cui è stato impostato il contesto, e l'account di accesso originale.  
  
```  
USE AdventureWorks2012;  
GO  
--Create a temporary login and user.  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE USER user1 FOR LOGIN login1;  
GO  
--Execute a context switch to the temporary login account.  
DECLARE @original_login sysname;  
DECLARE @current_context sysname;  
EXECUTE AS LOGIN = 'login1';  
SET @original_login = ORIGINAL_LOGIN();  
SET @current_context = SUSER_SNAME();  
SELECT 'The current executing context is: '+ @current_context;  
SELECT 'The original login in this session was: '+ @original_login  
GO  
-- Return to the original execution context  
-- and remove the temporary principal.  
REVERT;  
GO  
DROP LOGIN login1;  
DROP USER user1;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-transact-sql.md)   
 [REVERT &#40;Transact-SQL&#41;](../../t-sql/statements/revert-transact-sql.md)  
  
  
