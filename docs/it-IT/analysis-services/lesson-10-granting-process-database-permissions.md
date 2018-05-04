---
title: Concessione di autorizzazioni di Database di processo | Documenti Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 69ba952e-09ae-49a9-9297-00e32e8e89a8
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 42e6abd08ccd8fe8cb574fa8fc0e3056c04f0801
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-10---granting-process-database-permissions"></a>Lezione 10 - concessione di autorizzazioni di Database di elaborazione
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

Dopo l'installazione di un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], tutti i membri del ruolo di amministratore del server [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nell'istanza dispongono di autorizzazioni valide per l'intero server per eseguire qualsiasi attività all'interno dell'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Per impostazione predefinita, nessun altro utente dispone dell'autorizzazione per amministrare o visualizzare gli oggetti nell'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
Un membro del ruolo di amministratore del server può consentire agli utenti l'accesso amministrativo a livello del server rendendoli membri del ruolo. Un membro del ruolo di amministratore del server può inoltre concedere agli utenti un accesso più limitato concedendo autorizzazioni amministrative o di accesso limitate o complete a livello di database. Le autorizzazioni amministrative limitate includono autorizzazioni per l'elaborazione o la visualizzazione delle definizioni degli oggetti a livello di database, cubo o dimensione.  
  
Nelle procedure descritte in questo argomento viene definito un ruolo di sicurezza Process Database Objects che concede ai membri del ruolo l'autorizzazione per elaborare tutti gli oggetti di database, ma non concede alcuna autorizzazione per visualizzare i dati nel database.  
  
## <a name="defining-a-process-database-objects-security-role"></a>Definizione di un ruolo di sicurezza Process Database Objects  
  
1.  Fare clic con il pulsante destro del mouse su **Ruoli** in Esplora soluzioni, quindi scegliere **Nuovo ruolo** per aprire Progettazione ruoli.  
  
2.  Selezionare la casella di controllo **Elaborazione database** .  
  
3.  Nella finestra Proprietà modificare la proprietà **Nome** del nuovo ruolo in **Process Database Objects Role**.  
  
    ![Progettazione ruoli](../analysis-services/media/l10-security-1.png "progettazione ruoli")  
  
4.  Passare alla scheda **Appartenenze** di Progettazione ruoli e fare clic su **Aggiungi**.  
  
5.  Immettere gli account di utenti o gruppi di dominio Windows che saranno membri di questo ruolo. Fare clic su **Verifica nomi** per verificare le informazioni sull'account, quindi fare clic su **OK**.  
  
6.  Passare alla scheda **Cubi** di Progettazione ruoli.  
  
    Si noti che i membri di questo ruolo dispongono delle autorizzazioni per elaborare questo database, ma non per accedere ai dati nel cubo [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial né dispongono dell'accesso locale al cubo/drill-through, come illustrato nella figura seguente.  
  
    ![Scheda cubi di progettazione ruoli](../analysis-services/media/l10-security-2.png "scheda cubi di progettazione ruoli")  
  
7.  Passare alla scheda **Dimensioni** di Progettazione ruoli.  
  
    Si noti che i membri di questo ruolo dispongono delle autorizzazioni per elaborare tutti gli oggetti dimensione in questo database e, per impostazione predefinita, delle autorizzazioni di lettura per accedere a ogni oggetto dimensione nel database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.  
  
8.  Scegliere **Distribuisci Analysis Services Tutorial** dal menu **Compila**.  
  
    La definizione e la distribuzione del ruolo di sicurezza Process Database Objects sono state portate a termine con successo. Quando un cubo viene distribuito nell'ambiente di produzione gli amministratori del cubo distribuito possono aggiungere utenti al ruolo, allo scopo di delegare le responsabilità di elaborazione a utenti specifici.  
  
> [!NOTE]  
> È possibile ottenere un progetto completo per la lezione 10 scaricando e installando gli esempi aggiornati. Per altre informazioni, vedere [Installare dati di esempio e progetti per l'esercitazione di modellazione multidimensionale di Analysis Services](../analysis-services/install-sample-data-and-projects.md).  
  
## <a name="see-also"></a>Vedere anche  
[Ruoli e autorizzazioni & #40; Analysis Services & #41;](../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  
  