---
title: STInteriorRingN (tipo di dati geometry) | Microsoft Docs
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
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5dfa4d7a8669234cb7c154d18ce103626182b52a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce l'anello interno specificato di un'istanza **Polygongeometry**.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression*  
 Espressione **int** compresa tra 1 e il numero di anelli interni nell'istanza **geometry**.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
 Tipo OGC (Open Geospatial Consortium): **LineString**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo restituisce **null** se l'istanza **geometry** non è un poligono. Questo metodo genererà anche un'eccezione **ArgumentOutOfRangeException** se l'espressione è maggiore del numero di anelli. Il numero di anelli può essere restituito usando `STNumInteriorRing``()`.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `Polygon` e viene usato `STInteriorRingN()` per restituire l'anello interno del poligono come **LineString**.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

