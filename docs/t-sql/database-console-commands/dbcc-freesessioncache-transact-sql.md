---
title: DBCC FREESESSIONCACHE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|database-console-commands
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- FREESESSIONCACHE
- FREESESSIONCACHE_TSQL
- DBCC_FREESESSIONCACHE_TSQL
- DBCC FREESESSIONCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC FREESESSIONCACHE statement
- distributed queries [SQL Server], cache
- clearing distributed query cache
- flushing distributed query cache
ms.assetid: a256ba63-7e11-4d5e-abc0-1fa4ed072e63
caps.latest.revision: 15
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 22875c70f330b6df996358fd3bee1802e777365c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dbcc-freesessioncache-transact-sql"></a>DBCC FREESESSIONCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Scarica la cache delle connessioni query distribuite usata dalle query distribuite per un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
```sql
DBCC FREESESSIONCACHE [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argomenti  
 WITH NO_INFOMSGS  
 Disattiva tutti i messaggi informativi.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene scaricata la cache delle query distribuite.
  
```sql
USE AdventureWorks2012;  
GO  
DBCC FREESESSIONCACHE WITH NO_INFOMSGS;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
