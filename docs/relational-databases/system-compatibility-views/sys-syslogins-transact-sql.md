---
title: Sys. syslogins (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syslogins_TSQL
- syslogins
- sys.syslogins
- sys.syslogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syslogins compatibility view
- syslogins system table
ms.assetid: 4cb34f17-a4bb-469f-a218-71f074e6308f
caps.latest.revision: 41
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 924ae2b530c719085e21d7b045e4a872255b3009
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="syssyslogins-transact-sql"></a>sys.syslogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni account di accesso.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**sid**|**varbinary(85)**|Identificatore di sicurezza.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**createdate**|**datetime**|Data in cui l'account di accesso è stato aggiunto.|  
|**updateDate**|**datetime**|Data di aggiornamento dell'account di accesso.|  
|**accdate**|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totcpu**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totio**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**spacelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**timelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**resultlimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**name**|**sysname**|Nome dell'account di accesso dell'utente.|  
|**dbname**|**sysname**|Nome del database predefinito dell'utente quando viene stabilita una connessione.|  
|**password**|**nvarchar(128)**|Restituisce NULL.|  
|**Lingua**|**sysname**|Lingua predefinita dell'utente.|  
|**denylogin**|**int**|1 = L'account di accesso è un utente o un gruppo di [!INCLUDE[msCoName](../../includes/msconame-md.md)] a cui è stato negato l'accesso.|  
|**HasAccess**|**int**|1 = L'account di accesso dispone dell'accesso al server.|  
|**isntname**|**int**|1 = L'account di accesso è un utente o un gruppo di Windows.<br /><br /> 0 = L'account di accesso è un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**isntgroup**|**int**|1 = L'account di accesso è un gruppo di Windows.|  
|**isntuser**|**int**|1 = L'account di accesso è un utente di Windows.|  
|**sysadmin**|**int**|1 = account di accesso è membro il **sysadmin** ruolo del server.|  
|**securityadmin**|**int**|1 = account di accesso è membro il **securityadmin** ruolo del server.|  
|**serveradmin**|**int**|1 = account di accesso è membro il **serveradmin** ruolo predefinito del server.|  
|**setupadmin**|**int**|1 = account di accesso è membro il **setupadmin** ruolo predefinito del server.|  
|**processadmin**|**int**|1 = account di accesso è membro il **processadmin** ruolo predefinito del server.|  
|**diskadmin**|**int**|1 = account di accesso è membro il **diskadmin** ruolo predefinito del server.|  
|**dbcreator**|**int**|1 = account di accesso è membro il **dbcreator** ruolo predefinito del server.|  
|**bulkadmin**|**int**|1 = account di accesso è membro il **bulkadmin** ruolo predefinito del server.|  
|**LoginName**|**nvarchar(128)**|Nome dell'account di accesso dell'utente. Disponibile per compatibilità con le versioni precedenti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
