---
title: '@@CPU_BUSY (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@CPU_BUSY_TSQL'
- '@@CPU_BUSY'
dev_langs:
- TSQL
helpviewer_keywords:
- CPU [SQL Server]
- status information [SQL Server], CPU
- ticks [SQL Server]
- time [SQL Server], CPU activity
- '@@CPU_BUSY function'
- statistical information [SQL Server], CPU
- CPU [SQL Server], activity
ms.assetid: 81ae0e64-79fa-4a74-9aa5-37045c4cd211
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 165aef4dc063f9487c5ee581981fc013d6f40ff0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="cpubusy-transact-sql"></a>@@CPU_BUSY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Restituisce il tempo di attività di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dopo l'ultimo avvio. Il risultato è in incrementi di tempo di CPU, o "tick" ed è cumulativo per tutte le CPU, pertanto può essere maggiore del tempo trascorso effettivo. Moltiplicare per@TIMETICKS per convertire i microsecondi.
  
> [!NOTE]  
>  Se l'ora restituita@CPU_BUSY o @@IO_BUSY superiore a circa 49 giorni di tempo cumulativo di CPU, viene visualizzato un avviso di overflow aritmetico. In questo caso, il valore di @@CPU_BUSY, @@IO_BUSY e @@IDLE variabili non sono precise.  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
@@CPU_BUSY  
```  
  
## <a name="return-types"></a>Tipi restituiti
**integer**
  
## <a name="remarks"></a>Osservazioni  
Per visualizzare un report contenente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statistiche, tra cui l'attività della CPU, eseguire [sp_monitor](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md).
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene restituita l'attività della CPU di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in corrispondenza della data e dell'ora correnti. Per evitare un overflow aritmetico durante la conversione del valore in microsecondi, uno dei valori viene convertito nel tipo di dati `float`.
  
```sql
SELECT @@CPU_BUSY * CAST(@@TIMETICKS AS float) AS 'CPU microseconds',   
   GETDATE() AS 'As of' ;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`CPU microseconds As of`
  
`---------------- -----------------------`
  
`18406250         2006-12-05 17:00:50.600`
  
## <a name="see-also"></a>Vedere anche
[Sys.dm os_sys_info &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)  
[@@IDLE &#40;Transact-SQL&#41;](../../t-sql/functions/idle-transact-sql.md)  
[@@IO_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/io-busy-transact-sql.md)  
[la procedura sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)  
[Funzioni statistiche di sistema &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)
  
  
