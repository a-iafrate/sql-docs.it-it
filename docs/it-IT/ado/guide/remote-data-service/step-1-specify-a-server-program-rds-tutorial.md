---
title: "Passaggio 1: Specificare un'applicazione Server (esercitazione su RDS) | Documenti Microsoft"
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], specifying server program
ms.assetid: d8bb35b1-c02a-4231-8d55-016e56e53b95
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2acdd9c143ebedfc8af600e09b4791fca1620350
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="step-1-specify-a-server-program-rds-tutorial"></a>Passaggio 1: Specificare un'applicazione Server (esercitazione di servizi desktop remoto)
Nel caso più generale, utilizzare il [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) oggetto [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) per specificare il programma server predefinito, [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), o un'applicazione server personalizzata (oggetto business). Viene creata un'istanza di un programma server nel server e un riferimento all'applicazione server, o *proxy*, viene restituito.  
  
 Questa esercitazione viene utilizzato il programma server predefinito:  
  
```  
Sub RDSTutorial1()  
   Dim DS as New RDS.DataSpace  
   Dim DF as Object  
   Set DF = DS.("RDSServer.DataFactory", "http://yourServer")  
...  
```  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Vedere anche  
 [Passaggio 2: Richiamare il programma di Server (esercitazione di servizi desktop remoto)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)   
 [Esercitazione su RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   