---
title: DENY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DENY
- DENY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- schema-level securables [SQL Server]
- security [SQL Server], denying access
- DENY statement
- permissions [SQL Server], denying
- server-level securables [SQL Server]
- inherited security settings [SQL Server]
- denying permissions [SQL Server], DENY statement
- principal security [SQL Server]
- database-level securables [SQL Server]
- denying permissions [SQL Server]
ms.assetid: c32d1e01-9ee9-4665-a516-fcfece58078e
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 08f2d3c555dceef71e331b6df8727afb5780b86b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="deny-transact-sql"></a>DENY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Nega un'autorizzazione a un'entità. Impedisce a tale entità di ereditare l'autorizzazione tramite l'appartenenza al ruolo o al gruppo. DENY ha la precedenza su tutte le autorizzazioni, ad eccezione del fatto che non si applica a proprietari di oggetti o i membri del ruolo predefinito del server sysadmin.
  **Nota sulla sicurezza** i membri del ruolo di sysadmin ruolo predefinito del server e i proprietari degli oggetti non è possibile negare le autorizzazioni. "
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for DENY  
DENY   { ALL [ PRIVILEGES ] } 
     | <permission>  [ ( column [ ,...n ] ) ] [ ,...n ]  
    [ ON [ <class> :: ] securable ] 
    TO principal [ ,...n ]   
    [ CASCADE] [ AS principal ]  
[;]

<permission> ::=  
{ see the tables below }  
  
<class> ::=  
{ see the tables below }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DENY   
    <permission> [ ,...n ]  
    [ ON [ <class_> :: ] securable ]   
    TO principal [ ,...n ]  
    [ CASCADE ]  
[;]  
  
<permission> ::=  
{ see the tables below }  
  
<class> ::=  
{  
      LOGIN  
    | DATABASE  
    | OBJECT  
    | ROLE  
    | SCHEMA  
    | USER  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 ALL  
 Questa opzione non nega tutte le autorizzazioni possibili. Negare ALL equivale a negare le autorizzazioni seguenti.  
  
-   Se l'entità a protezione diretta è un database, ALL corrisponde a BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE e CREATE VIEW.  
  
-   Se l'entità a protezione diretta è una funzione scalare, ALL corrisponde a EXECUTE e REFERENCES.  
  
-   Se l'entità a protezione diretta è una funzione con valori di tabella, ALL corrisponde a DELETE, INSERT, REFERENCES, SELECT e UPDATE.  
  
-   Se l'entità a protezione diretta è una stored procedure, ALL corrisponde a EXECUTE.  
  
-   Se l'entità a protezione diretta è una tabella, ALL corrisponde a DELETE, INSERT, REFERENCES, SELECT e UPDATE.  
  
-   Se l'entità a protezione diretta è una vista, ALL corrisponde a DELETE, INSERT, REFERENCES, SELECT e UPDATE.  
  
> [!NOTE]  
>  La sintassi DENY ALL è deprecata. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Negare invece autorizzazioni specifiche.  
  
 PRIVILEGES  
 Opzione inclusa per compatibilità con lo standard ISO. Non modifica il funzionamento di ALL.  
  
 *autorizzazione*  
 Nome di un'autorizzazione. I mapping validi tra le autorizzazioni e le entità a protezione diretta sono descritti negli argomenti correlati elencati di seguito.  
  
 *colonna*  
 Specifica il nome di una colonna in una tabella per la quale vengono negate le autorizzazioni. È necessario utilizzare le parentesi ().  
  
 *classe*  
 Specifica la classe dell'entità a protezione diretta per la quale viene negata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 *entità a protezione diretta*  
 Specifica l'entità a protezione diretta per cui viene negata l'autorizzazione.  
  
 PER *principale*  
 Nome di un'entità. Le entità alle quali possono essere negate le autorizzazioni per un'entità a protezione diretta variano in base all'entità a protezione diretta. Per le combinazioni valide, vedere gli argomenti relativi alle entità a protezione diretta elencati di seguito.  
  
 CASCADE  
 Indica che l'autorizzazione viene negata all'entità specificata e a tutte le entità alle quali l'entità ha concesso l'autorizzazione. Obbligatorio quando l'entità dispone dell'autorizzazione con GRANT OPTION.  
  
 AS *principale*  
  Utilizzare la clausola principale per indicare che l'entità è registrata come denari dell'autorizzazione devono essere un'identità diverso da quello che esegue l'istruzione. Ad esempio, presuppongono che l'utente Mary sia principal_id 12 utente Raul è 15 principale. Mary esegue `DENY SELECT ON OBJECT::X TO Steven WITH GRANT OPTION AS Raul;` ora la tabella sys. database_permissions indicherà che grantor_prinicpal_id dell'istruzione deny è 15 (Raul), anche se l'istruzione è stata effettivamente eseguita dall'utente 13 (Mary).
  
L'utilizzo di come questa istruzione non implica la possibilità di rappresentare un altro utente.  
  
## <a name="remarks"></a>Osservazioni  
 La sintassi completa dell'istruzione DENY è complessa. Il diagramma della sintassi precedente è stato semplificato per evidenziarne la struttura. La sintassi completa per negare le autorizzazioni su entità a protezione diretta specifiche è descritta negli argomenti elencati di seguito.  
  
 DENY ha esito negativo se l'argomento CASCADE viene omesso quando si nega un'autorizzazione a un'entità a cui è stata concessa tale autorizzazione con l'opzione GRANT OPTION specificata.  
  
 La stored procedure di sistema sp_helprotect visualizza le autorizzazioni per un'entità a protezione diretta a livello di database.  
  
> [!CAUTION]  
>  Un'istruzione DENY a livello di tabella non ha la precedenza rispetto a un'istruzione GRANT a livello di colonna. Questa incongruenza nella gerarchia di autorizzazioni è stata mantenuta per garantire la compatibilità con le versioni precedenti Verrà rimosso in una versione futura.  
  
> [!CAUTION]  
>  Negando l'autorizzazione CONTROL per un database viene negata implicitamente anche l'autorizzazione CONNECT per il database. Un'entità a cui viene negata l'autorizzazione CONTROL per un database non può connettersi a tale database.  
  
> [!CAUTION]  
>  Se si nega l'autorizzazione CONTROL SERVER, viene implicitamente negata anche l'autorizzazione CONNECT SQL per il server. Un'entità a cui viene negata l'autorizzazione CONTROL SERVER per un server non può connettersi a tale server.  
  
## <a name="permissions"></a>Permissions  
 Il chiamante (o l'entità specificata con l'opzione AS) deve disporre dell'autorizzazione CONTROL per un'entità a protezione diretta o di un'autorizzazione di livello superiore che implichi l'autorizzazione CONTROL per tale entità a protezione diretta. Se si utilizza l'opzione AS, l'entità specificata deve essere proprietaria dell'entità a protezione diretta per la quale viene negata un'autorizzazione.  
  
 Gli utenti che dispongono dell'autorizzazione CONTROL SERVER, ad esempio i membri del ruolo predefinito del server sysadmin, possono negare qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel server. Gli utenti che dispongono dell'autorizzazione CONTROL per il database, ad esempio i membri del ruolo predefinito del database db_owner, possono negare qualsiasi autorizzazione per ogni entità a protezione diretta nel database. Gli utenti che dispongono dell'autorizzazione CONTROL per uno schema possono negare qualsiasi autorizzazione per qualsiasi oggetto nello schema. Se si utilizza la clausola AS, l'entità specificata deve essere proprietaria dell'entità a protezione diretta per cui vengono negate le autorizzazioni.  
  
## <a name="examples"></a>Esempi  
 Nella tabella seguente vengono elencate le entità a protezione diretta e gli argomenti in cui viene descritta la relativa sintassi specifica.  
  
|||  
|-|-|  
|Ruolo applicazione|[NEGARE autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|Assembly|[DENY-autorizzazioni per Assembly &#40; Transact-SQL &#41;](../../t-sql/statements/deny-assembly-permissions-transact-sql.md)|  
|Chiave asimmetrica|[NEGARE autorizzazioni per chiavi asimmetriche &#40; Transact-SQL &#41;](../../t-sql/statements/deny-asymmetric-key-permissions-transact-sql.md)|  
|Gruppo di disponibilità|[Nega le autorizzazioni del gruppo di disponibilità &#40; Transact-SQL &#41;](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)|  
|Certificato|[Nega le autorizzazioni del certificato &#40; Transact-SQL &#41;](../../t-sql/statements/deny-certificate-permissions-transact-sql.md)|  
|Contratto|[NEGARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Database|[Nega le autorizzazioni di Database &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-permissions-transact-sql.md)|  
|Credenziali con ambito database|[DENY (Transact-SQL) credenziali con ambito Database](../../t-sql/statements/deny-database-scoped-credential-transact-sql.md)|  
|Endpoint|[NEGARE autorizzazioni per Endpoint &#40; Transact-SQL &#41;](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)|  
|Catalogo full-text|[NEGAZIONE di autorizzazioni Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/deny-full-text-permissions-transact-sql.md)|  
|Elenco di parole non significative full-text|[NEGAZIONE di autorizzazioni Full-Text &#40; Transact-SQL &#41;](../../t-sql/statements/deny-full-text-permissions-transact-sql.md)|  
|Funzione|[NEGARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Account di accesso|[NEGARE autorizzazioni per entità Server &#40; Transact-SQL &#41;](../../t-sql/statements/deny-server-principal-permissions-transact-sql.md)|  
|Tipo di messaggio|[NEGARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Oggetto|[NEGARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Coda|[NEGARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Associazione al servizio remoto|[NEGARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Ruolo|[NEGARE autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|Route|[NEGARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|schema|[DENY Schema autorizzazioni &#40; Transact-SQL &#41;](../../t-sql/statements/deny-schema-permissions-transact-sql.md)|  
|Elenco delle proprietà di ricerca|[NEGARE autorizzazioni Search Property List &#40; Transact-SQL &#41;](../../t-sql/statements/deny-search-property-list-permissions-transact-sql.md)|  
|Server|[NEGARE autorizzazioni per Server &#40; Transact-SQL &#41;](../../t-sql/statements/deny-server-permissions-transact-sql.md)|  
|Servizio|[NEGARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|Stored procedure|[NEGARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Chiave simmetrica|[NEGARE autorizzazioni per chiavi simmetriche &#40; Transact-SQL &#41;](../../t-sql/statements/deny-symmetric-key-permissions-transact-sql.md)|  
|Sinonimo|[NEGARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Oggetti di sistema|[NEGARE autorizzazioni per gli oggetti di sistema &#40; Transact-SQL &#41;](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)|  
|Tabella|[NEGARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Tipo|[Nega le autorizzazioni di tipo &#40; Transact-SQL &#41;](../../t-sql/statements/deny-type-permissions-transact-sql.md)|  
|Utente|[NEGARE autorizzazioni per entità di Database &#40; Transact-SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|Visualizza|[NEGARE autorizzazioni per oggetti &#40; Transact-SQL &#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Raccolta di XML Schema|[NEGARE autorizzazioni per raccolte XML Schema &#40; Transact-SQL &#41;](../../t-sql/statements/deny-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotect &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  
