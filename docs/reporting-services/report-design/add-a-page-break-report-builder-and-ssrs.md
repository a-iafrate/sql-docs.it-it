---
title: Aggiungere un'interruzione di pagina (Generatore report e SSRS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3846cd48-2787-47e9-b13b-7fc45a205f68
caps.latest.revision: "7"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: f264f0fc3f601ba9433f5ec591674bfa03b07779
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="add-a-page-break-report-builder-and-ssrs"></a>Aggiungere un'interruzione di pagina (Generatore report e SSRS)
  È possibile aggiungere un'interruzione di pagina a rettangoli, aree dati o gruppi all'interno di aree dati per controllare la quantità di informazioni in ogni pagina. Con l'aggiunta di interruzioni di pagina è possibile migliorare le prestazioni dei report pubblicati, perché quando si visualizza il report è necessario elaborare solo gli elementi presenti in ogni pagina. Quando l'intero report è costituito da un'unica pagina, prima che sia possibile visualizzare il report è necessario che tutti gli elementi vengano elaborati.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-break-to-a-data-region"></a>Per aggiungere un'interruzione di pagina a un'area dati  
  
1.  Nell'area di progettazione fare clic con il pulsante destro del mouse sull'handle d'angolo dell'area dati, quindi scegliere **Proprietà Tablix**.  
  
2.  Nella scheda **Generale** , in **Opzioni di interruzione pagina**, selezionare una delle opzioni seguenti:  
  
    -   **Aggiungi un'interruzione di pagina prima**. Selezionare questa opzione se si desidera aggiungere un'interruzione di pagina prima della tabella.  
  
    -   **Aggiungi un'interruzione di pagina dopo**. Selezionare questa opzione se si desidera aggiungere un'interruzione di pagina dopo la tabella.  
  
    -   **Riduci tabella a una sola pagina se possibile**. Selezionare questa opzione se si desidera adattare i dati in un'unica pagina.  
  
### <a name="to-add-a-page-break-to-a-rectangle"></a>Per aggiungere un'interruzione di pagina a un rettangolo  
  
1.  Nell'area di progettazione fare clic con il pulsante destro del mouse sul rettangolo in cui si desidera aggiungere un'interruzione di pagina, quindi scegliere **Proprietà rettangolo**.  
  
2.  Nella scheda **Generale** , in **Opzioni di interruzione pagina**, selezionare una delle opzioni seguenti:  
  
    -   **Aggiungi un'interruzione di pagina prima**. Selezionare questa opzione se si desidera aggiungere un'interruzione di pagina prima del rettangolo.  
  
    -   **Aggiungi un'interruzione di pagina dopo**. Selezionare questa opzione se si desidera aggiungere un'interruzione di pagina dopo il rettangolo.  
  
    -   **Ometti bordo sull'interruzione di pagina**. Selezionare questa opzione se non si desidera aggiungere un bordo sull'interruzione di pagina.  
  
    -   **Mantieni contenuto in una singola pagina, se possibile**. Selezionare questa opzione se si desidera che il contenuto del rettangolo occupi una sola pagina.  
  
### <a name="to-add-a-page-break-to-a-row-group-in-a-table-matrix-or-list"></a>Per aggiungere un'interruzione di pagina a un gruppo di righe in una tabella, in una matrice o in un elenco  
  
1.  Nel riquadro Raggruppamento fare clic con il pulsante destro del mouse sul gruppo di righe, quindi scegliere **Proprietà gruppo**.  
  
    > [!NOTE]  
    >  Le interruzioni di pagina relative a gruppi di colonne vengono ignorate.  
  
2.  Nella scheda **Interruzioni di pagina** selezionare **Tra ogni istanza di un gruppo** per aggiungere un'interruzione di pagina tra ogni istanza di un gruppo nella tabella.  
  
3.  Facoltativamente, selezionare **Anche all'inizio di un gruppo** o **Anche alla fine di un gruppo** per specificare che un'interruzione di pagina deve essere aggiunta all'inizio o alla fine di un gruppo nella tabella.  
  
## <a name="see-also"></a>Vedere anche  
 [Paginazione in Reporting Services &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Tipi di rendering &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Intestazioni di pagina e piè di pagina &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
