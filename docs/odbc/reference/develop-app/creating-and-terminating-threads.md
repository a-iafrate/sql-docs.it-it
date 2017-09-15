---
title: Creazione e chiusura di thread | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7a30fbe976ac3de550f8067cca82732631f698ac
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="creating-and-terminating-threads"></a>Creazione e chiusura di thread
Applicazioni multithread che utilizzano ODBC devono chiamare le funzioni della libreria Run-Time di Microsoft® Visual C++® **beginthread** e **endthread** (o **beginthreadex** e **endthreadex**) per creare e terminare i thread che chiamano gestione Driver ODBC. Se le applicazioni chiamano le funzioni Microsoft Windows NT® **CreateThread** e **EndThread** invece le funzioni che perché Gestione Driver e alcuni driver ODBC di chiamata C in fase di esecuzione si verificherà le perdite di memoria non funziona in un thread creato chiamando **CreateThread**. Per ulteriori informazioni, vedere la documentazione di Microsoft Windows®.