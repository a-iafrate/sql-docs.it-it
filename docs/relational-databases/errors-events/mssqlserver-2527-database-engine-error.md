---
title: MSSQLSERVER_2527 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2527 (Database Engine error)
ms.assetid: 1cef90ef-9c39-44e6-bc7f-316c8f53c10c
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4bdf98e0beaed65cac6cd792646bf7441ee5d4fd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver2527"></a>MSSQLSERVER_2527
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2527|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_INDEX_FILEGROUP_IS_OFFLINE|  
|Testo del messaggio|Impossibile elaborare l'indice I_NAME della tabella O_NAME perché il filegroup F_NAME è offline.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio informativo indica che non è possibile verificare l'indice perché uno dei filegroup che archivia i dati dell'indice è offline. Lo stato dei file di un filegroup determina la disponibilità dell'intero filegroup. Un filegroup è disponibile se tutti i file in esso inclusi sono online. In assenza di altri problemi, tutti gli altri indici dello stesso oggetto verranno verificati.  
  
## <a name="user-action"></a>Azione dell'utente  
Per visualizzare lo stato dei file per il filegroup specificato, eseguire una query sulla vista del catalogo **sys.database_files** o **sys.master_files**.  
  
Ripristinare il file offline da un backup.  
  
## <a name="see-also"></a>Vedere anche  
[sys.database_files &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[sys.master_files &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  
