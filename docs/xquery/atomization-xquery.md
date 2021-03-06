---
title: Atomizzazione (XQuery) | Documenti Microsoft
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, atomization
- atomization [XQuery]
ms.assetid: e3d7cf2f-c6fb-43c2-8538-4470a6375af5
caps.latest.revision: 16
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a704ccc0b5be37a668984ce4d8d543984f360b54
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="atomization-xquery"></a>Atomizzazione (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Per atomizzazione si intende il processo di estrazione del valore tipizzato di un elemento. In determinate circostanze, il processo è implicito. Alcuni operatori XQuery, ad esempio gli operatori aritmetici e di confronto, dipendono da tale processo. Ad esempio, quando si applicano operatori aritmetici direttamente ai nodi, il valore tipizzato di un nodo viene recuperato innanzitutto richiamando in modo implicito il [funzione dati](../xquery/data-accessor-functions-data-xquery.md). Tale funzione passa il valore atomico come operando all'operatore aritmetico.  
  
 Ad esempio, la query seguente restituisce il numero totale di attributi LaborHours. In questo caso, **data ()** viene applicata in modo implicito ai nodi attributo.  
  
```  
declare @x xml  
set @x='<ROOT><Location LID="1" SetupTime="1.1" LaborHours="3.3" />  
<Location LID="2" SetupTime="1.0" LaborHours="5" />  
<Location LID="3" SetupTime="2.1" LaborHours="4" />  
</ROOT>'  
-- data() implicitly applied to the attribute node sequence.  
SELECT @x.query('sum(/ROOT/Location/@LaborHours)')  
```  
  
 Sebbene non obbligatorio, è possibile specificare in modo esplicito il **data ()** funzione:  
  
```  
SELECT @x.query('sum(data(ROOT/Location/@LaborHours))')  
```  
  
 Un altro esempio di atomizzazione implicita riguarda l'utilizzo di operatori aritmetici. Il **+** operatore richiede valori atomici e **data ()** viene applicata in modo implicito per recuperare il valore atomico dell'attributo LaborHours. La query viene specificata sulla colonna Instructions del **xml** tipo nella tabella ProductModel. La query seguente restituisce tre volte l'attributo LaborHours. Dalla query si noti quanto segue:  
  
-   Nella costruzione dell'attributo OrignialLaborHours, l'atomizzazione viene applicata in modo implicito alla sequenza singleton restituita da (`$WC/@LaborHours`). Il valore tipizzato dell'attributo LaborHours viene assegnato a OrignialLaborHours.  
  
-   Nella costruzione dell'attributo UpdatedLaborHoursV1, l'operatore aritmetico richiede valori atomici. Pertanto, **data ()** viene applicata in modo implicito all'attributo LaborHours restituito da (`$WC/@LaborHours`). Successivamente, viene aggiunto il valore atomico 1. La costruzione dell'attributo UpdatedLaborHoursV2 viene illustrata l'applicazione esplicita della **data ()**, ma non è obbligatorio.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in /AWMI:root/AWMI:Location[1]  
        return  
            <WC OriginalLaborHours = "{ $WC/@LaborHours }"  
                UpdatedLaborHoursV1 = "{ $WC/@LaborHours + 1 }"   
                UpdatedLaborHoursV2 = "{ data($WC/@LaborHours) + 1 }" >  
            </WC>') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Risultato:  
  
```  
<WC OriginalLaborHours="2.5"   
    UpdatedLaborHoursV1="3.5"   
    UpdatedLaborHoursV2="3.5" />  
```  
  
 L'atomizzazione restituisce un'istanza di tipo semplice, un set vuoto o un errore di tipo statico.  
  
 Atomizzazione si verifica anche in parametri dell'espressione di confronto passati alle funzioni, valori restituiti dalle funzioni, **cast ()** espressioni ed espressioni di ordinamento passate nell'ordine in base alla clausola.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su XQuery](../xquery/xquery-basics.md)   
 [Espressioni di confronto &#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)   
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
