---
title: STIsSimple (tipo di dati geometry) | Microsoft Docs
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
- STIsSimple_TSQL
- STIsSimple (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsSimple (geometry Data Type)
ms.assetid: da8f45d4-4f9c-405d-b883-760eb5344a71
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bea42a649318a7658c108634d165656cf9dce0ca
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="stissimple-geometry-data-type"></a>STIsSimple (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce 1 se un'istanza **geometry** è semplice, in base alla definizione di Open Geospatial Consortium (OGC). Restituisce 0 se l'istanza **geometry** non è semplice.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STIsSimple ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Per essere semplice, un'istanza **geometry** deve soddisfare tutti i requisiti seguenti:  
  
-   Ogni figura dell'istanza non deve intersecarsi, salvo agli endpoint.  
  
-   Le figure dell'istanza non possono intersecarsi tra di loro in un punto non esistente in entrambi i loro limiti.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza non semplice `LineString` che interseca se stessa e viene utilizzato `STIsSimple()` per verificare se l'istanza `LineString` è semplice.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STIsSimple();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

