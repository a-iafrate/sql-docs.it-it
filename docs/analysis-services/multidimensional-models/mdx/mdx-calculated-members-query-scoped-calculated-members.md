---
title: Creazione con ambito Query calcolato membri (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WITH keyword
- query-scoped calculated members [MDX]
ms.assetid: c4507149-e67b-4e5d-9192-cc911acd9adc
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 2ba34cb6af554bb958c8754a9971f3ff4ba5b9a6
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="mdx-calculated-members---query-scoped-calculated-members"></a>Membri: membri calcolati con ambito Query calcolati di MDX
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Se un membro calcolato è necessario solo per un'unica query MDX (Multidimensional Expression), è possibile definire tale membro calcolato mediante la parola chiave WITH. Un membro calcolato creato utilizzando la parola chiave WITH non esisterà più al termine dell'esecuzione della query.  
  
 Come illustrato in questo argomento, la sintassi della parola chiave WITH è molto flessibile e consente addirittura di basare un membro calcolato su un altro membro calcolato.  
  
> [!NOTE]  
>  Per altre informazioni sui membri calcolati, vedere [Compilazione di membri calcolati in MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md).  
  
## <a name="with-keyword-syntax"></a>Sintassi della parola chiave WITH  
 Utilizzare la sintassi seguente per aggiungere la parola chiave WITH a un'istruzione SELECT MDX:  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ] SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]FROM <SELECT subcube clause> [ <SELECT slicer axis clause> ][ <SELECT cell property list clause> ]  
<SELECT WITH clause> ::=  
   ( [ CALCULATED ] MEMBER <CREATE MEMBER body clause>) | <CREATE MEMBER body clause> ::= Member_Identifier AS 'MDX_Expression'  
   [ <CREATE MEMBER property clause> [ , <CREATE MEMBER property clause> ... ] ]  
<CREATE MEMBER property clause> ::=  
   ( MemberProperty_Identifier = Scalar_Expression )  
  
```  
  
 Nella sintassi della parola chiave WITH il valore `Member_Identifier` rappresenta il nome completo del membro calcolato. Il nome completo include la dimensione o il livello a cui è associato il membro calcolato. Il valore `MDX_Expression` restituisce il valore del membro calcolato dopo la valutazione del valore dell'espressione. È possibile specificare i valori delle proprietà della cella intrinseche per un membro calcolato, se si desidera, indicando il nome della proprietà della cella nel valore `MemberProperty_Identifier` e il valore della proprietà della cella nel valore `Scalar_Expression` .  
  
## <a name="with-keyword-examples"></a>Esempi di parola chiave WITH  
 La query MDX seguente definisce un membro calcolato, `[Measures].[Special Discount]`, che esegue il calcolo di uno sconto speciale in base all'importo dello sconto originale.  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 È inoltre possibile creare membri calcolati in un punto qualsiasi di una gerarchia. La query MDX seguente, ad esempio, definisce il membro calcolato `[BigSeller]` per un cubo Sales ipotetico. Questo membro calcolato determina se un particolare punto vendita ha registrato almeno 100,00 nelle vendite unitarie di birra e vino. La query, tuttavia, crea il membro calcolato `[BigSeller]` non come membro figlio della dimensione `[Product]` ma come membro figlio del membro `[Beer and Wine]` .  
  
```  
WITH   
   MEMBER [Product].[Beer and Wine].[BigSeller] AS  
  IIf([Product].[Beer and Wine] > 100, "Yes","No")  
SELECT  
   {[Product].[BigSeller]} ON COLUMNS,  
   Store.[Store Name].Members ON ROWS  
FROM Sales  
  
```  
  
 I membri calcolati non devono necessariamente dipendere solo dai membri esistenti in un cubo. Un membro calcolato può inoltre basarsi su altri membri calcolati definiti nella stessa espressione MDX. La query MDX seguente, ad esempio, utilizza il valore creato nel primo membro calcolato, `[Measures].[Special Discount]`, per generare il valore del secondo membro calcolato, `[Measures].[Special Discounted Amount]`.  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Percentage] * 1.5,   
   FORMAT_STRING = 'Percent'  
  
   MEMBER [Measures].[Special Discounted Amount] AS  
   [Measures].[Reseller Average Unit Price] * [Measures].[Special Discount],   
   FORMAT_STRING = 'Currency'  
  
SELECT   
   {[Measures].[Special Discount], [Measures].[Special Discounted Amount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [Istruzione SELECT &#40; MDX &#41;](../../../mdx/mdx-data-manipulation-select.md)   
 [Creazione con ambito sessione calcolato membri &#40; MDX &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md)  
  
  
