---
title: Creare self-join in modo automatico (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 34cbf8f87e09ea7b738f29675f3f87ca1412b936
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="create-self-joins-automatically-visual-database-tools"></a>Creare self-join in modo automatico (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Se una tabella ha una relazione riflessiva nel database, sarà possibile metterla in join con se stessa automaticamente.  
  
### <a name="to-create-a-self-join-automatically"></a>Per creare automaticamente un self-join  
  
1.  Aggiungere la tabella appropriata al [riquadro Diagramma](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) .  
  
2.  Aggiungere nuovamente la stessa tabella in modo che venga visualizzata due volte nel riquadro Diagramma.  
  
    In [Progettazione query e Progettazione viste](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) verrà assegnato un alias alla seconda istanza aggiungendo un numero sequenziale al nome della tabella. Inoltre, verrà inserita una linea di join tra i due rettangoli che rappresentano i due diversi tipi di partecipazione della tabella nella query.  
  
## <a name="see-also"></a>Vedere anche  
[Eseguire query con join &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
