---
title: Informazioni rapide (IntelliSense) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f661c2d8c63241e97e4fbc37e348d13a4bcae624
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="quick-info-intellisense"></a>Informazioni rapide (IntelliSense)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  La funzionalità [!INCLUDE[msCoName](../../includes/msconame-md.md)] Informazioni rapide **di** IntelliSense visualizza la dichiarazione completa di qualsiasi identificatore nel codice. Quando si sposta il puntatore del mouse su un identificatore, viene visualizzata la relativa dichiarazione in una finestra popup gialla. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **Informazioni rapide** è disponibile nell'editor di query del motore di database e XML.  
  
## <a name="transact-sql-quick-info"></a>Informazioni rapide Transact-SQL  
 **Informazioni rapide** contiene due tipi di informazioni nell'editor di query [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Se non si trova in modalità debug, **Informazioni rapide** visualizza la dichiarazione dell'espressione. In modalità debug, **Informazioni rapide** visualizza invece il nome dell'espressione e il valore corrente.  
  
 Nell'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , la funzionalità **Informazioni rapide** è disponibile solo per quelle parti di sintassi [!INCLUDE[tsql](../../includes/tsql-md.md)] che sono supportate da IntelliSense. Ad esempio, se si sposta il puntatore del mouse sull'identificatore di un oggetto che dispone di un tipo di dati non supportato da IntelliSense, la finestra popup **Informazioni rapide** conterrà un messaggio indicante che il tipo di dati non è supportato.  
  
## <a name="see-also"></a>Vedere anche  
 [Sintassi Transact-SQL supportata da IntelliSense](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md)  
  
  
