---
title: ParameterDirectionEnum | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ParameterDirectionEnum
helpviewer_keywords:
- ParameterDirectionEnum enumeration [ADO]
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba667bc530ce0fbfda9d9d6a788809fdbf5725c5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Specifica se il [parametro](../../../ado/reference/ado-api/parameter-object.md) rappresenta un parametro di input, un parametro di output, entrambi un input e un parametro di output o il valore restituito da una stored procedure.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|Valore predefinito. Indica che il parametro rappresenta un parametro di input.|  
|**adParamInputOutput**|3|Indica che il parametro rappresenta un parametro input e output.|  
|**adParamOutput**|2|Indica che il parametro rappresenta un parametro di output.|  
|**adParamReturnValue**|4|Indica che il parametro rappresenta un valore restituito.|  
|**adParamUnknown**|0|Indica che la direzione del parametro è sconosciuta.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.ParameterDirection.INPUT|  
|AdoEnums.ParameterDirection.INPUTOUTPUT|  
|AdoEnums.ParameterDirection.OUTPUT|  
|AdoEnums.ParameterDirection.RETURNVALUE|  
|AdoEnums.ParameterDirection.UNKNOWN|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|[Proprietà Direction](../../../ado/reference/ado-api/direction-property.md)|
