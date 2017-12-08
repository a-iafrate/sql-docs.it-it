---
title: srv_setcollen (API Stored procedure estesa) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_setcollen
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_setcollen
ms.assetid: 3c60f1c3-4562-463a-a259-12df172788bd
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e28b67f794e98d471eac9b7277c013ddf8065a57
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="srvsetcollen-extended-stored-procedure-api"></a>srv_setcollen (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Specifica la lunghezza in byte della data corrente di una colonna a lunghezza variabile o di una colonna che consente valori Null.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_setcollen (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
int  
len   
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *column*  
 Indica il numero della colonna per la quale viene specificata la lunghezza dei dati. Le colonne sono numerate a partire da 1.  
  
 *len*  
 Indica la lunghezza in byte dei dati della colonna. Alla lunghezza 0 corrisponde un valore Null per i dati della colonna.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Osservazioni  
 Ogni colonna della riga deve essere definita prima con **srv_describe**. La lunghezza della colonna dei dati viene impostata dall'ultima chiamata a **srv_describe** o **srv_setcollen**. Se viene modificata una riga dei dati a lunghezza variabile (dati con terminazione null), è necessario usare **srv_setcollen** per impostarli sulla nuova lunghezza prima di chiamare **srv_sendrow**. Per una colonna che consente valori Null è necessario che sia stato chiamato **srv_describe** con *desttype* impostato su un tipo di dati che consente valori Null (ad esempio SRVINTN) e che i dati Null siano stati specificati chiamando **srv_setcollen** con *len* impostato su 0. Quando si utilizza l'API Stored procedure estesa, non è possibile specificare dati di lunghezza zero.  
  
 Quando il tipo di dati della colonna è a lunghezza variabile, *len* non viene controllato. Questa funzione restituisce FAIL se chiamata per una colonna a lunghezza fissa.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [srv_describe &#40;API Stored procedure estesa&#41;](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  