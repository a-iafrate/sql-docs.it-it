---
title: plan_guides (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.planguides_TSQL
- plan_guides
- sys.planguides
- plan_guides_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.plan_guides catalog view
ms.assetid: 3dde0397-ef6f-4b3f-8250-3f25584eb62b
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4309a55a8c0b631cd1e5f49d6601bfba30245178
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysplanguides-transact-sql"></a>sys.plan_guides (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contiene una riga per ogni guida di piano nel database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**plan_guide_id**|**int**|Identificatore univoco della guida di piano nel database.|  
|**name**|**sysname**|Nome della guida di piano.|  
|**create_date**|**datetime**|Data e ora di creazione della guida di piano.|  
|**modify_date**|**DateTime**|Data dell'ultima modifica della guida di piano.|  
|**is_disabled**|**bit**|1 = La guida di piano è disabilitata.<br /><br /> 0 = La guida di piano è abilitata.|  
|**query_text**|**nvarchar(max)**|Testo della query in cui è stata creata la guida di piano.|  
|**scope_type**|**tinyint**|Identifica l'ambito della guida di piano.<br /><br /> 1 = OBJECT<br /><br /> 2 = SQL<br /><br /> 3 = TEMPLATE|  
|**scope_type_desc**|**nvarchar(60)**|Descrizione dell'ambito della guida di piano.<br /><br /> OBJECT<br /><br /> SQL<br /><br /> TEMPLATE|  
|**scope_object_id**|**Int**|object_id dell'oggetto che definisce l'ambito della guida di piano, se l'ambito è OBJECT.<br /><br /> NULL se la guida di piano non è definita a livello di ambito di OBJECT.|  
|**scope_batch**|**nvarchar(max)**|Testo batch, se **scope_type** è SQL.<br /><br /> NULL se il tipo di batch non è SQL.<br /><br /> Se è NULL e **scope_type** è SQL, il valore di **query_text** si applica.|  
|**parameters**|**nvarchar(max)**|Stringa che definisce l'elenco dei parametri associati alla guida di piano.<br /><br /> NULL = Nessun elenco di parametri è associato alla guida di piano.|  
|**suggerimenti**|**nvarchar(max)**|Hint della clausola OPTION associati alla guida di piano.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
