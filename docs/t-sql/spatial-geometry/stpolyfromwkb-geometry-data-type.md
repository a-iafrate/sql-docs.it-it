---
title: STPolyFromWKB (tipo di dati geometry) | Microsoft Docs
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
- STPolyFromWKB_TSQL
- STPolyFromWKB (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPolyFromWKB (geometry Data Type)
ms.assetid: 8e8f0c41-0c62-4919-9d4c-d37c93fdd31c
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 486bad91da8d9a18dca10ecdc309b2d1eab643de
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="stpolyfromwkb-geometry-data-type"></a>STPolyFromWKB (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un'istanza **geometryPolygon** di una rappresentazione WKB (Well-Known Binary) OGC (Open Geospatial Consortium).
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STPolyFromWKB ( 'WKB_polygon' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *WKB_polygon*  
 Rappresentazione WKB dell'istanza **geometryPolygon** che si desidera restituire. *WKB_polygon* è un'espressione **varbinary(max)**.  
  
 *SRID*  
 Espressione **int** che rappresenta l'identificatore SRID dell'istanza **geometryPolygon** da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
 Tipo OGC: **Polygon**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo genererà un'eccezione **FormatException** se l'input non è formattato in modo corretto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `STPolyFromWKB()` per creare un'istanza `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STPolyFromWKB(0x0103000000010000000400000000000000000014400000000000001440000000000000244000000000000014400000000000002440000000000000244000000000000014400000000000001440, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geometria statici OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

