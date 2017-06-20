---
title: Report di metodi del servizio Web ReportServer | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
caps.latest.revision: 49
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ec79e5169ff32294cc68f5bee24c3df677d8b38b
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="report-server-web-service-methods"></a>Metodi del servizio Web ReportServer
  I servizi Web ReportServer includono diverse categorie di metodi basate sulle caratteristiche dei componenti. Questi metodi vengono forniti tramite diversi endpoint del servizio Web (tre per la gestione e uno per l'esecuzione dei report) esposti come membri delle classi <xref:ReportService2010.ReportingService2010> e <xref:ReportExecution2005.ReportExecutionService>. Queste classi possono essere generate tramite uno strumento di classe proxy, ad esempio wsdl.exe, inclusa la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK. Per ulteriori informazioni sui servizi Web ReportServer e [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], vedere [compilazione di applicazioni tramite il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
## <a name="endpoints-and-methods"></a>Endpoint e metodi  
 Nella tabella seguente vengono elencati gli endpoint del servizio Web ReportServer e le categorie di metodi forniti dall'endpoint <xref:ReportService2010.ReportingService2010>. Per informazioni sui metodi disponibili in altri endpoint, vedere [tecniche &#40; SSRS &#41; ](../../../reporting-services/technical-reference-ssrs.md).  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Endpoint del servizio Web ReportServer](../../../reporting-services/report-server-web-service/methods/report-server-web-service-endpoints.md)|Descrive gli endpoint di gestione ed esecuzione del servizio Web ReportServer.|  
|[Metodi di gestione di report Server Namespace](../../../reporting-services/report-server-web-service/methods/report-server-namespace-management-methods.md)|Descrive i metodi che è possibile utilizzare per gestire il database del server di report. In particolare, è possibile gestire le cartelle e le risorse e impostare le proprietà dell'elemento.|  
|[Metodi di autorizzazione](../../../reporting-services/report-server-web-service/methods/authorization-methods.md)|Descrive i metodi che è possibile utilizzare per gestire attività, ruoli e criteri.|  
|[Origini dati e i metodi di connessione](../../../reporting-services/report-server-web-service/methods/data-sources-and-connection-methods.md)|Descrive i metodi che è possibile utilizzare per impostare e gestire la connessione all'origine dati e le informazioni sulle credenziali per i report.|  
|[Metodi di parametri di report](../../../reporting-services/report-server-web-service/methods/report-parameters-methods.md)|Descrive i metodi che è possibile utilizzare per impostare e recuperare parametri per i report.|  
|[Metodi del modello - servizio Web ReportServer](../../../reporting-services/report-server-web-service/methods/model-methods-report-server-web-service.md)|Descrive i metodi che è possibile utilizzare per gestire modelli.|  
|[Per il rendering e i metodi di esecuzione](../../../reporting-services/report-server-web-service/methods/rendering-and-execution-methods.md)|Descrive i metodi che è possibile utilizzare per gestire l'esecuzione, il rendering e la memorizzazione nella cache dei report.|  
|[Metodi relativi alla cronologia report](../../../reporting-services/report-server-web-service/methods/report-history-methods.md)|Descrive i metodi che è possibile utilizzare per creare e gestire gli snapshot della cronologia dei report.|  
|[Metodi di pianificazione](../../../reporting-services/report-server-web-service/methods/scheduling-methods.md)|Descrive i metodi che è possibile utilizzare per creare e gestire pianificazioni condivise e piani di aggiornamento della cache utilizzate dal server di report.|  
|[Metodi di sottoscrizione e recapito](../../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md)|Descrive i metodi che è possibile utilizzare per creare e gestire sottoscrizioni e recapito dei report.|  
|[Metodi di report collegati](../../../reporting-services/report-server-web-service/methods/linked-reports-methods.md)|Descrive i metodi che è possibile utilizzare per creare e gestire i report collegati.|  
  
## <a name="see-also"></a>Vedere anche  
 [L'accesso all'API SOAP](../../../reporting-services/report-server-web-service/accessing-the-soap-api.md)   
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Riferimento tecnico &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  