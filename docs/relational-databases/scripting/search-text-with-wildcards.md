---
title: Eseguire ricerche di testo con caratteri jolly | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
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
f1_keywords:
- vs.wildcards
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: af619a112b08a9d964c13b9d93b3eb10079d8918
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="search-text-with-wildcards"></a>Testo di ricerca con caratteri jolly
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Caratteri o cifre nel campo **Trova** della finestra di dialogo [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Find and Replace** dialog box.  
  
#### <a name="to-search-using-wildcards"></a>Per eseguire la ricerca utilizzando caratteri jolly  
  
1.  Per consentire l'uso di caratteri jolly nel campo **Trova** durante operazioni Ricerca veloce, **Cerca nei file**, **Sostituzione veloce**o **Sostituisci nei file** , selezionare l'opzione **Utilizza** in **Opzioni di ricerca** e quindi scegliere **Caratteri jolly**.  
  
2.  Accanto al campo **Trova** viene reso disponibile il pulsante triangolare per **l'elenco dei riferimenti**. Fare clic su di esso per visualizzare l'elenco dei caratteri jolly disponibili. L'elemento scelto dall' **Elenco riferimenti**viene inserito nella stringa **Trova** .  
  
 Nella tabella seguente sono descritti i caratteri jolly disponibili nell' **Elenco riferimenti**.  
  
|Espressione|Sintassi|Description|  
|----------------|------------|-----------------|  
|Un solo carattere|?|Individua un qualsiasi singolo carattere.|  
|Una sola cifra|#|Individua una qualsiasi singola cifra. Ad esempio, 7# individua i numeri che comprendono 7 seguito da un altro numero. In questo caso potrebbe essere 71 ma non 17.|  
|Qualsiasi carattere esterno al set|[! ]|Individua qualsiasi carattere non specificato nel set.|  
|Zero o più caratteri|*|Individua uno o più caratteri. Ad esempio, nuovo* individua qualsiasi testo che comprende "nuovo", come nuovofile.txt.|  
|Qualsiasi carattere del set|[ ]|Individua qualsiasi carattere specificato nel set.|  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca e sostituzione](../../relational-databases/scripting/search-and-replace.md)   
 [Testo di ricerca con espressioni regolari](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  
