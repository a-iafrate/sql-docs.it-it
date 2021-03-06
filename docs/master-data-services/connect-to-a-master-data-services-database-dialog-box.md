---
title: Finestra di dialogo Connessione a un database Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.mds.configmanager.srvconnect.f1
ms.assetid: b2f8c9b9-c31e-4f0d-9095-978709423190
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 124d70b1c0696bdc47834796e82a83b03f867f4c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-a-master-data-services-database-dialog-box"></a>Finestra di dialogo Connessione a un database Master Data Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Usare la finestra di dialogo **Connessione a un database Master Data Services** per selezionare un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]è possibile accedere a questa finestra di dialogo nei modi seguenti:  
  
-   Nella pagina **Configurazione database** fare clic su **Selezione database**. Utilizzare questa finestra di dialogo per selezionare un database per il quale configurare le impostazioni del sistema.  
  
-   Nella pagina **Configurazione Web** in **Associare un'applicazione a un database**fare clic su **Seleziona** per selezionare il database da associare al sito Web o all'applicazione [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="select-database"></a>Selezione database  
 Specificare le informazioni per connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] locale o remota che ospita il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Per connettersi a un'istanza remota, è necessario che questa sia abilitata per le connessioni remote.  
  
|Nome del controllo|Description|  
|------------------|-----------------|  
|**Istanza di SQL Server**|Specificare il nome dell'istanza del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] in cui si vuole ospitare il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Può corrispondere a un'istanza predefinita o denominata in un computer locale o remoto. Specificare le informazioni digitando quanto segue:<br /><br /> Un punto (.) per connettersi all'istanza predefinita nel computer locale.<br /><br /> Il nome server o l'indirizzo IP per connettersi all'istanza predefinita nel computer locale o remoto specificato.<br /><br /> Il nome server o l'indirizzo IP, nonché il nome dell'istanza per la connessione all'istanza denominata nel computer locale o remoto specificato. Specificare le informazioni nel formato *nome_server*\\*nome_istanza*.|  
|**Tipo di autenticazione**|Selezionare il tipo di autenticazione da usare per la connessione all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] specificata. Le credenziali usate per connettersi determinano i database visualizzati nell'elenco a discesa **Database Master Data Services** .<br /><br /> Nei tipi di autenticazione sono inclusi:<br /><br /> **Utente corrente - Sicurezza integrata**: usa l'autenticazione integrata di Windows per connettersi tramite le credenziali dell'account utente di Windows corrente. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] usa le credenziali di Windows dell'utente che ha eseguito l'accesso al computer e ha aperto l'applicazione. Non è possibile specificare credenziali di Windows diverse nell'applicazione. Per connettersi con credenziali di Windows diverse, è necessario accedere al computer con il nome utente desiderato, quindi aprire [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].<br /><br /> **Account di SQL Server**: usa un account di SQL Server per la connessione. Quando si seleziona questa opzione, i campi **Nome utente** e **Password** sono abilitati ed è necessario specificare le credenziali per un account di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] specificata.|  
|**User name**|Specificare il nome dell'account utente che verrà utilizzato per connettersi all'istanza di SQL Server specificata. L'account deve far parte del ruolo **sysadmin** nell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] specificata:<br /><br /> Quando l'opzione **Tipo di autenticazione** è impostata su **Utente corrente - Sicurezza integrata**, la casella **Nome utente** è di sola lettura e visualizza il nome dell'account utente di Windows usato per l'accesso al computer.<br /><br /> Quando l'opzione **Tipo di autenticazione** è impostata su **Account di SQL Server**, la casella **Nome utente** è abilitata ed è necessario specificare le credenziali per un account di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] specificata.|  
|**Password**|Specificare la password associata all'account utente:<br /><br /> Quando l'opzione **Tipo di autenticazione** è impostata su **Utente corrente - Sicurezza integrata**, la casella **Password** è di sola lettura e per la connessione vengono usate le credenziali dell'account utente di Windows specificato.<br /><br /> Quando l'opzione **Tipo di autenticazione** è impostata su **Account di SQL Server**, la casella **Password** è abilitata ed è necessario specificare la password associata all'account utente specificato.|  
|**Connect**|Stabilisce la connessione all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con le credenziali specificate.|  
|**Database Master Data Services**|Consente di visualizzare i database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] nell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] specificata in base ai criteri seguenti:<br /><br /> Quando l'utente è un membro del ruolo del server **sysadmin** per l'istanza specificata, vengono visualizzati tutti i database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] nell'istanza.<br /><br /> Quando l'utente è un membro del ruolo del database **db_owner** per qualsiasi database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] nell'istanza specificata, vengono visualizzati i database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br/> Per altre informazioni sui ruoli di SQL Server, vedere [Ruoli a livello di server](../relational-databases/security/authentication-access/server-level-roles.md) e [Ruoli a livello di database](../relational-databases/security/authentication-access/database-level-roles.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Pagina Configurazione database &#40;Gestione configurazione Master Data Services&#41;](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   

[Installazione e configurazione di Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)
  
  
