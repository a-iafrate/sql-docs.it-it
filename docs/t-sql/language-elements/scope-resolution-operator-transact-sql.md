---
title: ":: (risoluzione dell'ambito) (Transact-SQL) | Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
dev_langs:
- TSQL
ms.assetid: 764d8f91-957b-4037-997b-a9b6b533c504
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 924feab0d037f4da1f6e18ac63b6ba6417f13ee2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="-scope-resolution-transact-sql"></a>:: (risoluzione dell'ambito) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  L'operatore di risoluzione dell'ambito **::** fornisce l'accesso ai membri statici di un tipo di dati composto. Un tipo di dati composto è un tipo che contiene più tipi di dati e metodi semplici, ad esempio i tipi CLR predefiniti e i tipi definiti dall'utente (UDT) SQLCLR.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene indicato come utilizzare l'operatore di risoluzione dell'ambito per accedere al membro `GetRoot()` di tipo `hierarchyid`.  
  
```  
DECLARE @hid hierarchyid;  
SELECT @hid = hierarchyid::GetRoot();  
PRINT @hid.ToString();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `/`  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
