---
title: Set di righe DISCOVER_LITERALS | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DISCOVER_LITERALS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_LITERALS rowset
ms.assetid: 1bf0a2e2-a419-4c25-b271-37dfa44de2ea
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: dc239de2abb609aa035880c0cf9dd9217343c08c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="discoverliterals-rowset"></a>Set di righe DISCOVER_LITERALS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Restituisce informazioni sui valori letterali, inclusi tipi e valori di dati, supportati dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA (XML for Analysis).  
  
 Se si chiama il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo con il **DISCOVER_LITERALS** valore di enumerazione nel [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) elemento, il **Discover** metodo restituisce il **DISCOVER_LITERALS** set di righe.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_LITERALS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**LiteralName**|**DBTYPE_WSTR**||Nome del valore letterale descritto nella riga.<br /><br /> Ad esempio: **DBLITERAL_LIKE_PERCENT**|  
|**LiteralValue**|**DBTYPE_WSTR**||Valore letterale effettivo.<br /><br /> Ad esempio, se **LiteralName** è **DBLITERAL_LIKE_PERCENT** e il carattere di percentuale (**%**) consente di ricercare zero o più caratteri in una clausola LIKE, il valore del **LiteralValue** colonna è "**%**".|  
|**LiteralInvalidChars**|**DBTYPE_WSTR**||Caratteri non validi nel valore letterale.<br /><br /> Ad esempio, se i nomi di tabella possono contenere qualsiasi elemento diverso da un carattere numerico, questa stringa è "**0123456789**".|  
|**LiteralInvalidStartingChars**|**DBTYPE_WSTR**||Caratteri non validi come primo carattere del valore letterale. Se il valore letterale può iniziare con qualsiasi carattere valido, si tratta di **null**.|  
|**LiteralMaxLength**|**DBTYPE_I4**||Numero massimo di caratteri nel valore letterale. Se non è presente un valore massimo o tale valore è sconosciuto, il valore sarà –1.|  
|**LiteralNameEnumValue**|**DBTYPE_I4**|||  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_LITERALS** set di righe può essere limitato sulle colonne nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**LiteralName**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i set di righe dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Set di righe DISCOVER_KEYWORDS & #40; XMLA & #41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)  
  
  
