---
title: sysssispackages (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdtspackages90_TSQL
- sysdtspackages90
dev_langs: TSQL
helpviewer_keywords: sysssispackages system table
ms.assetid: 66155dcd-dcdb-4e33-a242-1625828ad8d2
caps.latest.revision: "43"
author: spelluru
ms.author: spelluru
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5b694a277a235b373f1051878551ccca9537623f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni pacchetto salvato [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa tabella è archiviata nel **msdb** database.  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Identificatore univoco del pacchetto.|  
|**id**|**uniqueidentifier**|GUID del pacchetto.|  
|**Descrizione**|**nvarchar**|Descrizione del pacchetto (facoltativa).|  
|**CREATEDATE**|**datetime**|Data di creazione del pacchetto.|  
|**ID cartella**|**uniqueidentifier**|GUID della cartella logica in cui [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] elenca il pacchetto.|  
|**ownersid**|**varbinary**|ID di sicurezza (SID) univoco dell'utente che ha creato il pacchetto.|  
|**packagedata**|**image**|Il pacchetto.|  
|**packageformat**|**int**|Formato in cui viene salvato il pacchetto.<br /><br /> Il valore 2 indica che il pacchetto viene salvato nel [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] formato.<br /><br /> Il valore 3 indica che il pacchetto viene salvato in formato di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]o versione successiva.|  
|**PackageType**|**int**|Client che ha creato il pacchetto. I valori possibili sono i seguenti:<br /><br /> 0 (valore predefinito)<br /><br /> 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importazione / esportazione guidata)<br /><br /> 3 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replica)<br /><br /> 5 ([!INCLUDE[ssIS](../../includes/ssis-md.md)] progettazione)<br /><br /> 6 (Finestra di progettazione dei piani di manutenzione o procedura guidata).<br /><br /> <br /><br /> Si noti che i valori in questa colonna corrispondono al <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType> enumerazione.|  
|**versprinc**|**int**|Versione principale più recente del pacchetto.|  
|**verssecond**|**int**|Versione secondaria più recente del pacchetto.|  
|**verbuild**|**int**|Ultima build del pacchetto.|  
|**vercomments**|**nvarchar**|Commenti sulla versione del pacchetto.|  
|**verid**|**uniqueidentifier**|GUID della versione del pacchetto.|  
|**IsEncrypted**|**bit**|Valore booleano che indica se un pacchetto è crittografato.|  
|**readrolesid**|**varbinary**|Ruolo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che consente di caricare i pacchetti.|  
|**writerolesid**|**varbinary**|Ruolo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che consente di salvare i pacchetti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-packages.md)  
  
  