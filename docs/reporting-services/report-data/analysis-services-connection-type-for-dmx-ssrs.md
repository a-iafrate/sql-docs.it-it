---
title: Tipo di connessione di Analysis Services per DMX (SSRS) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-data
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters [Reporting Services], DMX
- Data Mining Prediction [Reporting Services]
- query view [Reporting Services]
- DMX [Reporting Services]
- design view [Reporting Services]
- data mining [Reporting Services]
- passing parameters [Reporting Services]
ms.assetid: 2de825e9-6d8a-4128-add0-da15dc6cea3e
caps.latest.revision: "64"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 14ff9f92d3582bbad4af7d3252d2e2ae6ce170bd
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="analysis-services-connection-type-for-dmx-ssrs"></a>Tipo di connessione di Analysis Services per DMX (SSRS)
  Quando si crea un set di dati da un'origine dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , Progettazione report visualizza la finestra Progettazione query MDX (Multidimensional Expression) se rileva un cubo valido. Se non viene rilevato alcun cubo, ma è disponibile un modello di data mining, in Progettazione report viene visualizzata la finestra Progettazione query DMX (Data Mining Extensions). Per visualizzare alternativamente le finestre di progettazione MDX e DMX, fare clic sul pulsante **Tipo di comando DMX** (![Passa alla visualizzazione linguaggio query DMX](../../reporting-services/report-data/media/rsqdicon-commandtypedmx.gif "Passa alla visualizzazione linguaggio query DMX")) sulla barra degli strumenti. La finestra di progettazione query DMX consente di compilare in modo interattivo una query DMX tramite elementi grafici. Per utilizzare Progettazione query DMX, l'origine dei dati specificata deve avere già un modello di data mining che fornisce i dati. I risultati della query vengono convertiti in un set di righe bidimensionale da utilizzare nel report.  
  
> [!NOTE]  
>  Prima di progettare il report, è necessario eseguire il training del modello. Per altre informazioni, vedere [Soluzioni di data mining](../../analysis-services/data-mining/data-mining-solutions.md).  
  
## <a name="design-mode"></a>Modalità progettazione  
 Progettazione query DMX viene aperto in modalità progettazione. Tale modalità include un'area di progettazione grafica utilizzata per la selezione di un singolo modello di data mining e di una tabella di input e una griglia utilizzata per specificare la query di stima. Sono disponibili altre due modalità di Progettazione query, ovvero query e risultati. In modalità query, la griglia della modalità progettazione è sostituita da un riquadro Query che è possibile utilizzare per digitare query DMX. In modalità risultati il set di risultati restituito dalla query viene visualizzato in una griglia di dati.  
  
 Per modificare le modalità di Progettazione query DMX, fare clic con il pulsante destro del mouse nell'area di progettazione della query e scegliere **Progettazione**, **Query**o **Risultato**. Per altre informazioni, vedere [Interfaccia utente di Progettazione query DMX in Analysis Services](../../reporting-services/report-data/analysis-services-dmx-query-designer-user-interface.md) e [Recuperare i dati da un modello di data mining &#40;DMX&#41; &#40;SSRS&#41;](../../reporting-services/report-data/retrieve-data-from-a-data-mining-model-dmx-ssrs.md).  
  
## <a name="designing-a-prediction-query"></a>Progettazione di una query di stima  
 Il riquadro Progettazione query in modalità progettazione contiene due finestre, ovvero **Modello di data mining** e **Seleziona tabella di input**. Usare la finestra **Modello di data mining** per selezionare il modello di data mining da usare nella query. Usare la finestra **Seleziona tabella/e di input** per selezionare la tabella sulla quale basare le stime. Se si vuole usare una query singleton anziché una tabella di input, fare clic con il pulsante destro del mouse nel riquadro di progettazione query e scegliere **Query singleton**. La finestra **Seleziona tabella/e di input** è sostituita da una finestra **Input query singleton** .  
  
 In modalità progettazione trascinare i campi dalle finestre **Modello di data mining** e **Seleziona tabella/e di input** nella colonna **Campo** del riquadro griglia. È inoltre possibile compilare le colonne restanti per specificare un alias, mostrare il campo nei risultati, raggruppare campi e specificare un operatore per limitare il valore del campo a uno specifico criterio o argomento. In modalità query trascinare i campi nel riquadro Query per compilare la query DMX.  
  
## <a name="using-parameters"></a>Utilizzo di parametri  
 È possibile passare parametri di report a un parametro di query DMX. A tale scopo, è necessario aggiungere un parametro alla query DMX, definire i parametri di query nella finestra di dialogo **Parametri query** e quindi modificare i parametri di report associati. Per definire un parametro di query, fare clic su **Parametri query** (![icona della finestra di dialogo Parametri query](../../reporting-services/report-data/media/iconqueryparameter.gif "icona della finestra di dialogo Parametri query")) nella barra degli strumenti. Per istruzioni sulla definizione dei parametri in una query DMX, vedere [Definizione dei parametri in Progettazione query MDX per Analysis Services &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/define-parameters-in-the-mdx-query-designer-for-analysis-services.md).  
  
 Per altre informazioni sulla gestione della relazione tra i parametri di query e i parametri di report, vedere [Associazione di un parametro di query a un parametro di report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs.md). Per altre informazioni sui parametri, vedere [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Soluzioni di data mining](../../analysis-services/data-mining/data-mining-solutions.md)   
 [Strumenti di progettazione query &#40;SSRS&#41;](../../reporting-services/report-data/query-design-tools-ssrs.md)   
 [Connessioni dati, origini dati e stringhe di connessione in Generatore report e SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
