---
title: Origini dati (SSAS - multidimensionale) supportate | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 925cff488a4fdce4ca017ec2e5a0f16fe862bfe5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="supported-data-sources-ssas---multidimensional"></a>Origini dati supportate (SSAS - multidimensionale)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In questo argomento vengono descritti i tipi di origini dati che possono essere utilizzati in un modello multidimensionale.  
  
##  <a name="bkmk_supported_ds"></a> Origini dati supportate  
 È possibile recuperare dati dalle origini dati riportate nella tabella seguente. Il programma di installazione di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]non consente di installare i provider elencati per ogni origine dati. Alcuni provider potrebbero già essere installati con altre applicazioni nel computer; negli altri casi sarà necessario scaricare e installare il provider.  
  
> [!NOTE]  
>  È inoltre possibile utilizzare provider di terze parti, ad esempio il provider OLE DB Oracle, per la connessione a database di terze parti, di cui verrà offerto il supporto.  
  
|||||  
|-|-|-|-|  
|Origine|Versioni|Tipo di file|Provider*|  
|Database di Access|Microsoft Access 2010, 2013, 2016|Estensione accdb o mdb|Provider OLE DB per Microsoft Jet 4.0.|  
|Database relazionali di SQL Server*|Microsoft SQL Server 2008, 2008 R2, 2012, 2014, 2016, [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)], Azure SQL Data Warehouse, Microsoft Analitica Platform System (AP)<br /><br /> <br /><br /> Nota: altre informazioni sul [!INCLUDE[ssSDS](../../includes/sssds-md.md)] sono disponibili in [Azure.com](http://go.microsoft.com/fwlink/?LinkID=157856).<br /><br /> Nota: Analitica piattaforma di strumenti analitici era precedentemente noto come SQL Server Parallel Data Warehouse (PDW). Originariamente la connessione a PDW da Analysis Services richiedeva un provider di dati speciale. Questo provider è stato sostituito in SQL Server 2012. A partire da SQL Server 2012, per le connessioni a PDW/piattaforma di strumenti analitici viene usato SQL Server Native Client. Per altre informazioni su APS, visitare il sito Web di [Microsoft Analytics Platform System](http://www.microsoft.com/en-us/server-cloud/products/analytics-platform-system/resources.aspx).|(non applicabile)|Provider OLE DB per SQL Server<br /><br /> Provider OLE DB di SQL Server Native Client<br /><br /> Provider OLE DB per SQL Server Native Client 11.0<br /><br /> Provider di dati .NET Framework per SQL Client|  
|Database relazionali Oracle|Oracle 9i, 10g, 11g, 12g|(non applicabile)|Provider OLE DB Oracle<br /><br /> Provider di dati .NET Framework per il client Oracle<br /><br /> Provider di dati .NET Framework per SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Database relazionali di Teradata|Teradata V2R6 e V12|(non applicabile)|Provider OLE DB TDOLEDB<br /><br /> Provider di dati .NET per Teradata|  
|Database relazionali di Informix|V11.10|(non applicabile)|Provider OLE DB per Informix|  
|Database relazionali di IBM DB2|8.1|(non applicabile)|DB2OLEDB|  
|Database relazionali di Sybase Adaptive Server Enterprise (ASE)|15.0.2|(non applicabile)|Provider OLE DB per Sybase|  
|Altri database relazionali|(non applicabile)|(non applicabile)|Un provider OLE DB|  
  
 \* Le origini dati ODBC non sono supportate per soluzioni multidimensionali. Anche se la connessione viene gestita direttamente da Analysis Services, le finestre di progettazione in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] usate per la compilazione di soluzioni non sono in grado di connettersi a un'origine dati ODBC, anche quando si usano driver MSDASQL. Se i requisiti aziendali includono un'origine dati ODBC, provare invece a compilare una soluzione tabulare.  
  
 ** Alcune funzionalità richiedono un database relazionale di SQL Server eseguito in locale. In particolare, per il writeback e l'archiviazione ROLAP è necessario che l'origine dati sottostante sia un database relazionale di SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Origini dati supportate](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)   
 [Origini dati nei modelli multidimensionali](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Viste origine dati nei modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
