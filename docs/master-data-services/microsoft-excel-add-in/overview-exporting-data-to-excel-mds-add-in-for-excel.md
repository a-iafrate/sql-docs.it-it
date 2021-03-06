---
title: 'Panoramica: Esportazione dei dati in Excel (componente aggiuntivo MDS per Excel) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: microsoft-excel-add-in
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8efeac0ce5df99707f1b9d22ecfea1398b4e158f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="overview-exporting-data-to-excel-mds-add-in-for-excel"></a>Panoramica: Esportazione dei dati in Excel (componente aggiuntivo MDS per Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]è necessario esportare i dati dal repository MDS in un foglio di lavoro di Excel attivo prima di poterli usare. Dopo aver lavorato con i dati, importarli nel repository MDS per consentire ad altri utenti di condividerli.  
  
 È possibile esportare solo i dati per i quali si dispone dell'autorizzazione di accesso. L'autorizzazione di accesso ai dati viene impostata nell'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] o impostata a livello di programmazione.  
  
 Quando si esportano grandi quantità di dati, è possibile impostare la visualizzazione di avvisi nel caso sia necessario molto tempo per il caricamento. A tale scopo, nel gruppo **Opzioni** fare clic su **Impostazioni**. Nella scheda **Dati** selezionare **Visualizza avviso di filtro per grandi set di dati**.  
  
> [!WARNING]  
>  Una cartella di lavoro abilitata per MDS deve essere aperta e aggiornata solo in Excel con il componente aggiuntivo MDS per Excel. L'apertura di una cartella di lavoro abilitata per MDS in Excel su un computer nel quale non è installato il componente aggiuntivo Excel di MDS non è supportata e potrebbe provocare danni al file della cartella di lavoro. Se si desidera condividere dati con altri utenti, inviare tramite posta elettronica un file di query di collegamento a questi ultimi, anziché salvare il foglio di lavoro e inviarlo tramite posta elettronica. Per altre informazioni sulla query, vedere [Inviare tramite posta elettronica un file di query collegamento &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/email-a-shortcut-query-file-mds-add-in-for-excel.md).  
  
## <a name="filtering-data"></a>Filtro dei dati  
 È possibile filtrare i dati prima dell'esportazione per limitare la quantità di dati da scaricare. Ciò presuppone la scelta degli attributi (colonne) da caricare, l'ordine con cui si desidera visualizzare gli attributi e i membri (righe di dati) che si desidera utilizzare. Per altre informazioni, vedere [Filtrare i dati prima dell'esportazione &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Connettersi automaticamente e caricare i dati utilizzati frequentemente  
 Se si vuole connettersi sempre allo stesso server e caricare lo stesso set di dati, è possibile creare file di query di collegamento contenenti le informazioni di connessione e filtro. Per altre informazioni sui file di query, vedere [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="refreshing-data"></a>Aggiornamento dei dati  
 I dati nel repository MDS possono essere aggiornati da altri utenti dopo l'esportazione. È possibile recuperare questi dati senza perdere le modifiche apportate a dati diversi da MDS. Per altre informazioni, vedere [Aggiornamento dei dati &#40;Componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/refreshing-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Filtrare i dati MDS prima di caricarli in Excel.|[Filtrare i dati prima dell'esportazione &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)|  
|Caricare dati MDS in Excel.|[Esportare dati in Excel da Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)|  
|Modificare l'ordine delle colonne prima di scaricare i dati.|[Riordinare le colonne &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Connessioni &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
-   [File di query collegamento &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Componente aggiuntivo Master Data Services per Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Sicurezza &#40;Master Data Services&#41;](../../master-data-services/security-master-data-services.md)  
  
  
