---
title: Modifica della dimensione Product | Documenti Microsoft
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
ms.assetid: 8e3ffecd-7f40-41a8-8735-bc9858a310cb
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3bf90c339081a9e92965bda770c72c2624e3dbae
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-3-3---modifying-the-product-dimension"></a>Lezione 3-3-modifica della dimensione Product
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

Nelle attività di questo argomento si utilizzerà un calcolo denominato per fornire nomi più descrittivi per le linee di prodotti, si definirà una gerarchia nella dimensione Product e si specificherà il nome membro (Totale) per la gerarchia. Si raggrupperanno inoltre gli attributi in cartelle di visualizzazione.  
  
## <a name="adding-a-named-calculation"></a>Aggiunta di un calcolo denominato  
È possibile aggiungere un calcolo denominato a una tabella in una vista origine dati. Nell'attività seguente verrà creato un calcolo denominato che consente di visualizzare il nome completo della linea di prodotti.  
  
#### <a name="to-add-a-named-calculation"></a>Per aggiungere un calcolo denominato  
  
1.  Per aprire la vista origine dati **Adventure Works DW 2012** , fare doppio clic su **Adventure Works DW 2012** nella cartella **Viste origine dati** in Esplora soluzioni.  
  
2.  Nella parte inferiore del riquadro diagramma fare clic con il pulsante destro del mouse sull'intestazione di tabella **Product** , quindi scegliere **Nuovo calcolo denominato**.  
  
3.  Nella finestra di dialogo **Crea calcolo denominato** digitare **ProductLineName** nella casella **Nome colonna** .  
  
4.  Nella casella **Espressione** digitare o copiare e incollare l'istruzione **CASE** seguente:  
  
    ```  
    CASE ProductLine  
       WHEN 'M' THEN 'Mountain'  
       WHEN 'R' THEN 'Road'  
       WHEN 'S' THEN 'Accessory'  
       WHEN 'T' THEN 'Touring'  
       ELSE 'Components'  
    END  
    ```  
  
    Con questa istruzione **CASE** vengono creati nomi descrittivi per ogni linea di prodotti nel cubo.  
  
5.  Fare clic su **OK** per creare il calcolo denominato **ProductLineName** . Potrebbe essere necessario attendere alcuni istanti.  
  
6.  Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="modifying-the-namecolumn-property-of-an-attribute"></a>Modifica della proprietà NameColumn di un attributo  
  
#### <a name="to-modify-the-namecolumn-property-value-of-an-attribute"></a>Per modificare il valore della proprietà NameColumn di un attributo  
  
1.  Passare a Progettazione dimensioni per la dimensione Product. A tale scopo, fare doppio clic sulla dimensione **Product** nel nodo **Dimensioni** di Esplora soluzioni.  
  
2.  Nel riquadro **Attributi** della scheda **Struttura dimensione** selezionare **Product Line**.  
  
3.  Nella finestra Proprietà a destra dello schermo fare clic sul campo proprietà **NameColumn** nella parte inferiore della finestra, quindi fare clic sul pulsante con i puntini di sospensione (**…**) per aprire la finestra di dialogo **Colonna nome** . Per aprire la finestra Proprietà, potrebbe essere necessario fare clic sulla scheda **Proprietà** sul lato destro dello schermo.  
  
4.  Selezionare **ProductLineName** nella parte inferiore dell'elenco **Colonna di origine** , quindi fare clic su **OK**.  
  
    Il campo NameColumn ora contiene il testo **Product.ProductLineName (WChar)**. I membri della gerarchia dell'attributo **Product Line** ora vengono visualizzati con il nome completo della linea di prodotti anziché con un nome abbreviato.  
  
5.  Nel riquadro **Attributi** della scheda **Struttura dimensione** selezionare **Product Key**.  
  
6.  Nella finestra Proprietà fare clic nel campo proprietà **NameColumn** , quindi fare clic sui puntini di sospensione (**…**) per aprire la finestra di dialogo **Colonna nome** .  
  
7.  Selezionare **EnglishProductName** nell'elenco **Colonna di origine** , quindi fare clic su **OK**.  
  
    Il campo NameColumn ora contiene il testo **Product.EnglishProductName (WChar)**.  
  
8.  Nella finestra Proprietà scorrere verso l'alto, fare clic sul campo proprietà **Name** , quindi digitare **Product Name**.  
  
## <a name="creating-a-hierarchy"></a>Creazione di una gerarchia  
  
#### <a name="to-create-a-hierarchy"></a>Per creare una gerarchia  
  
1.  Trascinare l'attributo **Product Line** dal riquadro **Attributi** al riquadro **Gerarchie** .  
  
2.  Trascinare l'attributo **Model Name** dal riquadro **Attributi** alla cella **<new level>** nel riquadro **Gerarchie** , sotto il livello **Product Line** .  
  
3.  Trascinare l'attributo **Product Name** dal riquadro **Attributi** alla cella **<new level>** nel riquadro **Gerarchie** , sotto il livello **Model Name** . L'attributo Product Key è stato rinominato in Product Name nella sezione precedente.  
  
4.  Nel riquadro **Gerarchie** della scheda **Struttura dimensione** fare clic con il pulsante destro del mouse sulla barra del titolo della gerarchia **Gerarchia** , scegliere **Rinomina**, quindi digitare **Product Model Lines**.  
  
    Il nome della gerarchia è ora **Product Model Lines**.  
  
5.  Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="specifying-folder-names-and-all-member-names"></a>Impostazione dei nomi delle cartelle e dei nomi di membro Totale  
  
#### <a name="to-specify-the-folder-and-member-names"></a>Per impostare i nomi delle cartelle e dei membri  
  
1.  Nel riquadro **Attributi** tenere premuto CTRL e fare clic su ognuno dei seguenti attributi per selezionarli:  
  
    -   **Classe**  
  
    -   **Colore**  
  
    -   **Days To Manufacture**  
  
    -   **Reorder Point**  
  
    -   **Safety Stock Level**  
  
    -   **Dimensione**  
  
    -   **Size Range**  
  
    -   **Stile**  
  
    -   **Weight**  
  
2.  Nel campo proprietà **AttributeHierarchyDisplayFolder** della finestra Proprietà digitare **Stocking**.  
  
    Questi attributi sono stati ora raggruppati in un'unica cartella di visualizzazione.  
  
3.  Nel riquadro **Attributi** selezionare i seguenti attributi:  
  
    -   **Dealer Price**  
  
    -   **List Price**  
  
    -   **Standard Cost**  
  
4.  Digitare **Financial** nella cella di proprietà **AttributeHierarchyDisplayFolder**della finestra Proprietà.  
  
    Questi attributi sono stati ora raggruppati in una seconda cartella di visualizzazione.  
  
5.  Nel riquadro **Attributi** selezionare i seguenti attributi:  
  
    -   **End Date**  
  
    -   **Data inizio**  
  
    -   **Stato**  
  
6.  Digitare **History** nella cella di proprietà **AttributeHierarchyDisplayFolder**della finestra Proprietà.  
  
    Questi attributi sono stati ora raggruppati in una terza cartella di visualizzazione.  
  
7.  Selezionare la gerarchia **Product Model Lines** nel riquadro **Gerarchie** , quindi modificare la proprietà **AllMemberName** della finestra Proprietà in **All Products**.  
  
8.  Fare clic su un'area libera del riquadro **Gerarchie** , quindi modificare la proprietà **AttributeAllMemberName** nella parte superiore della finestra Proprietà in **All Products**.  
  
    Facendo clic su un'area libera è possibile modificare le proprietà della dimensione Product stessa. È inoltre possibile fare clic su **Product** nella parte superiore dell'elenco di attributi nel riquadro **Attributi** .  
  
9. Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="defining-attribute-relationships"></a>Definizione di relazioni tra attributi  
Se i dati sottostanti le supportano, è consigliabile definire relazioni tra gli attributi. La definizione di relazioni tra attributi consente di velocizzare l'elaborazione di dimensioni, partizioni e query. Per altre informazioni, vedere [Definire relazioni tra attributi](../analysis-services/multidimensional-models/attribute-relationships-define.md) e [Relazioni tra attributi](../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
#### <a name="to-define-attribute-relationships"></a>Per definire relazioni tra attributi  
  
1.  In **Progettazione dimensioni** per la dimensione Product fare clic sulla scheda **Relazioni tra attributi** .  
  
2.  Nel diagramma fare clic con il pulsante destro del mouse sull'attributo **Model Name** , quindi scegliere **Nuova relazione tra attributi**.  
  
3.  Nella finestra di dialogo **Crea relazione tra attributi** l'opzione **Attributo di origine** è impostata su **Model Name**. Impostare **Attributo correlato** su **Product Line**.  
  
    Nell'elenco **Tipo di relazione** lasciare il tipo di relazione impostato su **Flessibile** perché le relazioni tra i membri potrebbero cambiare nel corso del tempo. Ad esempio, un modello di prodotto può essere spostato in una linea di prodotti diversa.  
  
4.  Scegliere **OK**.  
  
5.  Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="reviewing-product-dimension-changes"></a>Esame delle modifiche alla dimensione Product  
  
#### <a name="to-review-the-product-dimension-changes"></a>Per esaminare le modifiche alla dimensione Product  
  
1.  Scegliere **Distribuisci Analysis Services Tutorial** dal menu [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Compila **di**.  
  
2.  Dopo la visualizzazione del messaggio **Distribuzione completata** , fare clic sulla scheda **Esplorazione** di **Progettazione dimensioni** per la dimensione **Product** , quindi fare clic sul pulsante Riconnetti sulla barra degli strumenti della finestra di progettazione.  
  
3.  Verificare che la gerarchia **Product Model Lines** sia selezionata nell'elenco **Gerarchia** , quindi espandere **All Products**.  
  
    Si noti che il nome del membro **Totale** viene visualizzato come **All Products**. La proprietà **AllMemberName** per la gerarchia è stata infatti modificata in **All Products** in un passaggio precedente della lezione. Inoltre, i membri del livello **Product Line** hanno ora nomi descrittivi anziché abbreviazioni costituite da una sola lettera.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Modifica della dimensione Date](../analysis-services/lesson-3-4-modifying-the-date-dimension.md)  
  
## <a name="see-also"></a>Vedere anche  
[Definire calcoli denominati in una vista origine dati & #40; Analysis Services & #41;](../analysis-services/multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
[Creare gerarchie definite dall'utente](../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
[Configurare il livello &#40;Totale&#41; per le gerarchie di attributi](../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
