---
title: TRY_CONVERT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- TRY_CONVERT_TSQL
- TRY_CONVERT
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_CONVERT function
ms.assetid: 3e6e7825-6482-4cb2-a8c2-9abc99e265a6
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 2ef43a22ebbdd936ec6be0ef1fec1186e80caffc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="tryconvert-transact-sql"></a>TRY_CONVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce un cast del valore nel tipo di dati specificato se il cast ha esito positivo. In caso contrario, restituisce Null.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
TRY_CONVERT ( data_type [ ( length ) ], expression [, style ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *data_type [ ( length ) ]*  
 Tipo di dati in cui eseguire il cast di *expression*.  
  
 *expression*  
 Valore di cui eseguire il cast.  
  
 *style*  
 Espressione Integer facoltativa che specifica il modo in cui la funzione **TRY_CONVERT** viene usata per convertire *expression*.  
  
 *style* accetta gli stessi valori del parametro *style* della funzione **CONVERT**. Per altre informazioni, vedere [CAST and CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 L'intervallo di valori accettabili è determinato dal valore di *data_type*. Se *style* è Null, **TRY_CONVERT** restituisce Null.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce un cast del valore nel tipo di dati specificato se il cast ha esito positivo. In caso contrario, restituisce Null.  
  
## <a name="remarks"></a>Remarks  
 **TRY_CONVERT** accetta il valore passato e prova a convertirlo nel tipo di dati *data_type* specificato. Se il cast ha esito positivo, **TRY_CONVERT** restituisce il valore come l'elemento *data_type* specificato. Se si verifica un errore, viene restituito Null. Se tuttavia si richiede una conversione non consentita in modo esplicito, **TRY_CONVERT** ha esito negativo e viene restituito un errore.  
  
 **TRY_CONVERT** è una parola chiave riservata nel livello di compatibilità 110 o superiore.  
  
 Questa funzione può essere eseguita in modalità remota in server con versione [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e successive, ma non in server con versioni precedenti a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-tryconvert-returns-null"></a>A. TRY_CONVERT restituisce Null  
 Nell'esempio seguente viene dimostrato che TRY_CONVERT restituisce Null quando il cast non riesce.  
  
```sql  
SELECT   
    CASE WHEN TRY_CONVERT(float, 'test') IS NULL   
    THEN 'Cast failed'  
    ELSE 'Cast succeeded'  
END AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
Cast failed  
  
(1 row(s) affected)  
```  
  
 Nell'esempio seguente viene dimostrato che l'espressione deve essere nel formato previsto.  
  
```sql  
SET DATEFORMAT dmy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-tryconvert-fails-with-an-error"></a>B. TRY_CONVERT restituisce un errore  
 Nell'esempio seguente viene dimostrato che TRY_CONVERT restituisce un errore quando il cast non è consentito in modo esplicito.  
  
```sql  
SELECT TRY_CONVERT(xml, 4) AS Result;  
GO  
```  
  
 Il risultato di questa istruzione è un errore perché il cast di un tipo di dati Integer non può essere eseguito nel tipo di dati xml.  
  
```  
Explicit conversion from data type int to xml is not allowed.  
```  
  
### <a name="c-tryconvert-succeeds"></a>C. TRY_CONVERT ha esito positivo  
 In questo esempio viene dimostrato che l'espressione deve essere nel formato previsto.  
  
```  
SET DATEFORMAT mdy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------------------  
2010-12-31 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
