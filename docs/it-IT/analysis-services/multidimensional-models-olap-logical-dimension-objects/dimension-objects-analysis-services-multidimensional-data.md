---
title: Dimensione oggetti (Analysis Services - dati multidimensionali) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e2c8ec6b4551605e7c2d659c021944966f630bda
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Oggetti dimensione (Analysis Services - Dati multidimensionali)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Un oggetto <xref:Microsoft.AnalysisServices.Dimension> semplice è composto da informazioni di base, attributi e gerarchie. Le informazioni di base includono il nome e il tipo della dimensione, l'origine dati, la modalità di archiviazione e altro. Gli attributi definiscono i dati effettivi nella dimensione. Sebbene gli attributi non appartengano necessariamente a una gerarchia, le gerarchie sono compilate dagli attributi. Una gerarchia crea elenchi ordinati di livelli e definisce le modalità di esplorazione della dimensione da parte di un utente.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Negli argomenti seguenti vengono fornite ulteriori informazioni sulla progettazione e sull'implementazione degli oggetti dimensione.  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Dimensioni & #40; Analysis Services - dati multidimensionali & #41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le dimensioni sono un componente essenziale dei cubi. Le dimensioni consentono di organizzare i dati in relazione a un'area di interesse per gli utenti, ad esempio relativa a clienti, archivi o dipendenti.|  
|[Gli attributi e gerarchie di attributi](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)|Le dimensioni sono raccolte di attributi, associate a una o più colonne in una tabella o una vista della vista origine dati.|  
|[Relazioni tra attributi](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)|In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], gli attributi all'interno di una dimensione sono sempre correlati direttamente o indirettamente all'attributo chiave. Quando si definisce una dimensione in base a uno schema star, in cui tutti gli attributi della dimensione sono derivati dalla stessa tabella relazionale, viene automaticamente definita una relazione tra l'attributo chiave e ogni attributo non chiave della dimensione. Quando si definisce una dimensione in base a uno schema snowflake, in cui gli attributi della dimensione sono derivati da più tabelle correlate, viene automaticamente definita una relazione tra attributi come indicato di seguito:<br /><br /> Tra l'attributo chiave e ogni attributo non chiave associato alle colonne della tabella principale della dimensione.<br /><br /> Tra l'attributo chiave e l'attributo associato alla chiave esterna della tabella secondaria che collega le tabelle delle dimensioni sottostanti.<br /><br /> Tra l'attributo associato alla chiave esterna della tabella secondaria e ogni attributo non chiave associato alle colonne della tabella secondaria.|  
  
  
