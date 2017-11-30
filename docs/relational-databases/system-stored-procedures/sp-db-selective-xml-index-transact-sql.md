---
title: sp_db_selective_xml_index (Transact-SQL) | Documenti Microsoft
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
- sp_db_selective_xml_index_TSQL
- sp_db_selective_xml_index
dev_langs: TSQL
helpviewer_keywords: sp_db_selective_xml_index procedure
ms.assetid: 017301a2-4a23-4e68-82af-134f3d4892b3
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13c3ba559b77f2cf8c71db96d9df0204e581ced7
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spdbselectivexmlindex-transact-sql"></a>sp_db_selective_xml_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Abilita e disabilita la funzionalità degli indici XML selettivi in un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se chiamata senza parametri, la stored procedure restituisce 1 se l'indice XML selettivo è abilitato in un database specifico.  
  
> [!NOTE]  
>  Per disabilitare l'indice XML selettivo tramite questa stored procedure, il database da inserire in modalità di recupero con registrazione minima utilizzando il [opzioni ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) comando.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```tsql  
  
      sys.sp_db_selective_xml_index[[ @db_name = ] 'db_name'],   
[[ @action = ] 'action']  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@ db_name =** ] **'***db_name***'**  
 Nome del database in cui abilitare o disabilitare l'indice XML selettivo. Se *db_name* è NULL, si presuppone che il database corrente.  
  
 [  **@action =** ] **'***azione***'**  
 Determina se abilitare o disabilitare l'indice. Se viene passato un altro valore ad eccezione di 'on', 'true', 'off' o 'false', verrà generato un errore.  
  
```  
  
Allowed values: 'on', 'off', 'true', 'false'  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 **1** se l'indice XML selettivo è abilitato in un database specifico.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-enable-selective-xml-index-functionality"></a>A. Abilitare la funzionalità degli indici XML selettivi  
 Nell'esempio seguente viene abilitato l'indice XML selettivo nel database corrente.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'on';  
GO  
```  
  
 Nell'esempio seguente viene abilitato l'indice XML selettivo nel database AdventureWorks2012.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'true';  
GO  
```  
  
### <a name="b-disable-selective-xml-index-functionality"></a>B. Disabilitare la funzionalità degli indici XML selettivi  
 Nell'esempio seguente viene disabilitato l'indice XML selettivo nel database corrente.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'off';  
GO  
```  
  
 Nell'esempio seguente viene disabilitato l'indice XML selettivo nel database AdventureWorks2012.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'false';  
GO  
```  
  
### <a name="c-detect-if-selective-xml-index-is-enabled"></a>C. Rilevare se l'indice XML selettivo è abilitato  
 Nell'esempio seguente viene rilevato se l'indice XML selettivo è abilitato. Restituisce 1 se l'indice XML selettivo è abilitato.  
  
```  
EXECUTE sys.sp_db_selective_xml_index;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Indici XML selettivi &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)  
  
  