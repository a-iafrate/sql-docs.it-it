---
title: STNumCurves (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geometry)
ms.assetid: 20c2fa0b-656b-4519-b34c-cc8f094290d4
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 947baac6cd2a562bc24469bcf9554aca7a735ae7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="stnumcurves-geometry-data-type"></a>STNumCurves (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Questo metodo restituisce il numero di curve di un'istanza **geometry** quando l'istanza è un tipo di dati spaziali unidimensionali. I tipi di dati spaziali unidimensionali includono **LineString**, **CircularString** e **CompoundCurve**. `STNumCurves`() funziona solo su tipi semplici; non funziona con raccolte **geometry** come **MultiLineString**.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Un'istanza **geometry** unidimensionale vuota restituisce 0. Viene restituito **NULL** quando l'istanza **geometry** non è un'istanza unidimensionale oppure è un'istanza non inizializzata.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. Utilizzo di STNumCurves() in un'istanza CircularString  
 Nell'esempio seguente viene illustrato come ottenere il numero di curve in un'istanza `CircularString`:  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>B. Utilizzo di STNumCurves() in un'istanza CompoundCurve  
 Nell'esempio seguente viene utilizzato `STNumCurves()` per restituire il numero di curve in un'istanza `CompoundCurve`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei tipi di dati spaziali](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

