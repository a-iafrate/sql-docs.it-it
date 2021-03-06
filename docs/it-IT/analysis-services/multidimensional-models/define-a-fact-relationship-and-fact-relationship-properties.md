---
title: Definire una relazione di tipo fatti e le relative proprietà | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4206cdda1b608b8cb22adaca531b917e80b94571
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Definire una relazione di tipo Fatti e le relative proprietà
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Quando si definisce un nuovo gruppo di misure o una nuova dimensione del cubo, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prova a rilevare la presenza di una relazione tra dimensioni dei fatti e quindi imposta l'utilizzo delle dimensioni su **Fatti**. È possibile visualizzare o modificare una relazione di tipo Fatti nella scheda **Utilizzo dimensioni** di Progettazione cubi. La relazione di tipo Fatti tra una dimensione e un gruppo di misure presenta i vincoli seguenti:  
  
-   Una dimensione del cubo può avere un'unica relazione di tipo Fatti con un particolare gruppo di misure.  
  
-   Una dimensione del cubo può avere diverse relazioni di tipo Fatti con più gruppi di misure.  
  
-   L'attributo di granularità per la relazione deve essere l'attributo chiave, ad esempio il numero di transazione, della dimensione. Viene così creata una relazione uno-a-uno tra la dimensione e i fatti della tabella dei fatti.  
  
  
