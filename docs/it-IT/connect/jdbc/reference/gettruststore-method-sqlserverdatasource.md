---
title: Metodo getTrustStore (SQLServerDataSource) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- getTrustStore Method (SQLServerDataSource)
apilocation:
- getTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 8f5850e4-8627-49a8-ba0e-b1f4014322a5
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5035c150e0e66b55893397d2d840a5a3239b51c8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="gettruststore-method-sqlserverdatasource"></a>Metodo getTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il percorso (incluso il nome file) del file trustStore del certificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getTrustStore()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene il percorso (incluso il nome di file) del file trustStore del certificato, o null se è impostato alcun valore.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà trustStore non è impostata, il [getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md) metodo restituisce null.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
