---
title: Creazione di un database (esercitazione) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: t-sql
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d3c3af391ebf47664107a00299533f59f50c0029
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="lesson-1-1---creating-a-database"></a>Lezione 1-1 - Creazione di un database
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Analogamente a numerose altre istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] , l'istruzione CREATE DATABASE ha un parametro obbligatorio, ovvero il nome del database. L'istruzione CREATE DATABASE dispone inoltre di numerosi parametri facoltativi, ad esempio il percorso su disco in cui si desidera inserire i file del database. Quando si esegue CREATE DATABASE senza parametri facoltativi, in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vengono utilizzati i valori predefiniti per molti di tali parametri. In questa esercitazione vengono utilizzati solo alcuni dei parametri facoltativi della sintassi.  
  
### <a name="to-create-a-database"></a>Per creare un database  
  
1.  In una finestra dell'editor di query digitare ma non eseguire il codice seguente:  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  Usare il puntatore per selezionare le parole `CREATE DATABASE`e quindi premere **F1**. Verrà aperto l'argomento relativo all'istruzione CREATE DATABASE della documentazione online di SQL Server. È possibile utilizzare questa tecnica per trovare la sintassi completa di CREATE DATABASE e delle altre istruzioni utilizzate in questa esercitazione.  
  
3.  Nell'editor di query premere **F5** per eseguire l'istruzione e creare un database denominato `TestData`.  
  
Quando si crea un database, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] esegue una copia del database **model** e le assegna il nome del database specificato. L'operazione dovrebbe richiedere solo alcuni secondi a meno che non si specifichi una dimensione iniziale per il database particolarmente grande come parametro facoltativo.  
  
> [!NOTE]  
> La parola chiave GO separa le istruzioni inviate in un singolo batch. GO è un elemento facoltativo se il batch contiene un'unica istruzione.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Esercitazione per la creazione di una tabella](../t-sql/lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a>Vedere anche  
[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
  
