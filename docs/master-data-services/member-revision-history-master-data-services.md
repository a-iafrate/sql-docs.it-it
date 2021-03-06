---
title: Cronologia delle revisioni del membro (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
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
ms.assetid: 113069c5-12e6-48ec-b443-b42e14f77308
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2b241a2819c61b4c671c06d5622b9e30ed3f51f2
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="member-revision-history-master-data-services"></a>Cronologia delle revisioni del membro (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  La cronologia delle revisioni di un membro viene registrata ogni volta che un membro viene modificato, se il log delle transazioni delle entità è di tipo member.  
  
 Per informazioni sui tipi di log delle transazioni, vedere [Modificare il tipo di log delle transazioni dell'entità &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md).  
  
 Le cronologie delle revisioni dei membri vengono registrate quando si verificano le modifiche seguenti.  
  
-   Vengono creati, eliminati, riattivati o eliminati membri.  
  
-   Vengono modificati i valori degli attributi.  
  
-   I membri vengono spostati in una gerarchia o raccolta  
  
## <a name="view-and-manage-revision-history-by-entity"></a>Visualizzare e gestire la cronologia delle revisioni in base all'entità  
 Nell'area funzionale Visualizzatore è possibile visualizzare le revisioni per tutti i membri nell'entità. Se si hanno le autorizzazioni di aggiornamento, è possibile eseguire il rollback del membro a una revisione precedente.  
  
 **Per visualizzare e gestire la cronologia delle revisioni**  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]selezionare il modello e la versione e fare clic su **Visualizzatore**.  
  
2.  Selezionare l'entità dal menu **Entità** .  
  
3.  Fare clic su **Visualizza cronologia** per visualizzare tutti i dati cronologici dell'entità.  
  
4.  Fare clic su **Filtro** per filtrare i dati.  
  
5.  Fare clic sull'intestazione di colonna per ordinare i dati.  
  
6.  Se si hanno di autorizzazioni per l'aggiornamento, fare clic su **Ripristina membro** per eseguire il rollback alla versione selezionata.  
  
## <a name="view-and-manage-revision-history-by-member"></a>Visualizzare e gestire la cronologia delle revisioni in base al membro  
 Nell'area funzionale Visualizzatore è possibile visualizzare le revisioni per un membro se si hanno le autorizzazioni di lettura per il membro. Se si hanno le autorizzazioni di aggiornamento, è possibile eseguire il rollback del membro a una revisione precedente o aggiungere annotazioni alla revisione.  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]selezionare il modello e la versione e fare clic su **Visualizzatore**.  
  
2.  Selezionare l'entità dal menu **Entità** .  
  
3.  Selezionare il membro.  
  
4.  Fare clic su **Visualizza cronologia** nel riquadro di destra.  
  
## <a name="log-retention-setting"></a>Impostazione di conservazione dei log  
 È possibile configurare il periodo di conservazione dei dati cronologici impostando la proprietà **Conservazione log in giorni** nelle impostazioni di sistema per il database di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] e impostando **Giorni di conservazione log** quando si crea o si modifica un modello.  
  
## <a name="related-task"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Eseguire il rollback della cronologia delle revisioni del membro|[Rollback della cronologia delle revisioni del membro &#40;Master Data Services&#41;](../master-data-services/rollback-member-revision-history-master-data-services.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un modello &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md)   
 [Impostazioni di sistema &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md)  
  
  
