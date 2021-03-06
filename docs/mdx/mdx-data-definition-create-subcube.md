---
title: Istruzione CREATE SUBCUBE (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE_SUBCUBE
- CREATE SUBCUBE
- CREATE
- SUBCUBE
dev_langs:
- kbMDX
helpviewer_keywords:
- subcubes [MDX]
- CREATE SUBCUBE statement
ms.assetid: 15b6ac4c-b68a-4f9f-b33c-f5f7c4a74535
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 364bf7fe910e5073130bef1a75d88bfa560dd9f9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---create-subcube"></a>Definizione dei dati MDX - creare SOTTOCUBO
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ridefinisce in base a un sottocubo specificato lo spazio di un cubo o sottocubo specificato. Questa istruzione modifica lo spazio di un cubo disponibile per le operazioni successive.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE SUBCUBE Cube_Name AS Select_Statement  
                                                  | NON VISUAL ( Select_Statement )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Espressione stringa valida che specifica il nome del cubo o della prospettiva da limitare, che diventa il nome del sottocubo.  
  
 *Select_Statement*  
 Espressione SELECT MDX (Multidimensional Expression) valida che non contiene clausole WITH, NON EMPTY o HAVING e non richiede le proprietà della dimensione o delle celle.  
  
 Vedere [istruzione SELECT &#40;MDX&#41; ](../mdx/mdx-data-manipulation-select.md) per una spiegazione dettagliata sulla sintassi istruzioni Select e i **NON VISUAL** clausola.  
  
## <a name="remarks"></a>Osservazioni  
 Se nella definizione di un sottocubo vengono eseguiti i membri predefiniti, le coordinate verranno modificate in modo appropriato. Per gli attributi che possono essere aggregati, il membro predefinito viene spostato nel membro [Totale]. Per gli attributi che non possono essere aggregati, il membro predefinito viene spostato in un membro presente nel sottocubo. Nella tabella seguente sono inclusi alcuni sottocubi di esempio e i relativi membri predefiniti.  
  
|Membro predefinito originale|Aggregabile|sub-SELECT|Membro predefinito modificato|  
|-----------------------------|-----------------------|---------------|----------------------------|  
|Time.Year.All|Sì|{Time.Year.2003}|Nessuna modifica|  
|Time.Year. [1997]|Sì|{Time.Year.2003}|Time.Year.All|  
|Time.Year. [1997]|no|{Time.Year.2003}|Time.Year. [2003]|  
|Time.Year. [1997]|Sì|{Time.Year.2003, Time.Year.2004}|Time.Year.All|  
|Time.Year. [1997]|no|{Time.Year.2003, Time.Year.2004}|Either Time.Year.[2003] o<br /><br /> Time.Year.[2004]|  
  
 I sottocubi includono sempre membri [Totale].  
  
 Gli oggetti di sessione creati nel contesto di un sottocubo vengono eliminati all'eliminazione del sottocubo.  
  
 Per ulteriori informazioni sui sottocubi, vedere [compilazione di sottocubi in MDX &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato un sottocubo che limita lo spazio di un cubo disponibile per i membri con paese Canada. Viene quindi utilizzato il **membri** funzione per restituire tutti i membri del paese livello gerarchico Geography definita dall'utente - restituendo solo il Canada.  
  
```  
CREATE SUBCUBE [Adventure Works] AS  
   SELECT [Geography].[Country].&[Canada] ON 0  
   FROM [Adventure Works]  
  
SELECT [Geography].[Country].[Country].MEMBERS ON 0  
   FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene creato un sottocubo il quale limita l'apparente spazio del cubo ai membri {Accessories, Clothing} in Products.Category e {[Value Added Reseller], [Warehouse]} in Resellers.[Business Type].  
  
 `CREATE SUBCUBE [Adventure Works] AS`  
  
 `Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works]`  
  
 Una query sul sottocubo per tutti i membri in Products.Category e Resellers.[Business Type] con la seguente istruzione MDX:  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Restituisce i risultati seguenti:  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$2,031,079.39|$506,172.45|$1,524,906.93|  
|Value Added Reseller|$767,388.52|$175,002.81|$592,385.71|  
|Warehouse|$1,263,690.86|$331,169.64|$932,521.23|  
  
 L'eliminazione e la nuova creazione del sottocubo utilizzando la clausola NON VISUAL crea un sottocubo che tiene i totali reali per tutti i membri in Products.Category e Resellers.[Business Type], che siano visibili o meno nel sottocubo.  
  
 `CREATE SUBCUBE [Adventure Works] AS`  
  
 `NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 Esecuzione della stessa query MDX precedente:  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Restituisce i seguenti risultati differenti:  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$80,450,596.98|$571,297.93|$1,777,840.84|  
|Value Added Reseller|$34,967,517.33|$175,002.81|$592,385.71|  
|Warehouse|$38,726,913.48|$331,169.64|$932,521.23|  
  
 [All Products] e [All Resellers], colonna e riga rispettivamente, contengono i totali per tutti i membri e non solo per quelli visibili.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti chiave di MDX & #40; Analysis Services & #41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [Istruzioni di Scripting MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [DROP SUBCUBE-istruzione &#40;MDX&#41;](../mdx/mdx-data-definition-drop-subcube.md)   
 [Istruzione SELECT & #40; MDX & #41;](../mdx/mdx-data-manipulation-select.md)  
  
  
