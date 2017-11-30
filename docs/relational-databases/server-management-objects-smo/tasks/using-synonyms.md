---
title: Utilizzo dei sinonimi | Documenti Microsoft
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
caps.latest.revision: "49"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fd77a87430f9b9405c9b6bc900f924cba66368ad
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="using-synonyms"></a>Utilizzo dei sinonimi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Un sinonimo è un nome alternativo per un oggetto con ambito schema. In SMO i sinonimi sono rappresentati dal <xref:Microsoft.SqlServer.Management.Smo.Synonym> oggetto. L'oggetto <xref:Microsoft.SqlServer.Management.Smo.Synonym> è un elemento figlio dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database>. Ciò significa che i sinonimi sono validi solo all'interno dell'ambito del database nel quale sono definiti. Il sinonimo può tuttavia fare riferimento a oggetti in un altro database o in un'istanza remota di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 L'oggetto a cui viene assegnato un nome alternativo è noto come oggetto di base. La proprietà name dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Synonym> è il nome alternativo assegnato all'oggetto di base.  
  
## <a name="example"></a>Esempio  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per ulteriori informazioni, vedere [crea un Visual C &#35; Progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-synonym-in-visual-c"></a>Creazione di un sinonimo in Visual C#  
 Nell'esempio di codice viene illustrato come creare un sinonimo o un nome alternativo per un oggetto con ambito schema. Le applicazioni client possono utilizzare un singolo riferimento per l'oggetto di base mediante un sinonimo anziché utilizzare un nome costituito da più parti per fare riferimento all'oggetto di base.  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Synonym object variable by supplying the   
            //parent database, name, and schema arguments in the constructor.   
            //The name is also a synonym of the name of the base object.   
            Synonym syn = new Synonym(db, "Shop", "Sales");  
  
            //Specify the base object, which is the object on which   
            //the synonym is based.   
            syn.BaseDatabase = "AdventureWorks2012";  
            syn.BaseSchema = "Sales";  
            syn.BaseObject = "Store";  
            syn.BaseServer = srv.Name;  
  
            //Create the synonym on the instance of SQL Server.   
            syn.Create();  
        }  
```  
  
## <a name="creating-a-synonym-in-powershell"></a>Creazione di un sinonimo in PowerShell  
 Nell'esempio di codice viene illustrato come creare un sinonimo o un nome alternativo per un oggetto con ambito schema. Le applicazioni client possono utilizzare un singolo riferimento per l'oggetto di base mediante un sinonimo anziché utilizzare un nome costituito da più parti per fare riferimento all'oggetto di base.  
  
```powershell  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#And the database object corresponding to Adventureworks  
$db = $srv.Databases["AdventureWorks2012"]  
  
$syn = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Synonym `  
-argumentlist $db, "Shop", "Sales"  
  
#Specify the base object, which is the object on which the synonym is based.  
$syn.BaseDatabase = "AdventureWorks2012"  
$syn.BaseSchema = "Sales"  
$syn.BaseObject = "Store"  
$syn.BaseServer = $srv.Name  
  
#Create the synonym on the instance of SQL Server.  
$syn.Create()  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SYNONYM &#40;Transact-SQL&#41;](../../../t-sql/statements/create-synonym-transact-sql.md)  
  
  