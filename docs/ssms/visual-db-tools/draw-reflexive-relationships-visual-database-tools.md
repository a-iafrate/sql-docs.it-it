---
title: Creare relazioni riflessive (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing reflexive relationships
- reflexive relationships
- database diagrams [SQL Server], relationships
ms.assetid: e218363f-faec-46d5-9904-a537fbcc994d
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b3f92a8f199bf03ff3a9c0cff4aedfb8a138ebec
ms.lasthandoff: 04/11/2017

---
# <a name="draw-reflexive-relationships-visual-database-tools"></a>Creazione di relazioni riflessive (Visual Database Tools)
Le relazioni riflessive consentono di collegare una o più colonne di una tabella con una o più colonne della stessa tabella. Si supponga, ad esempio, che nella tabella `employee` sia presente una colonna `emp_id` e una colonna `mgr_id` . Poiché ogni responsabile è a sua volta anche un dipendente, è possibile correlare le due colonne tracciando una linea di relazione all'interno della stessa tabella. La relazione assicura che a ciascun ID responsabile aggiunto alla tabella corrisponda un ID dipendente esistente.  
  
Prima di creare una relazione, è necessario definire una chiave primaria o un vincolo univoco per la tabella. In seguito si correlerà la colonna chiave primaria con una colonna corrispondente. Una volta creata la relazione, la colonna corrispondente diventerà una chiave esterna della tabella.  
  
### <a name="to-draw-a-reflexive-relationship"></a>Per disegnare una relazione riflessiva  
  
1.  Nel diagramma del database fare clic sul selettore di riga della colonna di database che si desidera correlare a un'altra colonna e trascinare il puntatore all'esterno della tabella finché non viene visualizzata una linea.  
  
2.  Trascinare la linea di nuovo sulla tabella selezionata.  
  
3.  Rilasciare il pulsante del mouse. Verrà visualizzata la finestra di dialogo **Tabelle e colonne** .  
  
4.  Selezionare la colonna chiave esterna e la tabella e la colonna chiave primaria con cui si desidera creare una relazione.  
  
5.  Scegliere due volte **OK** per creare la relazione.  
  
Quando si eseguono delle query su una tabella, è possibile utilizzare una relazione riflessiva per creare un self-join. Per informazioni sull'esecuzione di query su tabelle con join, vedere [Query with Joins &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md).  
  
## <a name="see-also"></a>Vedere anche  
[Eseguire query con join &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
