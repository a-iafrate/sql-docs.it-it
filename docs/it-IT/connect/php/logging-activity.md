---
title: Attività di registrazione | Documenti Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- logging activity
ms.assetid: a777b3d9-2262-4e82-bc82-b62ad60d0e55
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc425ab4034715c158799b731016373ce2c16caa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="logging-activity"></a>Attività di registrazione
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Per impostazione predefinita, gli errori e gli avvisi generati dai [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] non vengono registrati. In questo argomento viene illustrato come configurare l'attività di registrazione.  
  
## <a name="logging-activity-using-the-pdosqlsrv-driver"></a>Attività di registrazione con il driver PDO_SQLSRV  
La sola configurazione disponibile per il driver PDO_SQLSRV è la voce pdo_sqlsrv.log_severity nel file php.ini.  
  
Aggiungere quanto segue alla fine del file php.ini:  
  
```  
[pdo_sqlsrv]  
pdo_sqlsrv.log_severity = <number>  
```  
  
**log_severity** può essere uno dei valori seguenti:  
  
|Value|Descrizione|  
|---------|---------------|  
|0|La registrazione è disabilitata (impostazione predefinita se non viene definita alcuna impostazione).|  
|-1|Specifica che vengono registrate errori, avvisi e notifiche.|  
|1|Specifica che gli errori vengono registrati.|  
|2|Specifica che vengono registrati gli avvisi.|  
|4|Specifica che le notifiche vengono registrate.|  
  
Le informazioni di registrazione viene aggiunto al file phperrors.  
  
PHP legge il file di configurazione durante l'inizializzazione e archivia i dati in una cache. PHP offre inoltre un'API per l'aggiornamento e l'uso di queste impostazioni che vengono scritte nel file di configurazione. Questa API consente agli script dell'applicazione di modificare le impostazioni anche dopo l'inizializzazione di PHP.  
  
## <a name="logging-activity-using-the-sqlsrv-driver"></a>Attività di registrazione con il driver SQLSRV  
Per abilitare la registrazione, è possibile usare il [sqlsrv_configure](../../connect/php/sqlsrv-configure.md) funzione oppure modificare il file PHP. ini. È possibile registrare l'attività durante l'inizializzazione, la connessione, le istruzioni o le funzioni di errore. È inoltre possibile specificare se registrare errori, avvisi, notifiche o tutti e tre.  
  
> [!NOTE]  
> Il percorso del file di log può essere specificato nel file php.ini.  
  
### <a name="turning-logging-on"></a>Attivazione della registrazione  
È possibile abilitare la registrazione tramite il [sqlsrv_configure](../../connect/php/sqlsrv-configure.md) funzione per specificare un valore per il **LogSubsystems** impostazione. Ad esempio, la riga di codice seguente consente di configurare il driver per la registrazione dell'attività durante le connessioni:  
  
`sqlsrv_configure("LogSubsystems", SQLSRV_LOG_SYSTEM_CONN);`  
  
Nella tabella seguente sono descritte le costanti che possono essere usate come valore dell'impostazione **LogSubsystems** :  
  
|Valore (intero equivalente tra parentesi)|Description|  
|-----------------------------------------------|---------------|  
|SQLSRV_LOG_SYSTEM_ALL (-1)|Attiva la registrazione di tutti i sottosistemi.|  
|SQLSRV_LOG_SYSTEM_OFF (0)|Disattiva la registrazione. Impostazione predefinita.|  
|SQLSRV_LOG_SYSTEM_INIT (1)|Attiva la registrazione dell'attività di inizializzazione.|  
|SQLSRV_LOG_SYSTEM_CONN (2)|Attiva la registrazione dell'attività di connessione.|  
|SQLSRV_LOG_SYSTEM_STMT (4)|Attiva la registrazione delle attività delle istruzioni.|  
|SQLSRV_LOG_SYSTEM_UTIL (8)|Attiva la registrazione delle attività delle funzioni di errore, ad esempio handle_error e handle_warning.|  
  
È possibile impostare più valori contemporaneamente per il **LogSubsystems** impostazione mediante l'operatore logico OR (|). Ad esempio, la riga di codice seguente attiva la registrazione dell'attività delle connessioni e delle istruzioni:  
  
`sqlsrv_configure("LogSubsystems", SQLSRV_LOG_SYSTEM_CONN | SQLSRV_LOG_SYSTEM_STMT);`  
  
È inoltre possibile abilitare la registrazione specificando un valore intero per il **LogSubsystems** nel file PHP. ini. Ad esempio, aggiungendo la riga seguente al `[sqlsrv]` sezione del file PHP. ini attiva la registrazione dell'attività di connessione:  
  
`sqlsrv.LogSubsystems = 2`  
  
Sommando i valori interi è possibile specificare più opzioni alla volta. Ad esempio, aggiungendo la riga seguente al `[sqlsrv]` sezione del file PHP. ini attiva la registrazione dell'attività di connessione e delle istruzioni:  
  
`sqlsrv.LogSubsystems = 6`  
  
### <a name="logging-errors-warnings-and-notices"></a>Registrazione di errori, avvisi e notifiche  
Dopo aver attivato la registrazione, è necessario specificare gli elementi da registrare. È possibile registrare uno o più degli elementi seguenti: errori, avvisi e notifiche. Ad esempio, la riga di codice seguente specifica che vengono registrati solo gli avvisi:  
  
`sqlsrv_configure("LogSeverity", SQLSRV_LOG_SEVERITY_WARNING);`  
  
> [!NOTE]  
> L'impostazione predefinita per **LogSeverity** è **SQLSRV_LOG_SEVERITY_ERROR**. Se la registrazione è attivata e non viene specificata alcuna impostazione per **LogSeverity** , vengono registrati solo gli errori.  
  
Nella tabella seguente sono descritte le costanti che possono essere usate come valore dell'impostazione **LogSeverity** :  
  
|Valore (intero equivalente tra parentesi)|Description|  
|-----------------------------------------------|---------------|  
|SQLSRV_LOG_SEVERITY_ALL (-1)|Specifica che vengono registrate errori, avvisi e notifiche.|  
|SQLSRV_LOG_SEVERITY_ERROR (1)|Specifica che gli errori vengono registrati. Impostazione predefinita.|  
|SQLSRV_LOG_SEVERITY_WARNING (2)|Specifica che vengono registrati gli avvisi.|  
|SQLSRV_LOG_SEVERITY_NOTICE (4)|Specifica che le notifiche vengono registrate.|  
  
È possibile impostare più valori contemporaneamente per il **LogSeverity** impostazione mediante l'operatore logico OR (|). Ad esempio, la riga di codice seguente specifica la registrazione di errori e avvisi:  
  
`sqlsrv_configure("LogSeverity", SQLSRV_LOG_SEVERITY_ERROR | SQLSRV_LOG_SEVERITY_WARNING);`  
  
> [!NOTE]  
> Se si specifica un valore per il **LogSeverity** non attiva la registrazione. È necessario attivare la registrazione specificando un valore per il **LogSubsystems** , quindi specificare il livello di gravità degli elementi registrati impostando un valore per **LogSeverity**.  
  
È inoltre possibile specificare un'impostazione per **LogSeverity** mediante valori interi nel file php.ini. Ad esempio, aggiungendo la seguente riga alla sezione `[sqlsrv]` del file php.ini verrà attivata solo la registrazione degli avvisi:  
  
`sqlsrv.LogSeverity = 2`  
  
Sommando i valori interi è possibile specificare più opzioni alla volta. Ad esempio, aggiungendo la riga seguente al `[sqlsrv]` sezione del file PHP. ini consente la registrazione degli errori e avvisi:  
  
`sqlsrv.LogSeverity = 3`  
  
## <a name="see-also"></a>Vedere anche  
[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Costanti &#40;driver Microsoft per PHP per SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)

[sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md)

[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  
