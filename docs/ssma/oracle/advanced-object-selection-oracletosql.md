---
title: Advanced Selezione oggetto (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c978fba4-c953-4ed0-a21d-1b38e7225552
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: v-pelars
ms.openlocfilehash: 03f32f9754c7263a478c43d88590ae8421fee4a2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="advanced-object-selection--oracletosql"></a>Selezione avanzata di oggetti (OracleToSQL)
Il **avanzate sezione oggetto** la finestra di dialogo consente di filtrare gli oggetti di database utilizzando le stringhe e sottostringhe nel nome dell'oggetto, quindi selezionare o deselezionare gli oggetti. SSMA consente di eseguire operazioni di conversione e migrazione oggetti selezionati.  
  
Per accedere a questa finestra di dialogo, in un Visualizzatore metadati e quindi scegliere **Selezione oggetto avanzata**.  
  
Quando si apre la finestra di dialogo, fare clic su **Mostra elementi sottocategorie** per visualizzare tutti gli oggetti che dispongono di metadati caricato nel progetto. È quindi possibile immettere le stringhe per filtrare gli elementi. Ad esempio, immettere la stringa "company" per visualizzare tutti gli elementi con nomi che includono tale stringa.  
  
Prima di utilizzare questa finestra di dialogo, si desidera forzare SSMA per caricare tutti i metadati dal salvataggio del progetto o la conversione di schemi.  
  
## <a name="options"></a>Opzioni  
**Controllare tutti gli elementi**  
Aggiunge un segno di spunta accanto a tutti gli elementi. Questi elementi verranno immediatamente selezionati in Esplora risorse di metadati.  
  
**Deselezionare tutti gli elementi**  
Rimuove il segno di spunta accanto a tutti gli elementi. Questi elementi verranno cancellati immediatamente in Esplora risorse di metadati.  
  
**Modalità di visualizzazione elenco**  
Consente di visualizzare filtrato di elementi in un elenco.  
  
**Modalità di visualizzazione tabella**  
Consente di visualizzare filtrato di elementi in una tabella.  
  
**Caricare solo gli elementi visualizzati**  
Attiva o disattiva la visualizzazione delle categorie o gli elementi. Quando si seleziona questo pulsante, SSMA Mostra tutti gli elementi che soddisfano i criteri di filtro e quelli che sono stati caricati in precedenza. Se questo pulsante non è selezionato, tramite SSMA vengono illustrate le cartelle di categoria.  
  
**Filtra**  
Immettere la stringa in cui che si desidera utilizzare per filtrare gli elementi. Ad esempio, per trovare tutti disponibili elementi che contengono la stringa "ID" nel nome dell'elemento, immettere la stringa "ID" nel **filtro** casella.  
  
Se gli elementi corrispondono ai criteri di filtro, le categorie o gli elementi verranno visualizzato durante la digitazione della stringa. Per visualizzare gli elementi corrispondenti, si consiglia di scegliere il **visualizzati solo gli elementi caricati** pulsante.  
  
**Cancella filtro**  
Cancella il **filtro** casella.  
  
