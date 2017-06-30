---
title: Creare modelli personalizzati | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: 7472e4f1f5284dcae032b057fc6d9d0caf3660b8
ms.contentlocale: it-it
ms.lasthandoff: 06/23/2017

---
# <a name="lesson-3-2---create-custom-templates"></a>Lezione 3-2 - Creare modelli personalizzati
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] include modelli da usare per molte attività comuni. L'effettivo vantaggio dei modelli, tuttavia, consiste nella possibilità di creare un modello personalizzato per uno script complesso che è necessario creare frequentemente. In questa esercitazione verranno illustrate le procedure per la creazione di uno script semplice con un numero limitato di parametri, ma i modelli risultano utili anche per script complessi e ripetitivi.  
  
## <a name="using-custom-templates"></a>Utilizzo di modelli personalizzati  
  
#### <a name="to-create-a-custom-template"></a>Per creare un modello personalizzato  
  
1.  In Esplora modelli espandere **Modelli di SQL Server**, fare clic con il pulsante destro del mouse su **Stored procedure**, scegliere **Nuova**e selezionare **Cartella**.  
  
2.  Digitare **Custom** come nome della nuova cartella del modello e premere INVIO.  
  
3.  Fare clic con il pulsante destro del mouse su **Custom**, scegliere **Nuovo**e selezionare **Modello**.  
  
4.  Digitare **WorkOrdersProc** come nome del nuovo modello e premere **INVIO**.  
  
5.  Fare clic con il pulsante destro del mouse su **WorkOrdersProc**e scegliere **Modifica**.  
  
6.  Nella finestra di dialogo **Connetti al motore di database** verificare le informazioni di connessione e fare clic su **Connetti**.  
  
7.  Nell'editor di query digitare lo script seguente per creare una stored procedure che ricerca negli ordini una determinata parte, in questo caso Blade. (È possibile copiare e incollare il codice dalla finestra dell'esercitazione).  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  Premere F5 per eseguire lo script e creare la procedura **WorkOrdersForBlade** .  
  
9. In Esplora oggetti fare clic con il pulsante destro del mouse sul server e scegliere **Nuova query**. Verrà visualizzata una nuova finestra dell'editor di query.  
  
10. Nell'editor di query digitare **EXECUTE dbo.WorkOrdersForBlade**e premere F5 per eseguire la query. Verificare che nel riquadro **Risultati** sia visualizzato l'elenco di ordini di blade richiesto.  
  
11. Modificare lo script del modello, quello del passaggio 7, sostituendo il nome del prodotto Blade con il parametro ***\<*product_name**, **nvarchar(50)**, **name*>***, in quattro punto.  
  
    > [!NOTE]  
    > Per i parametri sono necessari tre elementi, ovvero il nome che si desidera restituire, il tipo di dati e il valore predefinito.  
  
12. Lo script dovrebbe corrispondere a quanto segue:  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. Scegliere **Salva WorkOrdersProc.sql** dal menu **File** per salvare il modello.  
  
#### <a name="to-test-the-custom-template"></a>Per verificare il funzionamento del modello personalizzato  
  
1.  In Esplora modelli espandere **Stored Procedure**e **Custom**e fare doppio clic su **WorkOrderProc**.  
  
2.  Nella finestra di dialogo **Connetti al motore di database** specificare le informazioni di connessione e fare clic su **Connetti**. Verrà visualizzata una nuova finestra dell'editor di query che include il contenuto del modello **WorkOrderProc** .  
  
3.  Scegliere **Imposta valori per parametri modello** dal menu **Query**.  
  
4.  Nella finestra di dialogo **Replace Template Parameters** (Sostituisci parametri modello), come valore di **product_name** , digitare **FreeWheel** , sovrascrivendo il contenuto predefinito, e fare clic su **OK** per chiudere la finestra di dialogo **Replace Template Parameters** (Sostituisci parametri modello) e modificare lo script nell'editor di query.  
  
5.  Premere F5 per eseguire la query e creare la procedura.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Salvare gli script come progetti o soluzioni](../../tools/sql-server-management-studio/lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
  
