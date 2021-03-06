---
title: Proprietà database (pagina Rilevamento modifiche) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d6190dde5cacb135e923684cdb5866525298c08b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="database-properties-changetracking-page"></a>Proprietà database (pagina ChangeTracking)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Utilizzare questa pagina per visualizzare o modificare le impostazioni di rilevamento delle modifiche per il database selezionato. Per altre informazioni sulle opzioni disponibili in questa pagina, vedere [Abilitare e disabilitare il rilevamento delle modifiche &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md).  
  
## <a name="options"></a>Opzioni  
 **Rilevamento delle modifiche**  
 Consente di abilitare o disabilitare il rilevamento delle modifiche per il database.  
  
 Per abilitare il rilevamento delle modifiche, è necessario disporre dell'autorizzazione per modificare il database.  
  
 L'impostazione del valore su **True** consente di impostare un'opzione del database che consente l'abilitazione del rilevamento delle modifiche nelle singole tabelle.  
  
 È anche possibile configurare il rilevamento delle modifiche usando [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md).  
  
 **Periodo di memorizzazione**  
 Specifica il periodo minimo di conservazione delle informazioni sul rilevamento delle modifiche nel database. I dati vengono rimossi solo se il valore **Pulizia automatica** è impostato su **True**.  
  
 Il valore predefinito è 2.  
  
 **Unità di misura del periodo di memorizzazione**  
 Specifica le unità di misura per il valore Periodo di memorizzazione. È possibile selezionare **Giorni**, **Ore**o **Minuti**. Il valore predefinito è **Giorni**.  
  
 Il periodo di memorizzazione minimo è 1 minuto. Non esiste un periodo di memorizzazione massimo.  
  
 **Pulizia automatica**  
 Indica se le informazioni di rilevamento delle modifiche vengono rimosse automaticamente una volta trascorso il periodo di memorizzazione specificato.  
  
 L'abilitazione di **Pulizia automatica** reimposta i precedenti periodi di memorizzazione personalizzati al periodo di memorizzazione predefinito di 2 giorni.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
