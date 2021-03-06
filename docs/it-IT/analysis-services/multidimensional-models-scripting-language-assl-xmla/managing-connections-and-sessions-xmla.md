---
title: Gestione di connessioni e sessioni (XMLA) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4c11bc2a626f619c42df8bd22226fd59cb900749
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="managing-connections-and-sessions-xmla"></a>Gestione di connessioni e sessioni (XMLA)
  *Le informazioni sullo stato* è una condizione durante il quale il server mantiene l'identità e il contesto di un client tra le chiamate di metodo. *Senza stato* è una condizione durante il quale il server non ricorda l'identità e il contesto di un client dopo il completamento di una chiamata al metodo.  
  
 Per fornire le informazioni sullo stato, XML for Analysis (XMLA) supporta *sessioni* che consentono una serie di istruzioni da eseguire insieme. Un esempio di tale serie di istruzioni potrebbe essere la creazione di un membro calcolato da utilizzare in query successive.  
  
 In genere le sessioni in XMLA si comportano nel modo indicato dalla specifica OLE DB 2.6 e descritto di seguito:  
  
-   Le sessioni definiscono l'ambito del contesto dei comandi e delle transazioni.  
  
-   È possibile eseguire più comandi nel contesto di una singola sessione.  
  
-   Supporto delle transazioni nel contesto di XMLA è tramite comandi specifici del provider inviati con il [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
 XMLA definisce una modalità per supportare sessioni in un ambiente Web in modo analogo all'approccio utilizzato dal protocollo DAV (Distributed Authoring and Versioning) per implementare il blocco in un ambiente a regime di controllo libero. L'analogia con il protocollo DAV consiste nel fatto che è consentita la scadenza delle sessioni nel provider per diversi motivi, ad esempio se si verifica un timeout o un errore di connessione. Quando le sessioni sono supportate, i servizi Web devono essere consapevoli e pronti per gestire di set interrotti di comandi che devono essere riavviati.  
  
 La specifica SOAP (Simple Object Access Protocol ) definita dal World Wide Web Consortium (W3C) consiglia l'utilizzo di intestazioni SOAP per la compilazione di nuovi protocolli nella parte superiore dei messaggi SOAP. Nella tabella seguente vengono elencati gli elementi dell'intestazione SOAP e gli attributi che XMLA definisce per avviare, gestire e chiudere una sessione.  
  
|Intestazione SOAP|Description|  
|-----------------|-----------------|  
|BeginSession|Questa intestazione richiede al provider di creare una nuova sessione. Il provider deve rispondere costruendo una nuova sessione e restituendo l'ID di sessione come parte dell'intestazione Session nella risposta SOAP.|  
|SessionId|Area del valore che contiene l'ID di sessione da utilizzare in ogni chiamata al metodo per il resto della sessione. Nella risposta SOAP il provider invia questo tag, che deve essere inviato inoltre anche dal client con ogni elemento dell'intestazione Session.|  
|Sessione|Per ogni chiamata al metodo che si verifica nella sessione, questa intestazione deve essere utilizzata e l'ID di sessione deve essere incluso nell'area del valore dell'intestazione.|  
|EndSession|Per terminare la sessione, utilizzare questa intestazione. L'ID di sessione deve essere incluso con l'area del valore.|  
  
> [!NOTE]  
>  Un ID di sessione non garantisce che una sessione rimanga valida. Se la sessione scade (ad esempio se si verifica un timeout o se la connessione si interrompe), il provider può scegliere di terminare le azioni di tale sessione e di eseguirne il rollback. Di conseguenza, tutte le chiamate al metodo successive eseguite dal client su un ID di sessione avranno esito negativo e restituiranno un errore che indica che la sessione non è valida. Un client deve gestire questa condizione e deve essere preparato per inviare nuovamente le chiamate al metodo della sessione a partire dall'inizio.  
  
## <a name="legacy-code-example"></a>Codice di esempio legacy  
 Nell'esempio seguente viene illustrato come sono supportate le sessioni.  
  
1.  Per avviare la sessione, aggiungere un'intestazione BeginSession in SOAP alla chiamata al metodo XMLA in uscita dal client. L'area del valore è inizialmente vuota perché l'ID di sessione non è ancora noto.  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  Il messaggio di risposta SOAP dal provider include l'ID di sessione nell'area di intestazione restituita, usare il tag di intestazione XMLA \<SessionId >.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  Per ogni chiamata al metodo nella sessione, l'intestazione Session deve essere aggiunta e deve contenere l'ID di sessione restituito dal provider.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  Quando la sessione è stata completata, il \<EndSession > viene utilizzato il tag, che contiene il valore di ID di sessione correlato.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
