---
title: Sys. syscomments (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.syscomments_TSQL
- syscomments
- syscomments_TSQL
- sys.syscomments
dev_langs: TSQL
helpviewer_keywords:
- sys.syscomments compatibility view
- syscomments system table
ms.assetid: 767dd410-6bc9-4c4a-ab0f-6d2cf6163426
caps.latest.revision: "53"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5c9b5a5269025f6ed9c3bed493b71a6be557dc25
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="syssyscomments-transact-sql"></a>sys.syscomments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene voci per ogni vista, regola, valore predefinito, trigger, vincolo CHECK, vincolo DEFAULT e stored procedure all'interno di un database. Il **testo** colonna contiene le istruzioni di definizione SQL originali.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] È consigliabile utilizzare in alternativa i moduli sys.sql. Per ulteriori informazioni, vedere [Sys. sql_modules &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID di oggetto a cui si riferisce il testo.|  
|**numero**|**smallint**|Numero all'interno del gruppo di procedure, se raggruppate.<br /><br /> 0 = Le voci immesse non sono procedure.|  
|**colid**|**smallint**|Numero di sequenza di riga per definizioni di oggetto con più di 4.000 caratteri.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**CTEXT**|**varbinary (8000)**|Byte non elaborati dell'istruzione di definizione SQL.|  
|**textType**|**smallint**|0 = Commento fornito dall'utente.<br /><br /> 1 = Commento fornito dal sistema.<br /><br /> 4 = Commento crittografato.|  
|**lingua**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**crittografato**|**bit**|Indica se la definizione della stored procedure è offuscata.<br /><br /> 0 = Non offuscata<br /><br /> 1 = Offuscata<br /><br /> **\*\*Importante \* \***  per offuscare le definizioni delle stored procedure, utilizzare CREATE PROCEDURE con la parola chiave di crittografia.|  
|**compresso**|**bit**|Restituisce sempre 0. Indica che la procedura è compressa.|  
|**text**|**nvarchar(4000)**|Testo effettivo dell'istruzione di definizione SQL.<br /><br /> La semantica dell'espressione decodificata è equivalente al testo originale, tuttavia non è garantito che la sintassi venga mantenuta. Gli spazi vuoti vengono ad esempio eliminati dall'espressione decodificata.<br /><br /> Questo [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-vista compatibile Ottiene informazioni dalle corrente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] strutture e può restituire più caratteri di **nvarchar (4000)** definizione. **sp_help** restituisce **nvarchar (4000)** come tipo di dati della colonna di testo. Quando si lavora con **syscomments** utilizzare **nvarchar (max)**. Per i nuovi progetti di sviluppo, non utilizzare **syscomments**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema di viste di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  