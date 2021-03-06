---
title: Modificare la proprietà KeyColumn di un attributo | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 70928d88ac4138eda6c7a4da7b3195005c308f31
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="attribute-properties---modify-the-keycolumn-property"></a>Attributo di proprietà, modificare la proprietà KeyColumn
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  È possibile modificare la proprietà **KeyColumns** di un attributo. Ad esempio, è possibile specificare una chiave composta anziché una chiave semplice come chiave dell'attributo.  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a>Per modificare la proprietà KeyColumns di un attributo  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto nel quale si vuole modificare la proprietà **KeyColumns** .  
  
2.  Aprire Progettazione dimensioni effettuando una delle operazioni seguenti:  
  
    -   In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla dimensione nella cartella **Dimensioni** e quindi scegliere **Apri** o **Progettazione viste**.  
  
         -oppure-  
  
    -   In Progettazione cubi, nel **struttura cubo** espandere la dimensione del cubo nel **dimensioni** riquadro e fare clic su **modifica \<dimensione >**.  
  
3.  Nel riquadro **Attributi** della scheda **Struttura dimensione** fare clic sull'attributo per il quale si vuole modificare la proprietà **KeyColumns**.  
  
4.  Nella finestra **Proprietà** fare clic sul valore della proprietà **KeyColumns** .  
  
5.  Fare clic sul pulsante di ricerca ( **...** ) che viene visualizzato nella cella del valore della casella delle proprietà.  
  
     Verrà visualizzata la finestra di dialogo **Colonne chiave** .  
  
6.  Per rimuovere una colonna chiave esistente, nell'elenco **Colonne chiave** selezionare la colonna e quindi fare clic sul pulsante **\<** .  
  
7.  Per aggiungere una colonna chiave, nell'elenco **Colonne disponibili** selezionare la colonna e quindi fare clic sul pulsante **>** .  
  
    > [!NOTE]  
    >  Se si definiscono più colonne chiave, l'ordine di visualizzazione di tali colonne nell'elenco **Colonne chiave** influisce sull'ordine visualizzato. Ad esempio, l'attributo mese ha due colonne chiave: mese ed anno. Se la colonna anno è visualizzata nell'elenco prima della colonna mese, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ordina per anno e quindi per mese. Se la colonna mese appare prima della colonna anno, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ordina per mese e quindi per anno.  
  
8.  Per modificare l'ordine delle colonne chiave, selezionare una colonna e quindi fare clic sul pulsante **Su** o **Giù** .  
  
## <a name="see-also"></a>Vedere anche  
 [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
