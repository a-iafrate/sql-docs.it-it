---
title: Sys. database_usage (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- database_usage
- database_usage_TSQL
- sys.database_usage_TSQL
- sys.database_usage
dev_langs:
- TSQL
helpviewer_keywords:
- database_usage
- sys.database_usage
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: affdc08bb7ae507ca30edfa986cd68a81ba564f2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdatabaseusage-azure-sql-database"></a>sys.database_usage (Database di SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  **Nota: Si applica solo al V11 Database SQL di Azure.**  
  
 Elenca il numero, tipo e durata dei database sul [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server.  
  
 Il **Sys. database_usage** vista contiene le colonne seguenti.  
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|time|Data di esecuzione degli eventi di utilizzo.|  
|sku|Il tipo di livello di servizio per il database: **Web**, **Business**, **base**, **Standard**, **Premium**|  
|quantity|Numero massimo di database di un tipo SKU presente durante il giorno.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Accesso in sola lettura a questa vista è disponibile per tutti gli utenti con autorizzazioni per connettersi al **master** database.  
  
## <a name="remarks"></a>Osservazioni  
 Il **Sys. database_usage** vista restituisce una riga per ogni giorno della sottoscrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Dettagli prezzi del Database SQL](http://go.microsoft.com/fwlink/?LinkID=394978)   
 [Account e fatturazione nel Database SQL di Azure](http://msdn.microsoft.com/library/windowsazure/ee621788.aspx)  
  
  
