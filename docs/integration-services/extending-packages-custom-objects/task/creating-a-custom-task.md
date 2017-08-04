---
title: "Creazione di un'attività personalizzata | Documenti Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom tasks [Integration Services], creating
ms.assetid: 42965c09-1782-4cdb-9ce1-216af4c23e0a
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3d804ae69154913f4c5239a6bec304f14c4b856d
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="creating-a-custom-task"></a>Creazione di un'attività personalizzata.
  I passaggi per la creazione di un'attività personalizzata sono simili a quelli richiesti per la creazione di qualsiasi altro oggetto personalizzato per [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:  
  
-   Creare una nuova classe che eredita dalla classe di base. Per un'attività, la classe di base è <xref:Microsoft.SqlServer.Dts.Runtime.Task>.  
  
-   Applicare alla classe l'attributo che identifica il tipo di oggetto. Per un'attività, l'attributo è <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>.  
  
-   Eseguire l'override dell'implementazione dei metodi e delle proprietà della classe di base. Per un'attività, questi includono i metodi <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> e <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>.  
  
-   Se si desidera, sviluppare un'interfaccia utente personalizzata. Per un'attività, è richiesta una classe tramite cui venga implementata l'interfaccia <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>.  
  
## <a name="getting-started-with-a-custom-task"></a>Introduzione alle attività personalizzate  
  
### <a name="creating-projects-and-classes"></a>Creazione di progetti e classi  
 Poiché tutte le attività gestite derivano dalla classe di base <xref:Microsoft.SqlServer.Dts.Runtime.Task>, il primo passaggio da completare quando si crea un'attività personalizzata consiste nel creare un progetto di libreria di classi nel linguaggio di programmazione gestito preferito e creare una classe che eredita dalla classe di base. In questa classe derivata si eseguirà l'override dei metodi e delle proprietà della classe di base per implementare la funzionalità personalizzata.  
  
 Nella stessa soluzione creare un secondo progetto di libreria di classi per l'interfaccia utente personalizzata. Per semplificare lo sviluppo, si consiglia di utilizzare un assembly distinto per l'interfaccia utente, perché in questo modo è possibile e ridistribuire la gestione connessione o la relativa interfaccia utente in modo indipendente.  
  
 Configurare entrambi i progetti per firmare gli assembly che verranno generati durante la compilazione utilizzando un file di chiave con nome sicuro.  
  
### <a name="applying-the-dtstask-attribute"></a>Applicazione dell'attributo DtsTask  
 Applicare l'attributo <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> alla classe creata per identificarla come attività. Questo attributo fornisce informazioni in fase di progettazione, ad esempio il nome, la descrizione e il tipo di attività.  
  
 Utilizzare la proprietà <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> per collegare l'attività alla relativa interfaccia utente personalizzata. Per ottenere il token di chiave pubblica che è necessario per questa proprietà, è possibile utilizzare **sn.exe -t** per visualizzare il token di chiave pubblica dal file di coppia di chiavi (con estensione snk) che si intende utilizzare per firmare l'assembly dell'interfaccia utente.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
## <a name="building-deploying-and-debugging-a-custom-task"></a>Compilazione, distribuzione e debug di attività personalizzate  
 I passaggi per la compilazione, la distribuzione e il debug di un'attività personalizzata in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sono simili a quelli richiesti per altri tipi di oggetti personalizzati. Per ulteriori informazioni, vedere [compilazione, distribuzione e debug di oggetti personalizzati](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'attività personalizzata](../../../integration-services/extending-packages-custom-objects/task/creating-a-custom-task.md)   
 [La codifica di un'attività personalizzata](../../../integration-services/extending-packages-custom-objects/task/coding-a-custom-task.md)   
 [Sviluppo di un'interfaccia utente per un'attività personalizzata](../../../integration-services/extending-packages-custom-objects/task/developing-a-user-interface-for-a-custom-task.md)  
  
  