---
title: Glossario ODBC | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], glossary
- glossary [ODBC]
ms.assetid: e8227000-1944-42e5-a881-1f549e1ff9d1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0bd26d6d8d95399bfe1126f56f6f9b8c2d176e71
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-glossary"></a>Glossario ODBC
## <a name="a"></a>A  
 **piano di accesso**  
 Un piano generato dal motore di database per eseguire un'istruzione SQL. Equivalente a codice eseguibile compilato da un linguaggio generazione terzo, ad esempio C.  
  
 **Funzione di aggregazione**  
 Una funzione che genera un singolo valore da un gruppo di valori, spesso usato con **GROUP BY** e **HAVING** clausole. Funzioni di aggregazione includono **AVG**, **conteggio**, **MAX**, **MIN**, e **somma**. Noto anche come *funzioni set*. *Vedere anche* funzione scalare.  
  
 **ANSI**  
 American National Standards Institute. L'API ODBC è basato sull'interfaccia ANSI a livello di chiamata.  
  
 **APD**  
 *Vedere* descrittore del parametro dell'applicazione (APD).  
  
 **API**  
 Interfaccia di programmazione di applicazioni. Un set di routine che un'applicazione utilizza per richiedere e svolgere servizi di livello inferiore. L'API ODBC include le funzioni ODBC.  
  
 **Applicazione**  
 Un programma eseguibile che chiama le funzioni dell'API ODBC.  
  
 **Descrittore del parametro dell'applicazione (APD)**  
 Oggetto descrittore che descrive i parametri dinamici utilizzati in un'istruzione SQL prima di qualsiasi conversione specificato dall'applicazione.  
  
 **Descrittore della riga di applicazione (ARD)**  
 Descrittore di tipo che rappresenta i metadati di colonna e i dati nel buffer dell'applicazione, che descrive una riga di dati dopo qualsiasi conversione di dati specificato dall'applicazione.  
  
 **ARD**  
 *Vedere* descrittore della riga di applicazione (ARD).  
  
 **la modalità autocommit**  
 Una modalità di commit delle transazioni in cui vengono eseguito il commit delle transazioni immediatamente dopo che vengono eseguite.  
  
## <a name="b"></a>B  
 **differenza di comportamento**  
 Una modifica di determinate funzionalità da ODBC 3*x* comportamento ODBC 2. *x* comportamento, o viceversa. Causato dalla modifica l'attributo di ambiente SQL_ATTR_ODBC_VERSION.  
  
 **Oggetto binario di grandi dimensioni (BLOB)**  
 Eventuali dati binari in un determinato numero di byte, ad esempio 255. In genere molto più tempo. Tali dati vengono in genere inviati ed recuperati dall'origine dei dati in parti. Noto anche come *dati long*.  
  
 **Associazione**  
 Come un verbo, l'operazione di associazione di una colonna in un set di risultati o un parametro in un'istruzione SQL con una variabile di applicazione. Come nome, l'associazione.  
  
 **offset di associazione**  
 Un valore aggiunto gli indirizzi di buffer di dati e gli indirizzi di buffer di lunghezza/indicatore per tutti gli indirizzi dei dati, che produce nuova colonna o parametro di associati.  
  
 **cursore rettangolare**  
 Un cursore in grado di recuperare più righe di dati alla volta.  
  
 **Buffer**  
 Una parte di memoria dell'applicazione utilizzata per passare dati tra l'applicazione e i driver. I buffer sono spesso in coppia: un *buffer dei dati* e un *buffer di lunghezza dati*.  
  
 **Byte**  
 Otto bit o a un ottetto. *Vedere anche* ottetto.  
  
## <a name="c"></a>C  
 **Tipo di dati C**  
 Il tipo di dati di una variabile in un programma C, in questo caso l'applicazione.  
  
 **catalog**  
 Il set di tabelle di sistema in un database che descrivono la forma del database. Noto anche come un *schema* o *dizionario dei dati*.  
  
 **funzione di catalogo**  
 Una funzione ODBC utilizzata per recuperare informazioni dal catalogo del database.  
  
 **CLI**  
 *Vedere* API.  
  
 **client/server**  
 Una strategia di accesso ai database in cui uno o più client di accedere ai dati tramite un server. In genere, i client implementano l'interfaccia utente durante l'accesso al database i controlli server.  
  
 **column**  
 Contenitore per un singolo elemento di informazioni in una riga. Noto anche come *campo*.  
  
 **commit**  
 Per rendere permanenti le modifiche in una transazione.  
  
 **Concorrenza**  
 La possibilità di più di una transazione di accedere agli stessi dati nello stesso momento.  
  
 **Livello di conformità**  
 Un set discreto di funzionalità supportate da un driver o l'origine dati. ODBC definisce i livelli di conformità di API e livelli di conformità di SQL.  
  
 **connessione**  
 Un'istanza specifica di un driver e l'origine dati.  
  
 **esplorazione di connessione**  
 La ricerca per le origini dati a cui connettersi. Esplorazione di connessione prevede diversi passaggi. Ad esempio, l'utente potrebbe esplorare innanzitutto la rete per i server e quindi selezionare un server specifico per un database.  
  
 **handle di connessione**  
 Un handle a una struttura di dati che contiene informazioni su una connessione.  
  
 **Riga corrente**  
 La riga attualmente a cui fa riferimento il cursore. Operazioni posizionate agiscono sulla riga corrente.  
  
 **cursor**  
 Un componente software che restituisce righe di dati per l'applicazione. Probabilmente denominato dopo il cursore intermittente in un computer terminal; come tale cursore indica la posizione sullo schermo, un cursore su un set di risultati indica la posizione corrente nel set di risultati.  
  
## <a name="d"></a>D  
 **buffer dei dati**  
 Un buffer utilizzato per passare i dati. Spesso associata con dati di un buffer è un *buffer di lunghezza dati*.  
  
 **dizionario dei dati**  
 *Vedere* catalogo.  
  
 **buffer di lunghezza dei dati**  
 Un buffer utilizzato per passare la lunghezza del valore di un corrispondente *buffer dei dati*. Il buffer di lunghezza dei dati viene inoltre utilizzato per archiviare gli indicatori, ad esempio se il valore dei dati è con terminazione null.  
  
 **Origine dati**  
 I dati che l'utente desidera accesso e il relativo sistema operativo associato, DBMS e piattaforma di rete (se presente).  
  
 **Tipo di dati**  
 Il tipo di una porzione di dati. ODBC definisce tipi di dati C e SQL. *Vedere anche* indicatore del tipo.  
  
 **colonna data-at-execution**  
 Una colonna per cui i dati vengono inviati dopo **SQLSetPos** viene chiamato. Tale nome perché i dati vengono inviati in fase di esecuzione piuttosto che viene inserito in un buffer di set di righe. Dati di tipo Long in genere vengono inviati in parti in fase di esecuzione.  
  
 **parametro data-at-execution**  
 Un parametro per il quale i dati vengono inviati dopo **SQLExecute** o **SQLExecDirect** viene chiamato. Tale nome perché i dati vengono inviati quando viene eseguita l'istruzione SQL anziché essere inserito in un buffer del parametro. Dati di tipo Long in genere vengono inviati in parti in fase di esecuzione.  
  
 **database**  
 Raccolta di dati in un DBMS discreta. Anche un DBMS.  
  
 **Motore di database**  
 Il software in un sistema DBMS che analizza ed esegue istruzioni SQL e accede ai dati fisici.  
  
 **DBMS**  
 Sistema di gestione di database. Livello del software tra il database fisico e l'utente. Il sistema DBMS gestisce tutte le operazioni di accesso al database.  
  
 **Driver basati su DBMS**  
 Un driver che accede ai dati fisici tramite un motore di database autonomo.  
  
 **DDL**  
 Data Definition Language. Istruzioni SQL che definiscono, anziché per modificare, i dati. Ad esempio, **CREATE TABLE**, **CREATE INDEX**, **GRANT**, e **revocare**.  
  
 **identificatore delimitato**  
 Un identificatore che è racchiuso tra virgolette singole identificatore in modo che può contenere caratteri speciali o corrispondere a parole chiave (noto anche come un identificatore tra virgolette).  
  
 **descrittore**  
 Una struttura di dati che contiene informazioni sui dati delle colonne o parametri dinamici. La rappresentazione fisica del descrittore non è definita. applicazioni di ottengono l'accesso diretto a un descrittore solo modificando i relativi campi chiamando le funzioni ODBC con l'handle di descrittore.  
  
 **database desktop**  
 DBMS progettato per essere eseguito su un personal computer. In genere, questi DBMS non forniscono un motore di database autonoma e deve essere accessibile tramite un driver basati su file. I motori di questi driver in genere risulteranno ridotte di supporto per SQL e le transazioni. Ad esempio, dBASE, Paradox, Btrieve o Microsoft® FoxPro.  
  
 **Diagnostica**  
 Un record contenente le informazioni diagnostiche sull'ultima funzione chiamata che è usato un handle specifico. I record di diagnostica sono associati a handle descrittore, connessione, l'istruzione e ambiente.  
  
 **DML**  
 Data Manipulation Language. Istruzioni SQL che modificano, anziché per definire, i dati. Ad esempio, **inserire**, **aggiornamento**, **eliminare**, e **selezionare**.  
  
 **Driver**  
 Routine della libreria che espone le funzioni dell'API ODBC. I driver sono specifici per un singolo DBMS.  
  
 **Gestione driver**  
 Una libreria di routine che gestisce l'accesso al driver per l'applicazione. Gestione Driver carica e scarica (o si connette a e si disconnette da) i driver e passa le chiamate a funzioni ODBC per il driver corretto.  
  
 **DLL di installazione del driver**  
 Una DLL che contiene funzioni di installazione e configurazione specifiche del driver.  
  
 **cursore dinamico**  
 Un cursore scorrevole è in grado di rilevare le righe aggiornate, eliminate o inserite nel set di risultati.  
  
 **SQL dinamico**  
 Tipo di embedded SQL SQL vengono create e compilate in fase di esecuzione istruzioni. *Vedere anche* SQL statico.  
  
## <a name="e"></a>E  
 **Embedded SQL**  
 Le istruzioni SQL che sono inclusi direttamente in un programma scritto in un altro linguaggio, ad esempio COBOL o ODBC C. non utilizzare embedded SQL. *Vedere anche* SQL statico *e* istruzioni SQL dinamiche.  
  
 **Ambiente**  
 Un contesto globale in cui si desidera accedere ai dati. associato all'ambiente sono le informazioni che sono globale in natura, ad esempio un elenco di tutte le connessioni in tale ambiente.  
  
 **handle di ambiente**  
 Un handle a una struttura di dati che contiene informazioni sull'ambiente.  
  
 **clausola di escape**  
 Una clausola in un'istruzione SQL.  
  
 **Eseguire**  
 Per eseguire un'istruzione SQL.  
  
## <a name="f"></a>F  
 **cursore a blocchi**  
 *Vedere* cursore rettangolare.  
  
 **operazione di recupero**  
 Per recuperare una o più righe da un set di risultati.  
  
 **field**  
 *Vedere* colonna.  
  
 **driver basati su file**  
 Un driver che accede ai dati fisici direttamente. In questo caso, il driver contiene un motore di database e funge da origine dati e del driver.  
  
 **origine dati file**  
 Un'origine dati per la connessione vengono archiviate informazioni in un file DSN.  
  
 **chiave esterna**  
 Una o più colonne in una tabella che corrispondano alla chiave primaria in un'altra tabella.  
  
 **con cursori forward-only**  
 Un cursore che può solo passare attraverso il set di risultati e in genere recupera solo una riga alla volta. La maggior parte dei database relazionali supportano solo i cursori forward-only.  
  
## <a name="h"></a>H  
 **Handle**  
 Un valore che identifica in modo univoco un elemento, ad esempio una struttura di dati o file. Gli handle sono significativi solo per il software che crea e li utilizza ma viene passato da altri software per identificare elementi. ODBC definisce gli handle per gli ambienti, le connessioni, istruzioni e descrittori.  
  
## <a name="i"></a>I  
 **Descrizione del parametro di implementazione (IPD)**  
 Oggetto descrittore che descrive i parametri dinamici utilizzati in un'istruzione SQL dopo la conversione specificata dall'applicazione.  
  
 **Descrittore della riga di implementazione (IRD)**  
 Oggetto descrittore che descrive una riga di dati prima di qualsiasi conversione specificato dall'applicazione.  
  
 **Programma di installazione di DLL**  
 Una DLL che vengono installati i componenti ODBC e configura le origini dati.  
  
 **Miglioramento dell'integrità**  
 Un subset di SQL è progettato per mantenere l'integrità di un database.  
  
 **livello di conformità di interfaccia**  
 Il livello di interfaccia ODBC 3.7 supportata da un driver. può essere componenti di base, livello 1 o 2 di livello.  
  
 **Interoperabilità**  
 La possibilità di un'applicazione a usare lo stesso codice quando l'accesso ai dati in diversi DBMS.  
  
 **IPD**  
 *Vedere* descrittore del parametro di implementazione (IPD).  
  
 **IRD**  
 *Vedere* descrittore della riga di implementazione (IRD).  
  
 **ISO/IEC**  
 Standard internazionali organizzazione/International Electrotechnical Commission. L'API ODBC è basato sull'interfaccia ISO/IEC a livello di chiamata.  
  
## <a name="j"></a>J  
 **Creare un join**  
 Un'operazione in un database relazionale che collega le righe in due o più tabelle facendo corrispondere i valori nelle colonne specificate.  
  
## <a name="k"></a>K  
 **chiave**  
 Una o più colonne i cui valori identificano una riga. *Vedere anche* chiave esterna *e* chiave primaria.  
  
 **Keyset**  
 Un set di chiavi usate da un cursore misto o basati su keyset di recupero di righe.  
  
 **cursori basati su keyset**  
 Un cursore scorrevole che rileva le righe aggiornate ed eliminate tramite un keyset.  
  
## <a name="l"></a>L  
 **literal**  
 Una rappresentazione dei caratteri di un valore effettivo dei dati in un'istruzione SQL.  
  
 **Il blocco**  
 Il processo mediante il quale un DBMS limita l'accesso a una riga in un ambiente multiutente. Il sistema DBMS in genere imposta un bit su una riga o pagina fisica che contiene una riga che indica la riga o pagina è bloccata.  
  
 **dati di tipo Long**  
 I dati binari o character superano una certa lunghezza, ad esempio 255 byte o caratteri. In genere molto più tempo. Tali dati vengono in genere inviati ed recuperati dall'origine dei dati in parti. Noto anche come *BLOB*s o *CLOB*s.  
  
## <a name="m"></a>M  
 **origine dati macchina**  
 Un'origine dati per la connessione vengono archiviate informazioni sul sistema (ad esempio, il Registro di sistema).  
  
 **modalità di commit manuale**  
 Una modalità di commit transazione in cui le transazioni devono essere esplicitamente eseguito il commit chiamando **SQLTransact**.  
  
 **Metadati**  
 Dati che descrivono un parametro in un'istruzione SQL o una colonna in un set di risultati. Ad esempio, il tipo di dati, lunghezza in byte e una precisione di un parametro.  
  
 **driver a più livelli**  
 *Vedere* driver basati su DBMS.  
  
## <a name="n"></a>N  
 **Valore NULL**  
 Non hanno nessun valore assegnato in modo esplicito. In particolare, un valore NULL è diverso da zero o uno spazio vuoto.  
  
## <a name="o"></a>O  
 **ottetti**  
 Otto bit o a un byte. *Vedere anche* byte.  
  
 **lunghezza dell'ottetto**  
 La lunghezza in ottetti di un buffer o i dati in che esso contenuti.  
  
 **ODBC**  
 Aprire la connettività del Database. Specifica per un'API che definisce un set standard di routine a cui un'applicazione può accedere a dati in un'origine dati.  
  
 **Amministratore ODBC**  
 Un programma eseguibile che chiama il programma di installazione DLL per configurare le origini dati.  
  
 Apri gruppo  
 Una società che pubblica standard. In particolare, vengono pubblicati gli standard di gruppo di accesso SQL (SAG).  
  
 **Concorrenza ottimistica**  
 Una strategia per aumentare la concorrenza in cui le righe non bloccate. Prima di essere aggiornati o eliminati, un cursore controlla per vedere se sono state modificate dall'ultima lettura. In questo caso, update o delete ha esito negativo. *Vedere anche* concorrenza pessimistica.  
  
 **outer join**  
 Un join in quali righe non corrispondenti e corrispondenti vengono restituite. I valori di tutte le colonne della tabella non corrispondenti nelle righe non corrispondenti vengono impostati su NULL.  
  
 **proprietario**  
 Il proprietario di una tabella.  
  
## <a name="p"></a>P  
 **parameter**  
 Una variabile in un'istruzione SQL, è contrassegnato con un marcatore di parametro o un punto interrogativo (?). I parametri sono associati a variabili di applicazione e i relativi valori recuperati quando viene eseguita l'istruzione.  
  
 **descrittore del parametro**  
 Un descrittore che descrive i parametri in fase di esecuzione utilizzati in un'istruzione SQL, sia prima di qualsiasi conversione specificato dall'applicazione (un descrittore del parametro dell'applicazione o APD) o dopo qualsiasi conversione specificato dall'applicazione (un'implementazione descrittore del parametro o IPD).  
  
 **Matrice di parametri operazione**  
 Matrice contenente i valori che è possibile impostare un'applicazione per indicare che il parametro corrispondente deve essere ignorato un **SQLExecDirect** o **SQLExecute** operazione.  
  
 **Matrice di stato di parametro**  
 Matrice che contiene lo stato di un parametro dopo una chiamata a **SQLExecDirect** o **SQLExecute**.  
  
 **concorrenza pessimistica**  
 Una strategia per l'implementazione serializzabilità, in cui le righe vengono bloccate in modo che altre transazioni non è possibile modificarle. *Vedere anche* concorrenza ottimistica *e* serializzabilità.  
  
 **operazione posizionata**  
 Qualsiasi operazione che agisce sulla riga corrente. Ad esempio, posizionato aggiornamento ed eliminazione di istruzioni, **SQLGetData**, e **SQLSetPos**.  
  
 **istruzione di aggiornamento posizionato**  
 Un'istruzione SQL utilizzata per aggiornare i valori nella riga corrente.  
  
 **istruzione delete posizionata**  
 Un'istruzione SQL utilizzata per eliminare la riga corrente.  
  
 **Preparare**  
 Per compilare un'istruzione SQL. La preparazione di un'istruzione SQL viene creato un piano di accesso.  
  
 **chiave primaria**  
 Una o più colonne che identifica in modo univoco una riga in una tabella.  
  
 **procedure**  
 Un gruppo di uno o più precompilata di istruzioni SQL che vengono archiviate come un oggetto denominato in un database.  
  
 **colonna procedura**  
 Un argomento nella chiamata di routine, il valore restituito da una stored procedure o una colonna in un set di risultati creato da una stored procedure.  
  
## <a name="q"></a>Q  
 **Qualificatore**  
 Un database che contiene una o più tabelle.  
  
 **query**  
 Un'istruzione SQL. Talvolta utilizzato per indicare un **selezionare** istruzione.  
  
 **quoted identifier**  
 Un identificatore che è racchiuso tra virgolette singole identificatore in modo che può contenere caratteri speciali o corrispondere a parole chiave (note anche come un identificatore delimitato SQL-92).  
  
## <a name="r"></a>L  
 **radice**  
 La base di un numero di sistema. In genere 2 o 10.  
  
 **Record**  
 *Vedere* riga.  
  
 **set di risultati**  
 Il set di righe creato tramite l'esecuzione di un **selezionare** istruzione.  
  
 **Codice restituito**  
 Il valore restituito da una funzione ODBC.  
  
 **eseguire il rollback**  
 Per restituire i valori modificati da una transazione allo stato originale.  
  
 **Riga**  
 Un set di colonne correlate che descrivono un'entità specifica. Noto anche come un *record*.  
  
 **descrittore della riga**  
 Un descrittore che descrive le colonne di un set di risultati, la prima conversione specificato dall'applicazione (un descrittore della riga di implementazione o IRD) o dopo qualsiasi conversione specificato dall'applicazione (un descrittore della riga di applicazione o ARD).  
  
 **Matrice di operazione di riga**  
 Matrice contenente i valori che è possibile impostare un'applicazione per indicare che la riga corrispondente deve essere ignorata un **SQLSetPos** operazione.  
  
 **Matrice di stato di riga**  
 Matrice che contiene lo stato di una riga dopo una chiamata a **SQLFetch**, **SQLFetchScroll**, o **SQLSetPos**.  
  
 **set di righe**  
 Il set di righe restituite in un'unica operazione di recupero da un cursore a blocchi.  
  
 **buffer di set di righe**  
 I buffer associati alle colonne di un set di risultati in cui i dati per un intero set di righe viene restituiti.  
  
## <a name="s"></a>S  
 **SAG**  
 *Vedere* gruppo di accesso SQL (SAG).  
  
 **funzione scalare**  
 Una funzione che genera un singolo valore da un singolo valore. Ad esempio, una funzione che viene modificato nel caso di dati di tipo carattere.  
  
 **schema**  
 *Vedere* catalogo.  
  
 **con cursori scorrevoli**  
 Un cursore che può spostarsi in avanti o indietro tra il set di risultati.  
  
 **Serializzabilità è infatti**  
 Se l'esecuzione simultanea di due transazioni producono un risultato di esecuzione seriale (o sequenziale) di tali transazioni. Le transazioni serializzabili sono tenute a mantenere l'integrità del database.  
  
 **database del server**  
 DBMS progettato per essere eseguito in un ambiente client/server. Questi DBMS forniscono un motore di database autonomo che fornisce supporto completo per le transazioni e SQL. Vi si accede tramite driver basati su DBMS. Ad esempio, Oracle, Informix, DB/2 o Microsoft® SQL Server.  
  
 **set (funzione)**  
 *Vedere* funzione di aggregazione.  
  
 **DLL di installazione**  
 *Vedere* DLL di installazione del driver *e* DLL di installazione del convertitore.  
  
 **livello di singolo driver**  
 *Vedere* driver basati su file.  
  
 **SQL**  
 Structured Query Language. Linguaggio utilizzato dai database relazionali per eseguire una query, aggiornare e gestire i dati.  
  
 **Gruppo di accesso SQL (SAG)**  
 Un settore consorzio di società in questione con SQL DBMS. Interfaccia a livello di chiamata dell'Open Group è basato sul lavoro svolto originariamente dal gruppo di accesso SQL.  
  
 **Livello di conformità SQL**  
 Il livello di grammatica SQL-92 supportato da un driver. può essere una voce, FIPS transitorio, intermedio o Full.  
  
 **Tipo di dati SQL**  
 Il tipo di dati di una colonna o parametro come viene memorizzato nell'origine dati.  
  
 **SQLSTATE**  
 Un valore di cinque caratteri che indica un errore specifico.  
  
 **Istruzione SQL**  
 Una frase completa in SQL che inizia con una parola chiave e una descrizione completa di un'azione da intraprendere. Ad esempio, selezionare * FROM Orders. Istruzioni SQL non devono essere confuso con le istruzioni.  
  
 **state**  
 Una condizione ben definita di un elemento. Ad esempio, una connessione dispone di sette stati, inclusi i dati non allocati, allocati, connessi e debbano essere applicati. Alcune operazioni possono essere eseguite solo quando è un elemento in un determinato stato. Ad esempio, una connessione può essere liberata solo quando si trova in uno stato allocato e non, ad esempio, quando è in uno stato di connessione.  
  
 **transizione di stato**  
 Lo spostamento di un elemento da uno stato a un altro. ODBC definisce le transizioni di stato rigorosi per ambienti, le connessioni e le istruzioni.  
  
 **istruzione**  
 Un contenitore per tutte le informazioni relative a un'istruzione SQL. Le istruzioni non devono essere confuso con le istruzioni SQL.  
  
 **handle di istruzione**  
 Un handle a una struttura di dati che contiene informazioni su un'istruzione.  
  
 **cursore statico**  
 Un cursore scorrevole che non è in grado di rilevare gli aggiornamenti, Elimina o inserisce nel set di risultati. In genere implementata mediante la copia del set di risultati.  
  
 **SQL statico**  
 Tipo di embedded SQL, le istruzioni SQL sono hardcoded e compilate quando viene compilato il resto del programma. *Vedere anche* istruzioni SQL dinamiche.  
  
 **Stored procedure**  
 *Vedere* stored procedure.  
  
## <a name="t"></a>T  
 **table**  
 Una raccolta di righe.  
  
 **thunk**  
 La conversione di 16 bit indirizzi indirizzi a 32 bit, o viceversa, quando vengono utilizzate applicazioni a 16 bit con driver ODBC a 32 bit.  
  
 **transazione**  
 Unità atomica di lavoro. Il lavoro in una transazione deve essere completato nel suo complesso; Se qualsiasi parte della transazione non riesce, l'intera transazione avrà esito negativo.  
  
 **Isolamento delle transazioni**  
 L'atto di isolamento transazione dagli effetti di tutte le altre transazioni.  
  
 **Livello di isolamento delle transazioni**  
 Misura l'accuratezza una transazione è isolata. Sono disponibili cinque livelli di isolamento delle transazioni: Read Uncommitted, Read Committed, Repeatable Read, Serializable e controllo delle versioni.  
  
 **funzione di conversione DLL**  
 Una DLL utilizzato per convertire i dati da un set di caratteri da un altro.  
  
 **DLL di installazione di funzione di conversione**  
 Una DLL che contiene funzioni di installazione e configurazione specifiche del convertitore.  
  
 **commit in due fasi**  
 Il processo di commit di una transazione distribuita in due fasi. Nella prima fase, l'elaborazione delle transazioni controlla che tutte le parti della transazione possono essere eseguito il commit. Nella seconda fase, tutte le parti della transazione vengono eseguito il commit. Se qualsiasi parte della transazione indica che non può essere eseguito il commit nella prima fase, la seconda fase non viene eseguito. ODBC non supporta i commit in due fasi.  
  
 **indicatore del tipo**  
 Valore integer passato a o restituito da una funzione ODBC per indicare il tipo di dati di una variabile di applicazione, un parametro o una colonna. ODBC definisce gli indicatori di tipo per tipi di dati C e SQL.  
  
## <a name="v"></a>V  
 **Visualizzazione**  
 Un modo alternativo per visualizzare i dati in una o più tabelle. In genere è possibile creare una vista come un subset delle colonne di una o più tabelle. In ODBC, le visualizzazioni sono in genere equivalenti alle tabelle.
