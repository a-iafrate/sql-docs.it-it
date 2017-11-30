---
title: sysmail_help_profile_sp (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_help_profile_sp_TSQL
- sysmail_help_profile_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_help_profile_sp
ms.assetid: d7169a8e-92b1-49eb-9124-3b2f69755ddb
caps.latest.revision: "41"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b2e503789cf2ad564132f34af4e9ab61464332a
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sysmailhelpprofilesp-transact-sql"></a>sysmail_help_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza le informazioni relative a uno o più profili di posta.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_help_profile_sp  [   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@profile_id**  =] *profile_id*  
 ID del profilo per cui restituire informazioni. *profile_id* è **int**, con un valore predefinito è NULL.  
  
 [  **@profile_name**  =] **'***profile_name***'**  
 Nome del profilo per cui restituire informazioni. *profile_name* è **sysname**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Viene restituito un set di risultati con le colonne seguenti.  
  
||||  
|-|-|-|  
|Nome colonna|Tipo di dati|Description|  
|**profile_id**|**int**|ID del profilo.|  
|**name**|**sysname**|Nome del profilo.|  
|**Descrizione**|**nvarchar(256)**|Descrizione del profilo.|  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene specificato un nome del profilo o l'id del profilo, **sysmail_help_profile_sp** restituisce informazioni relative al profilo. In caso contrario, **sysmail_help_profile_sp** restituisce informazioni su tutti i profili di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.  
  
 La stored procedure **sysmail_help_profile_sp** nel **msdb** database ed è di proprietà di **dbo** dello schema. La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Autorizzazioni di esecuzione per questa routine per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 **A. Elenco di tutti i profili**  
  
 Nell'esempio seguente vengono visualizzati tutti i profili disponibili nell'istanza.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp;  
```  
  
 Quello che segue è un set di risultati di esempio, riformattato per adattarlo alla lunghezza di riga:  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
57          AdventureWorks Operator       Operator mail profile.          
```  
  
 **B. Elenco di un profilo specifico**  
  
 Nell'esempio seguente vengono visualizzate le informazioni relative al profilo `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 Quello che segue è un set di risultati di esempio, riformattato per adattarlo alla lunghezza di riga:  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Posta elettronica database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  