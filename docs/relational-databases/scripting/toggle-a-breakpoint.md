---
title: Attivare/disattivare un punto di interruzione | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 69e92d35e7805093d24421f39223030cc349f4c6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="toggle-a-breakpoint"></a>Attivare/disattivare un punto di interruzione
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  L'azione di definizione di un punto di interruzione in un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] è denominata impostazione/rimozione di un punto di interruzione.  
  
## <a name="breakpoints"></a>Punti di interruzione  
 Una volta impostato, il punto di interruzione è rappresentato da un'icona nella barra grigia a sinistra dell'istruzione. L'icona è nota come glifo del punto di interruzione. [!INCLUDE[tsql](../../includes/tsql-md.md)] I punti di interruzione vengono applicati a un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] completa. Quando un punto di interruzione viene attivato, il debugger evidenzia l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] associata.  
  
 Se sono presenti più istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] su una riga, è possibile impostare/rimuovere un punto di interruzione per ogni istruzione. Facendo clic nella barra grigia a sinistra della finestra, è possibile impostare/rimuovere un punto di interruzione nella prima istruzione della riga. Per impostare/rimuovere un punto di interruzione in un'istruzione successiva, è possibile evidenziare qualsiasi parte dell'istruzione o spostare il cursore all'interno dell'istruzione e quindi premere F9 o scegliere **Imposta/Rimuovi punto di interruzione** dal menu **Debug** . Se sono presenti più punti di interruzione su una riga, nella barra grigia a sinistra sarà presente il glifo di un solo punto di interruzione.  
  
 Dopo aver attivato o disattivato un punto di interruzione, è possibile eseguirvi diverse operazioni, ad esempio modificarne le proprietà oppure disabilitarlo temporaneamente. Per altre informazioni, vedere [Punti di interruzione Transact-SQL](../../relational-databases/scripting/transact-sql-breakpoints.md).  
  
## <a name="toggle-a-breakpoint"></a>Attivare/disattivare un punto di interruzione  
 **Per attivare o disattivare un punto di interruzione in un'istruzione Transact-SQL**  
  
1.  Fare clic sulla barra grigia a sinistra dell'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
2.  In alternativa, evidenziare qualsiasi parte dell'istruzione o spostare il cursore all'interno dell'istruzione, quindi effettuare una delle azioni seguenti:  
  
    -   Premere F9.  
  
    -   Scegliere **Imposta/Rimuovi punto di interruzione** dal menu **Debug**.  
  
  
