---
title: Criteri di supporto per SQL Server Native Client | Documenti Microsoft
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|applications
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 09c80cf4-23e6-4027-a24f-cdb9c87af811
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fcf6d00af82ce8a67fd3259d39118907713f97b9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="support-policies-for-sql-server-native-client"></a>Criteri di supporto per SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In questo argomento si illustrano le possibilità di utilizzo dei vari componenti di accesso ai dati con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="server-support"></a>Supporto server  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 supporta le connessioni a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] e al [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].  
  
## <a name="supported-operating-system-versions"></a>Versioni di sistema operativo supportate  
 Nella tabella seguente sono elencati i sistemi operativi supportati da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
|Versione di SQL Server Native Client|Sistemi operativi supportati|  
|--------------------------------------|---------------------------------|  
|SQL Server Native Client (SQL Server 2005)|Microsoft Windows 2000 Service Pack 4 o versione successiva<br /><br /> Microsoft Windows Server 2003 o versione successiva<br /><br /> Microsoft Windows XP Service Pack 1 o versione successiva<br /><br /> Microsoft Windows Vista (è richiesto [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service Pack 2 o versione successiva)<br /><br /> Microsoft Windows Server 2008 R2 (richiede [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service Pack 2 o versioni successive)|  
|SQL Server Native Client 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)])|Microsoft Windows Server 2003 Service Pack 2 o versione successiva<br /><br /> Microsoft Windows XP Service Pack 2 o versione successiva<br /><br /> Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2|  
|SQL Server Native Client 10.5 ([!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)])|Microsoft Windows Server 2003 Service Pack 2 o versione successiva<br /><br /> Microsoft Windows XP Service Pack 2 o versione successiva<br /><br /> Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2<br /><br /> Microsoft Windows 7|  
|SQL Server Native Client 11.0 ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] e [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)])|Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2<br /><br /> Microsoft Windows 7<br /><br /> Microsoft Windows 8<br /><br /> Microsoft Windows Server 2012|  
  
## <a name="ado-support-policies"></a>Criteri di supporto ADO  
 Le applicazioni ADO possono utilizzare il provider OLE DB SQLOLEDB incluso in Windows se non richiedono alcuna funzionalità di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva.  
  
 Applicazioni ADO possono utilizzare la versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client inclusa in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Le applicazioni ADO possono inoltre utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 (incluso in [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]). In tal caso, è tuttavia necessario che sia specificato `DataTypeCompatibility=80` nelle stringhe di connessione. Se nelle stringhe di connessione è presente `DataTypeCompatibility=80`, sono disponibili solo le funzionalità di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
## <a name="bcp-support-policies"></a>Criteri di supporto BCP  
 A partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], bcp.exe supporta file di dati appartenenti a versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non più vecchie di tre versioni rispetto alla versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] con cui viene fornito bcp.exe.  
  
## <a name="odbc-support-policies"></a>Criteri di supporto ODBC  
 Nelle applicazioni deve venire utilizzato il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] incluso nel sistema operativo Windows. Se l'applicazione è certificata per l'utilizzo con una versione specifica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, è possibile utilizzare il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="ole-db-support-policies"></a>Criteri di supporto OLE DB  
 Le applicazioni devono utilizzare il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] incluso con il sistema operativo Windows. Se l'applicazione è certificata per l'utilizzo con una versione specifica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, è possibile utilizzare il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 Le applicazioni OLE DB che non sono state certificate per l'utilizzo con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client possono utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client se `DataTypeCompatibility=80` è specificato nelle relative stringhe di connessione.  
  
 Le applicazioni OLE DB che utilizzano OLE DB Service Components possono utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client solo se specificano `DataTypeCompatibility=80` nelle stringhe di connessione. Tuttavia, delle funzionalità aggiunte dopo [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] saranno disponibili in questo caso.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di applicazioni con SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
