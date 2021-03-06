---
title: Definizione dei set denominati | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 47254fd3-525f-4c35-b93d-316607652517
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 427d414c5b0545815dac427bb791c4767cfe975d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-6-2---defining-named-sets"></a>Lezione 6-2 - definizione di set denominati
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

Un set denominato è un'espressione MDX (Multidimensional Expressions) che restituisce un set di membri della dimensione. È possibile definire set denominati e salvarli come parte della definizione del cubo, nonché creare set denominati in applicazioni client. I set denominati possono essere creati combinando dati del cubo, operatori aritmetici, numeri e funzioni. I set denominati possono essere utilizzati dagli utenti nelle query MDX in applicazioni client, nonché per definire set nei sottocubi. Un sottocubo è una raccolta di set di crossjoin che limita lo spazio del cubo nel sottospazio definito per istruzioni successive. La definizione di uno spazio del cubo limitato costituisce un concetto fondamentale dello scripting MDX.  
  
I set denominati semplificano le query MDX e generano alias utili per espressioni set complesse utilizzate spesso. È possibile ad esempio definire un set denominato chiamato Large Resellers contenente il set di membri nella dimensione Reseller con il numero più elevato di dipendenti. Gli utenti finali potrebbero quindi utilizzare il set denominato Large Resellers nelle query, oppure utilizzarlo per definire un set in un sottocubo. Le definizioni dei set denominati vengono archiviate nei cubi, ma i loro valori si trovano solo nella memoria. Per creare un set denominato usare il comando **Nuovo set denominato** nella scheda **Calcoli** di Progettazione cubi. Per altre informazioni, vedere [Calcoli](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)e [Creare set denominati](../analysis-services/multidimensional-models/create-named-sets.md).  
  
Nelle procedure descritte in questo argomento si definiranno due set denominati: Core Products e Large Resellers.  
  
## <a name="defining-a-core-products-named-set"></a>Definizione di un set denominato Core Products  
  
1.  Passare alla scheda **Calcoli** di Progettazione cubi per il cubo di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial e fare clic su **Visualizzazione Form** nella barra degli strumenti.  
  
2.  Fare clic su **[Total Sales Ratio to All Products]** nel riquadro **Libreria script** e quindi fare clic su **Nuovo set denominato** nella barra degli strumenti della scheda **Calcoli** .  
  
    Quando si definisce un nuovo calcolo nella scheda **Calcoli** ricordare che i calcoli vengono risolti seguendo l'ordine di visualizzazione del riquadro **Libreria script** . Il calcolo selezionato all'interno di tale riquadro al momento della creazione di un nuovo calcolo ne determina l'ordine di esecuzione. Un nuovo calcolo viene definito immediatamente dopo il calcolo selezionato.  
  
3.  Nella casella **Nome** cambiare il nome del nuovo set denominato in **[Core Products]**.  
  
    Si noti nel riquadro **Libreria script** l'icona speciale che distingue un set denominato da un comando script o da un membro calcolato.  
  
4.  Nella scheda **Metadati** del riquadro **Strumenti di calcolo** , espandere **Prodotto**, **Categoria**, **Membri**e quindi **Tutti i prodotti**.  
  
    > [!NOTE]  
    > Se non è possibile visualizzare i metadati nel riquadro **Strumenti di calcolo** , fare clic su **Riconnetti** nella barra degli strumenti. Se questo sistema non funziona, può essere necessario elaborare il cubo o avviare l'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
5.  Trascinare **Bikes** nella casella **Espressione** .  
  
    È stata ora creata un'espressione set che restituirà il set di membri contenuti nella categoria Bike della dimensione Product.  
  
## <a name="defining-a-large-resellers-named-set"></a>Definizione di un set denominato Large Resellers  
  
1.  Fare clic con il pulsante destro del mouse su **[Core Products]** nel riquadro **Libreria script** e fare clic su **Nuovo set denominato**.  
  
2.  Nella casella **Nome** cambiare il nome di questo set denominato in **[Large Resellers]**.  
  
3.  Nella casella **Espressione** digitare **Exists()**.  
  
    La funzione Exists verrà usata per restituire il set di membri della gerarchia dell'attributo Reseller Name che si interseca con il set di membri della gerarchia dell'attributo Number of Employees contenente il maggior numero di dipendenti.  
  
4.  Nella scheda **Metadati** del riquadro **Strumenti di calcolo** , espandere la dimensione **Reseller** e quindi espandere la gerarchia dell'attributo **Reseller Name** .  
  
5.  Trascinare il livello **Nome rivenditore** all'interno delle parentesi per l'espressione set Exists.  
  
    Per restituire tutti i membri di questo set si userà la funzione Members. Per altre informazioni, vedere [Members &#40;Set&#41; &#40;MDX&#41;](../mdx/members-set-mdx.md).  
  
6.  Digitare un punto dopo l'espressione set parziale e quindi aggiungere la funzione Members. L'espressione dovrebbe avere l'aspetto sotto illustrato:  
  
    ```  
    Exists([Reseller].[Reseller Name].[Reseller Name].Members)  
    ```  
  
    Ora che è stato definito il primo set per l'espressione set Exists è possibile aggiungere il secondo set, ovvero il set di membri della dimensione Reseller contenente il maggior numero di dipendenti.  
  
7.  Nella scheda **Metadati** del riquadro **Strumenti di calcolo** , espandere **Number of Employees** nella dimensione Reseller, espandere **Members**e quindi espandere **All Resellers**.  
  
    Si noti che i membri di questa gerarchia dell'attributo non sono raggruppati.  
  
8.  Aprire Progettazione dimensioni per la dimensione **Reseller** e quindi fare clic su **Number of Employees** nel riquadro **Attributi** .  
  
9. Nella finestra Proprietà modificare la proprietà **DiscretizationMethod** in **Automatic**, quindi modificare la proprietà **DiscretizationBucketCount** in **5**. Per altre informazioni, vedere [Raggruppare membri di attributo &#40;discretizzazione&#41;](../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
10. Nel menu **Compila** di [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], scegliere **Distribuisci Analysis Services Tutorial**.  
  
11. Dopo aver completato la distribuzione, passare a Progettazione cubi per il cubo di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial e fare clic su **Riconnetti** nella barra degli strumenti della scheda **Calcoli** .  
  
12. Nella scheda **Metadati** del riquadro **Strumenti di calcolo** espandere **Number of Employees** nella dimensione **Reseller** , espandere **Members**, quindi espandere **All Resellers**.  
  
    Si noti che i membri di questa gerarchia di attributi sono ora contenuti in cinque gruppi, numerati da 0 a 4. Per visualizzare il numero di un gruppo, posizionare il puntatore sul gruppo per visualizzare una finestra popup. Per l'intervallo `2 -17`InfoTip deve contenere `[Reseller].[Number of Employees].&[0]`.  
  
    I membri di questa gerarchia dell'attributo sono raggruppati perché la proprietà DiscretizationBucketCount è impostata su **5** e la proprietà DiscretizationMethod è impostata su **Automatic**.  
  
13. Nell'espressione set Exists contenuta nella casella **Espressione** aggiungere una virgola dopo la funzione Members e prima della parentesi di chiusura, quindi trascinare **83 - 100** dal riquadro **Metadati** e posizionarlo dopo la virgola.  
  
    È stata ora completata l'espressione set Exists che restituirà il set di membri che si interseca con i due set specificati, ovvero il set di tutti i rivenditori e il set dei rivenditori con un numero di dipendenti compreso tra 83 e 100, quando il set denominato Large Resellers viene posto su un'asse.  
  
    Nella figura seguente viene illustrato il riquadro **Espressione** per il set denominato **[Large Resellers]** .  
  
    ![Nel riquadro espressioni di calcolo per [Large Resellers]](../analysis-services/media/l6-named-set-02.gif "riquadro espressioni di calcolo per [Large Resellers]")  
  
14. Nella barra degli strumenti della scheda **Calcoli** fare clic su **Visualizzazione Script**e quindi controllare i due set denominati appena aggiunti allo script di calcolo.  
  
15. Aggiungere una nuova riga nello script di calcolo, immediatamente precedente al primo comando CREATE SET, e quindi aggiungere allo script il testo seguente su una riga a se stante:  
  
    ```  
    /* named sets */  
    ```  
  
    Sono stati ora definiti due set denominati, entrambi visibili nel riquadro **Libreria script** . È ora possibile passare alla distribuzione di tali set denominati, nonché esplorare tali misure nel cubo di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.  
  
## <a name="browsing-the-cube-by-using-the-new-named-sets"></a>Esplorazione del cubo utilizzando i nuovi set denominati  
  
1.  Nel menu **Compila** di [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], scegliere **Distribuisci Analysis Services Tutorial**.  
  
2.  Al termine delle operazioni di distribuzione, fare clic sulla scheda **Esplorazione** e fare clic su **Riconnetti**.  
  
3.  Deselezionare la griglia nel riquadro Dati.  
  
4.  Aggiungere la misura **Reseller Sales-Sales Amount** all'area dati.  
  
5.  Espandere la dimensione Product, quindi aggiungere Category e Subcategory all'area riga, come illustrato nell'immagine seguente.  
  
    ![I membri dell'attributo Subcategory](../analysis-services/media/l6-named-set-03.gif "membri dell'attributo Subcategory")  
  
6.  Nel riquadro **Metadati** , nella dimensione **Product** trascinare **Core Products** nell'area filtro.  
  
    Si noti che nel cubo restano solo il membro **Bike** dell'attributo **Category** e i membri delle sottocategorie **Bike** , poiché il set denominato **Core Products** viene usato per definire un sottocubo. Questo sottocubo limita i membri dell'attributo **Category** nella dimensione **Product** all'interno del sottocubo ai membri del set denominato **Core Product** , come illustrato nella figura seguente.  
  
    ![Set di membri del prodotto principale denominato](../analysis-services/media/l6-named-set-04.gif "set denominato di membri del prodotto principale")  
  
7.  Nel riquadro **Metadati** espandere **Reseller**, quindi aggiungere **Large Resellers** all'area filtro.  
  
    Si noti che la misura Reseller Sales Amount nel riquadro Dati visualizza solo gli importi di vendita per rivenditori di bici di grandi dimensioni. Si noti inoltre che ora il riquadro Filtro visualizza i due set denominati utilizzati per definire questo sottocubo specifico, come illustrato nella figura seguente.  
  
    ![Riquadro filtro contenente due denominato imposta](../analysis-services/media/l6-named-set-05.gif "riquadro filtro contenente due denominato imposta")  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 7: Definizione di indicatori di prestazioni chiave & #40; Gli indicatori KPI & #41;](../analysis-services/lesson-7-defining-key-performance-indicators-kpis.md)  
  
## <a name="see-also"></a>Vedere anche  
[Calcoli](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)  
[Creare set denominati](../analysis-services/multidimensional-models/create-named-sets.md)  
  
  
  
