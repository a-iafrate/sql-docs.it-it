---
title: Requisiti hardware e Software (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hardware requirements [ODBC], desktop database drivers
- software requirements [ODBC], desktop database drivers
- system requirements [ODBC], desktop database drivers
- requirements [ODBC], desktop database drivers
ms.assetid: 6df2e9cd-de10-4629-97bd-32f2782616c7
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45bea6f16f079367caeb36b42370c87e1885c56b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="hardware-and-software-requirements-odbc"></a>Requisiti hardware e Software (ODBC)
In questo argomento sono elencati i requisiti per l'utilizzo di driver di Database Desktop ODBC.  
  
## <a name="hardware-requirements"></a>Requisiti hardware  
 Per utilizzare i driver di Database ODBC Desktop, è necessario disporre di:  
  
-   Un PC IBM compatibile.  
  
-   Un disco rigido con 6 MB di spazio libero su disco.  
  
-   Almeno 16 MB di memoria (RAM).  
  
## <a name="software-requirements"></a>Requisiti software  
 Per accedere ai dati tramite un driver ODBC, è necessario disporre di:  
  
-   Il driver ODBC.  
  
-   32 bit gestione Driver ODBC, versione 3.51 o versioni successive (Odbc32.dll).  
  
-   Microsoft Windows 95 o versioni successive o Windows NT 4.0 o Windows 2000.  
  
-   Una dimensione dello stack di almeno 20 KB per un'applicazione tramite un driver ODBC di Microsoft.  
  
 Quando si utilizza Microsoft Windows NT 4.0 o Windows 2000, il driver a 32 bit è thread-safe, ma solo tramite l'utilizzo di un semaforo globale che controlla l'accesso al driver. È molto limitato simultanea utilizzo del driver in Windows NT. Tutti gli accessi al livello Jet ISAM sarà a thread singolo per tutte le applicazioni di gestione Microsoft Jet.  
  
 Quando si esegue più applicazioni a 16 bit in Windows on Windows (WOW) in Microsoft Windows NT 4.0, è necessario eseguire le applicazioni in spazi di memoria separati. (Lo stesso spazio di memoria non può essere utilizzato poiché ODBC non supporta più ambienti nello stesso processo.) Per eseguire un'applicazione in uno spazio di memoria separate, selezionare l'icona dell'applicazione in Program Manager, aprire il **File** menu e fare clic su **proprietà**, quindi fare clic su **eseguito In memoria separata Spazio**.  
  
 L'utilizzo di questi driver per applicazioni a 16 bit in Windows 95 non è supportato.  
  
## <a name="driver-specific-hardware-and-software-requirements"></a>Requisiti Hardware specifici del driver e Software  
  
-   Il MicrosoftAccess e dBASEdrivers può richiedere modifiche nei file di Autoexec.bat o Sys.
