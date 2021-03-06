---
title: Gruppi di disponibilità con scalabilità in lettura | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: availability-groups
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ''
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 727fbed9301389f740b112bc3fec3fcdf8767052
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="read-scale-availability-groups"></a>Gruppi di disponibilità con scalabilità in lettura
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Un gruppo di disponibilità è una soluzione completa che offre funzionalità a disponibilità elevata per SQL Server e anche soluzioni di scalabilità integrate. In un'applicazione di database tipica, diversi client eseguono vari tipi di carichi di lavoro. In alcuni casi a causa dei vincoli di risorse possono verificarsi dei colli di bottiglia. È possibile liberare risorse e ottenere una velocità effettiva maggiore per il carico di lavoro OLTP. È anche possibile offrire migliori prestazioni e maggior scalabilità per i carichi di lavoro di sola lettura. Sfruttare la tecnologia di replica più veloce per SQL Server, creando un gruppo di database replicati per allocare i carichi di lavoro di creazione report e analisi alle repliche di sola lettura. 

Con i gruppi di disponibilità è possibile configurare una o più repliche secondarie per supportare l'accesso in sola lettura ai database secondari.

Le applicazioni client che eseguono carichi di lavoro di analisi e report possono connettersi direttamente ai database secondari. È anche possibile impostare un elenco di routing di sola lettura e collegarlo al database primario. La richiesta di connessione viene inoltrata a ogni replica secondaria dell'elenco di routing in base a uno schema round-robin.

## <a name="read-scale-availability-groups-without-cluster"></a>Gruppi di disponibilità con scalabilità in lettura senza cluster

In [!INCLUDE[sssql15-md](..\..\..\includes\sssql15-md.md)] e versioni precedenti tutti i gruppi di disponibilità richiedevano un cluster. Il cluster garantiva una continuità operativa per disponibilità elevata e ripristino di emergenza (HADR). Le repliche secondarie venivano anche configurate per le operazioni di lettura. Se l'obiettivo non era la disponibilità elevata la configurazione e gestione di un cluster comportava un notevole sovraccarico operativo. SQL Server 2017 introduce i gruppi di disponibilità con scalabilità in lettura senza cluster. 

Se i requisiti operativi prevedono di risparmiare risorse orientandole sui carichi di lavoro di importanza critica in esecuzione nella replica primaria, ora è possibile usare il routing di sola lettura o connettersi direttamente a repliche secondarie leggibili. Non più necessario dipendere dall'integrazione con le tecnologie di clustering. Queste nuove funzionalità sono disponibili per SQL Server 2017 in esecuzione su piattaforme Windows e Linux.

>[!IMPORTANT]
>Non si tratta di un'installazione a disponibilità elevata. Non ci sono infrastrutture per monitorare e coordinare il rilevamento degli errori e il failover automatico. Senza cluster, SQL Server non può offrire l'obiettivo di tempo di ripristino ridotto (RTO, Recovery Time Objective) garantito da una soluzione a disponibilità elevata automatica. Se sono necessarie funzionalità di disponibilità elevata, usare un modulo di gestione cluster (Gestione cluster di failover in Windows Server o Pacemaker in Linux). 
>
>Il gruppo di disponibilità per la scalabilità in lettura può offrire funzionalità di ripristino di emergenza. Quando le repliche di sola lettura si trovano in modalità con commit sincrono garantiscono un obiettivo del punto di ripristino (RPO, Recovery Point Objective) pari a zero. Per eseguire il failover di un gruppo di disponibilità per la scalabilità in lettura, vedere [Fail over the primary replica on a read-scale availability group](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md#ReadScaleOutOnly) (Eseguire il failover della replica primaria in un gruppo di disponibilità per scalabilità in lettura).

## <a name="use-distributed-availability-groups-for-geographic-read-scale"></a>Usare gruppi di disponibilità distribuiti per la scalabilità in lettura a livello geografico

Soluzioni separate geograficamente possono implementare soluzioni con scalabilità in lettura con gruppi di disponibilità distribuiti. È possibile usarle per ripartire i carichi di lavoro di lettura dalla replica primaria alle repliche secondarie leggibili nei siti più vicini all'origine dei carichi di lavoro di lettura. I gruppi di disponibilità distribuiti riducono l'uso di risorse nella replica primaria. Incrementano anche la velocità effettiva di lettura riducendo la latenza di rete e sfruttando risorse dedicate.

Un singolo gruppo di disponibilità distribuito può avere fino a 17 repliche secondarie leggibili. Per accrescere la capacità di scalabilità, è possibile connettere a cascata più gruppi di disponibilità per aumentare ulteriormente il numero di repliche leggibili. È anche possibile implementare due gruppi di disponibilità distribuiti dallo stesso gruppo di disponibilità per letture a bassa latenza in ambienti dislocati in località geografiche diverse.




## <a name="next-steps"></a>Passaggi successivi 

[Configurare un gruppo di disponibilità con scalabilità in lettura per Linux](../../../linux/sql-server-linux-availability-group-configure-rs.md)

## <a name="see-also"></a>Vedere anche 
 [Panoramica di Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) 
  
  
