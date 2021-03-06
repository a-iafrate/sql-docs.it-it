---
title: Configurare il livello (totale) per le gerarchie di attributi | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dff6197f4bad933ee4e5abaf5e83e65125df3596
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="database-dimensions---configure-the-all-level-for-attribute-hierarchies"></a>Le dimensioni del database, configurare il livello (totale) per le gerarchie di attributi
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] il livello (Totale) è un livello facoltativo generato dal sistema. Contiene un solo membro il cui valore è determinato dall'aggregazione dei valori di tutti i membri nel livello immediatamente subordinato. Questo membro è denominato membro Totale. Si tratta di un membro generato dal sistema non contenuto nella tabella della dimensione. Poiché il membro nel livello (Totale) si trova al primo livello della gerarchia, il relativo valore è determinato dall'aggregazione consolidata dei valori di tutti i membri della gerarchia. Il membro Totale spesso funge da membro predefinito di una gerarchia.  
  
 La presenza di un livello (Totale) nella gerarchia di un attributo dipende dall'impostazione della proprietà **IsAggregatable** dell'attributo, mentre la presenza di un livello (Totale) in una gerarchia definita dall'utente dipende dall'impostazione della proprietà **IsAggregatable** dell'attributo nel livello superiore della gerarchia definita dall'utente. Se la proprietà **IsAggregatable** è impostata su **True**, esisterà un livello (Totale). Se la proprietà **IsAggregatable** è impostata su **False**il livello (Totale) non sarà presente.  
  
## <a name="establishing-the-topmost-level"></a>Determinazione del livello superiore  
 Se la proprietà **IsAggregatable** è impostata su **False** nell'attributo di origine di un livello di una gerarchia, la gerarchia non potrà contenere un livello aggregabile al di sopra di tale livello. È necessario che il livello non aggregabile sia il livello superiore di qualsiasi gerarchia oppure che la proprietà **IsAggregatable** degli attributi di origine in qualsiasi livello al di sopra di quello non aggregabile sia anch'essa impostata su **False**.  
  
## <a name="all-member-and-all-level"></a>Membro Totale e livello (Totale)  
 Il singolo membro del livello (Totale) è denominato membro Totale. La proprietà **AttributeAllMemberName**di una dimensione specifica il nome del membro Totale per gli attributi in una dimensione. La proprietà **AllMemberName** di una gerarchia specifica il nome del membro Totale per la gerarchia.  
  
## <a name="see-also"></a>Vedere anche  
 [Definire un membro predefinito](../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
