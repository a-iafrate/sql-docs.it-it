---
title: Convalida sottoscrizione | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.rep.validate.validateandresynch.f1
helpviewer_keywords:
- Validate Subscription dialog box
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9c95d9f51b284f0940526528e122e5d58c9ebd8e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="validate-subscription"></a>Convalida sottoscrizione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilizzare la finestra di dialogo **Convalida sottoscrizione** per specificare che una sottoscrizione di una pubblicazione di tipo merge deve essere convalidata alla successiva esecuzione dell'agente di merge per la sottoscrizione. I risultati della convalida vengono visualizzati in Monitoraggio replica. Per altre informazioni, vedere [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
 Per convalidare tutte le sottoscrizioni di una pubblicazione di tipo merge è inoltre possibile fare clic con il pulsante destro del mouse su una pubblicazione in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e scegliere **Convalida tutte le sottoscrizioni**.  
  
## <a name="options"></a>Opzioni  
 **Data ultimo tentativo di convalida**  
 Data dell'ultima sessione dell'agente di merge che prevedeva la convalida della sottoscrizione, indipendentemente dal fatto che la convalida sia stata completata o meno.  
  
 **Data ultima convalida**  
 Data dell'ultima sessione dell'agente di merge che prevedeva una convalida della sottoscrizione completata.  
  
 **Convalida la sottoscrizione**  
 Selezionare questa opzione per convalidare la sottoscrizione.  
  
 **Opzioni**  
 Fare clic su questo pulsante per accedere alla finestra di dialogo **Opzioni di convalida delle sottoscrizioni** nella quale è possibile specificare se utilizzare la convalida mediante il conteggio delle righe oppure la convalida mediante checksum binario.  
  
## <a name="see-also"></a>Vedere anche  
 [Convalidare i dati replicati](../../relational-databases/replication/validate-replicated-data.md)  
  
  
