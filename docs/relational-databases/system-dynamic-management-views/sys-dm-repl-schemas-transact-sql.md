---
title: sys.dm_repl_schemas (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_repl_schemas_TSQL
- dm_repl_schemas
- sys.dm_repl_schemas_TSQL
- sys.dm_repl_schemas
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_schemas dynamic management function
ms.assetid: 6f5fefff-8492-4360-bd5b-a97287367914
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3d5b3d67de25a1ae13c2a5f9649b5604db051144
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmreplschemas-transact-sql"></a>sys.dm_repl_schemas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle colonne di tabella pubblicate dalla replica.  
  
 
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**artcache_schema_address**|**varbinary(8)**|Indirizzo in memoria della struttura dello schema nella cache per l'articolo di tabella pubblicato.|  
|**tabid**|**bigint**|ID della tabella replicata.|  
|**IndexID**|**smallint**|ID di un indice cluster nella tabella pubblicata.|  
|**idSch**|**bigint**|ID dello schema di tabella.|  
|**tabschema**|**nvarchar(510)**|Nome dello schema di tabella.|  
|**ccTabschema**|**smallint**|Lunghezza in caratteri dello schema di tabella.|  
|**TabName**|**nvarchar(510)**|Nome della tabella pubblicata.|  
|**ccTabname**|**smallint**|Lunghezza in caratteri del nome della tabella pubblicata.|  
|**rowsetid_delete**|**bigint**|ID della riga eliminata.|  
|**rowsetid_insert**|**bigint**|ID della riga inserita.|  
|**num_pk_cols**|**int**|Numero di colonne chiave primaria.|  
|**pcitee**|**binary(8000)**|Puntatore alla struttura dell'espressione di query utilizzato per valutare la colonna calcolata.|  
|**re_numtextcols**|**int**|Numero di colonne BLOB nella tabella replicata.|  
|**re_schema_lsn_begin**|**binary(8000)**|Numero di sequenza iniziale del file di log (LSN) della registrazione della versione dello schema.|  
|**re_schema_lsn_end**|**binary(8000)**|LSN finale della registrazione della versione dello schema.|  
|**re_numcols**|**int**|Numero di colonne pubblicate.|  
|**re_colid**|**int**|Identificatore di colonna nel server di pubblicazione.|  
|**re_awcName**|**nvarchar(510)**|Nome della colonna pubblicata.|  
|**re_ccName**|**smallint**|Numero di caratteri nel nome di colonna.|  
|**re_pk**|**tinyint**|Indica se la colonna pubblicata appartiene a una chiave primaria.|  
|**re_unique**|**tinyint**|Indica se la colonna pubblicata appartiene a un indice univoco.|  
|**re_maxlen**|**smallint**|Lunghezza massima della colonna pubblicata.|  
|**re_prec**|**tinyint**|Precisione della colonna pubblicata.|  
|**re_scale**|**tinyint**|Scala della colonna pubblicata.|  
|**re_collatid**|**bigint**|ID di regole di confronto per la colonna pubblicata.|  
|**re_xvtype**|**smallint**|Tipo di colonna pubblicata.|  
|**re_offset**|**smallint**|Offset della colonna pubblicata.|  
|**re_bitpos**|**tinyint**|Posizione dei bit della colonna pubblicata nel vettore di byte.|  
|**re_fNullable**|**tinyint**|Specifica se la colonna pubblicata ammette valori NULL.|  
|**re_fAnsiTrim**|**tinyint**|Specifica se nella colonna pubblicata viene utilizzata la rimozione di spazi ANSI.|  
|**re_computed**|**smallint**|Specifica se la colonna pubblicata è una colonna calcolata.|  
|**se_rowsetid**|**bigint**|ID del set di righe.|  
|**se_schema_lsn_begin**|**binary(8000)**|LSN iniziale della registrazione della versione dello schema.|  
|**se_schema_lsn_end**|**binary(8000)**|LSN finale della registrazione della versione dello schema.|  
|**se_numcols**|**int**|Numero di colonne.|  
|**se_colid**|**int**|ID della colonna nel Sottoscrittore.|  
|**se_maxlen**|**smallint**|Lunghezza massima della colonna.|  
|**se_prec**|**tinyint**|Precisione della colonna.|  
|**se_scale**|**tinyint**|Scala della colonna.|  
|**se_collatid**|**bigint**|ID di regole di confronto per la colonna.|  
|**se_xvtype**|**smallint**|Tipo di colonna.|  
|**se_offset**|**smallint**|Offset della colonna.|  
|**se_bitpos**|**tinyint**|Posizione dei bit della colonna nel vettore di byte.|  
|**se_fNullable**|**tinyint**|Specifica se la colonna ammette valori NULL.|  
|**se_fAnsiTrim**|**tinyint**|Specifica se nella colonna viene utilizzata la rimozione di spazi ANSI.|  
|**se_computed**|**smallint**|Specifica se la colonna è una colonna calcolata.|  
|**se_nullBitInLeafRows**|**int**|Specifica se il valore di colonna è NULL.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW DATABASE STATE nel database di pubblicazione per chiamare **dm_repl_schemas**.  
  
## <a name="remarks"></a>Osservazioni  
 Vengono restituite informazioni solo per gli oggetti di database replicati caricati nella cache dell'articolo di replica.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative alle repliche &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  

