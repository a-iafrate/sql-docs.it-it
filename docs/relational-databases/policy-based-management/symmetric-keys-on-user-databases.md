---
title: Chiavi simmetriche nei database utente | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: be15cf6291d6cdeefe64f6dc6be77fe604dde30d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="symmetric-keys-on-user-databases"></a>Chiavi simmetriche nei database utente
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Questa regola consente di controllare se le chiavi con lunghezza minore di 128 byte utilizzano l'algoritmo di crittografia RC2 o RC4.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Utilizzare la crittografia AES a 128 bit o maggiore per creare chiavi simmetriche per la crittografia dei dati. Se la crittografia AES non è supportata dal sistema operativo in uso, utilizzare 3DES.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Scelta di un algoritmo di crittografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
