---
title: Disabilitare Resource Governor | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: resource-governor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7ecea90f11a2abab6277ef6b615a27edb019d92a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="disable-resource-governor"></a>Disabilitare Resource Governor
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  È possibile disabilitare Resource Governor tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o Transact-SQL.  
  
-   **Prima di iniziare:**  [Limitazioni e restrizioni](#LimitationsRestrictions), [Autorizzazioni](#Permissions)  
  
-   **Per disabilitare Resource Governor usando:**  [Esplora oggetti](#RGOffObjEx), [Proprietà di Resource Governor](#RGOffProp), [Transact-SQL](#RGOffTSQL)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
 La disabilitazione di Resource Governor comporta i risultati riportati di seguito:  
  
-   La funzione di classificazione non viene eseguita.  
  
-   Tutte le nuove connessioni vengono classificate automaticamente nel gruppo di carico di lavoro predefinito.  
  
-   Le richieste avviate dal sistema vengono classificate nel gruppo di carico di lavoro interno.  
  
-   Tutte le impostazioni del gruppo del carico di lavoro e del pool di risorse esistenti vengono reimpostate ai valori predefiniti. In questo caso non viene generato alcun evento quando vengono raggiunti i limiti.  
  
-   Il normale monitoraggio del sistema non viene modificato.  
  
-   Le modifiche alla configurazione non hanno effetto fino all'abilitazione di Resource Governor.  
  
-   Al riavvio di SQL Server, non verrà caricata la configurazione di Resource Governor, ma solo i gruppi di carico di lavoro e i pool di risorse interni e predefiniti.  
  
###  <a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
 Non è possibile usare l'istruzione **ALTER RESOURCE GOVERNOR** per disabilitare Resource Governor in una transazione utente.  
  
###  <a name="Permissions"></a> Permissions  
 Per disabilitare Resource Governor è necessaria l'autorizzazione CONTROL SERVER.  
  
##  <a name="RGOffObjEx"></a> Disabilitare Resource Governor utilizzando Esplora oggetti  
 **Per disabilitare Resource Governor utilizzando Esplora oggetti**  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire Esplora oggetti ed espandere in modo ricorsivo il nodo **Gestione** fino a **Resource Governor**.  
  
2.  Fare clic con il pulsante destro del mouse su **Resource Governor**, quindi su **Disabilita**.  
  
##  <a name="RGOffProp"></a> Disabilitare Resource Governor utilizzando Proprietà di Resource Governor  
 **Per disabilitare Resource Governor utilizzando la pagina Proprietà di Resource Governor**  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire Esplora oggetti ed espandere in modo ricorsivo il nodo **Gestione** fino a **Resource Governor**.  
  
2.  Fare clic con il pulsante destro del mouse su **Resource Governor** , quindi fare clic su **Proprietà**. In questo modo viene aperta la pagina **Proprietà di Resource Governor** .  
  
3.  Fare clic sulla casella di controllo **Abilita Resource Governor** , assicurarsi che la casella non sia selezionata, quindi fare clic su **OK**.  
  
##  <a name="RGOffTSQL"></a> Disabilitare Resource Governor utilizzando Transact-SQL  
 **Per disabilitare Resource Governor utilizzando Transact-SQL**  
  
1.  Eseguire l'istruzione **ALTER RESOURCE GOVERNOR DISABLE** .  
  
### <a name="example-transact-sql"></a>Esempio (Transact-SQL)  
 Nell'esempio seguente viene abilitato Resource Governor.  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Abilitare Resource Governor](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Gruppo di carico di lavoro di Resource Governor](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Funzione di classificazione di Resource Governor](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
