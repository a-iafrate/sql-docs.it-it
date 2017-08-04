---
title: Impostazioni globali (finestre di dialogo) (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43989355-cebf-4d8b-ba3d-fa8546e70230
caps.latest.revision: 3
author: sabotta
ms.author: carlasab
manager: v-pelars
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e2feffc4f4fdf2d37797bf51581eaad83580210e
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="global-settings-dialogs--oracletosql"></a>Impostazioni globali (finestre di dialogo) (OracleToSQL)
Utilizzare la pagina di finestre di dialogo del **impostazioni globali** la finestra di dialogo per specificare l'azione predefinita dell'utente e impostazioni di avviso per SSMA.  
  
Per accedere alle impostazioni di finestra di dialogo nel **strumenti** dal menu **impostazioni globali**, fare clic su **GUI** nella parte inferiore del riquadro sinistro, quindi scegliere **finestre di dialogo**.  
  
## <a name="options"></a>Opzioni  
**Avvisa prima di sovrascrivere gli oggetti**  
Quando SSMA converte gli oggetti in SQL Server, alcuni oggetti potrebbero già esistere nei metadati del progetto SQL Server. Questi oggetti possono sono già stati convertiti o gli oggetti siano presenti lo stesso nome all'interno dello schema di destinazione come oggetti di cui che si desidera convertire.  
  
Utilizzare questa opzione per specificare se SSMA venga chiesto di sovrascrivere le definizioni degli oggetti duplicati:  
  
-   Se si seleziona **True**, SSMA verrà visualizzata una finestra di dialogo di avviso quando rileva un oggetto duplicato. In questa finestra di dialogo è possibile specificare per sovrascrivere i singoli oggetti o tutti gli oggetti duplicati o di ignorare i singoli oggetti o tutti gli oggetti duplicati.  
  
-   Se si seleziona **False**, **azione predefinita di sovrascrittura dell'oggetto** opzione viene visualizzata in cui si specifica l'azione predefinita.  
  
**Azione predefinita di sovrascrittura di oggetto**  
Questa opzione viene visualizzata se si seleziona **False** per il **Avvisa prima di sovrascrivere gli oggetti** opzione.  
  
Utilizzare questa opzione per specificare l'oggetto predefinito sovrascrivere il comportamento:  
  
-   Se si seleziona **True**, SSMA sovrascrive automaticamente gli oggetti nei metadati del progetto di SQL Server che hanno lo stesso nome e sono nello stesso schema di destinazione dell'oggetto da convertire.  
  
-   Se si seleziona **False**, SSMA non sovrascrive i metadati degli oggetti durante la conversione.  
  
