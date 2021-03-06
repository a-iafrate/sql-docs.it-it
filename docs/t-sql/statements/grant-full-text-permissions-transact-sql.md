---
title: GRANT - autorizzazioni per il catalogo full-text (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], full-text
- full-text search [SQL Server], permissions
- full-text catalogs [SQL Server], permissions
- full-text stoplist [SQL Server], permissions
- GRANT statement, full-text permissions
ms.assetid: fdb64e09-222a-47fe-b08b-999264ca261d
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 51c14ec41b0f636d8fee54f0721e337d5d169c9f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="grant-full-text-permissions-transact-sql"></a>GRANT - autorizzazioni per il catalogo full-text (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Concede le autorizzazioni per un catalogo full-text o un elenco di parole non significative full-text.  
  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
GRANT permission [ ,...n ] ON  
    FULLTEXT   
        {  
           CATALOG :: full-text_catalog_name  
           |  
           STOPLIST :: full-text_stoplist_name  
        }  
    TO database_principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS granting_principal ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *permission*  
 Nome di un'autorizzazione. I mapping validi tra le autorizzazioni e le entità a protezione diretta sono descritti nella sezione "Osservazioni" più avanti in questo argomento.  
  
 ON FULLTEXT CATALOG **::***full-text_catalog_name*  
 Specifica il catalogo full-text per cui viene concessa l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 ON FULLTEXT STOPLIST **::***full-text_stoplist_name*  
 Specifica l'elenco di parole non significative full-text per cui viene concessa l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 *database_principal*  
 Specifica l'entità a cui viene concessa l'autorizzazione. I tipi validi sono:  
  
-   utente del database  
-   ruolo del database  
-   ruolo dell'applicazione  
-   utente del database sul quale viene eseguito il mapping a un account di accesso di Windows  
-   utente del database sul quale viene eseguito il mapping a un gruppo di Windows  
-   utente del database sul quale viene eseguito il mapping a un certificato  
-   utente del database mappato a una chiave asimmetrica  
-   utente del database non mappato ad alcuna entità server.  
  
GRANT OPTION  
 Indica che l'entità potrà inoltre concedere l'autorizzazione specificata ad altre entità.  
  
AS *granting_principal*  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di concedere l'autorizzazione. I tipi validi sono:  
  
-   utente del database  
-   ruolo del database  
-   ruolo dell'applicazione  
-   utente del database sul quale viene eseguito il mapping a un account di accesso di Windows  
-   utente del database sul quale viene eseguito il mapping a un gruppo di Windows  
-   utente del database sul quale viene eseguito il mapping a un certificato  
-   utente del database mappato a una chiave asimmetrica  
-   utente del database non mappato ad alcuna entità server.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="fulltext-catalog-permissions"></a>Autorizzazioni FULLTEXT CATALOG  
 Un catalogo full-text è un'entità a protezione diretta a livello di database contenuta nel database padre nella gerarchia delle autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile concedere per un catalogo full-text, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione del catalogo full-text|Autorizzazione del catalogo full-text in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|-----------------------------------|----------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY FULLTEXT CATALOG|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="fulltext-stoplist-permissions"></a>Autorizzazioni FULLTEXT STOPLIST  
 Un elenco di parole non significative full-text è un'entità a protezione diretta a livello di database contenuta nel database padre nella gerarchia delle autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile concedere per un elenco di parole non significative full-text, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione dell'elenco di parole non significative full-text|Autorizzazione dell'elenco di parole non significative full-text in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|------------------------------------|-----------------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY FULLTEXT CATALOG|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Autorizzazioni  
 L'utente che concede le autorizzazioni (o l'entità specificata con l'opzione AS) deve disporre della relativa autorizzazione con GRANT OPTION oppure di un'autorizzazione di livello superiore che include l'autorizzazione che viene concessa.  
  
 Se si usano l'opzione AS, sono previsti questi requisiti aggiuntivi.  
  
|AS *granting_principal*|Autorizzazione aggiuntiva necessaria|  
|------------------------------|------------------------------------|  
|Utente del database|Autorizzazione IMPERSONATE per l'utente, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Utente del database di cui è stato eseguito il mapping a un account di accesso di Windows|Autorizzazione IMPERSONATE per l'utente, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Utente del database di cui è stato eseguito il mapping a un gruppo di Windows|Appartenenza al gruppo di Windows, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Utente del database di cui è stato eseguito il mapping a un certificato|Appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica|Appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Utente del database di cui non è stato eseguito il mapping ad alcuna entità server|Autorizzazione IMPERSONATE per l'utente, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Ruolo del database|Autorizzazione ALTER per il ruolo, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
|Ruolo applicazione|Autorizzazione ALTER per il ruolo, appartenenza al ruolo predefinito del database db_securityadmin, appartenenza al ruolo predefinito del database db_owner o appartenenza al ruolo predefinito del server sysadmin.|  
  
 I proprietari degli oggetti possono concedere autorizzazioni per gli oggetti di cui sono proprietari. Le entità con l'autorizzazione CONTROL per un'entità a sicurezza diretta possono concedere l'autorizzazione per quella entità.  
  
 Gli utenti che dispongono dell'autorizzazione CONTROL SERVER, ad esempio i membri del ruolo predefinito del server sysadmin, possono concedere qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel server. Gli utenti che dispongono dell'autorizzazione CONTROL in un database, ad esempio i membri del ruolo predefinito del database db_owner, possono concedere qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel database. Gli utenti che dispongono dell'autorizzazione CONTROL in uno schema, possono concedere qualsiasi autorizzazione per qualsiasi oggetto all'interno dello schema.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-granting-permissions-to-a-full-text-catalog"></a>A. Concessione di autorizzazioni per un catalogo full-text  
 Nell'esempio seguente a `Ted` viene concessa l'autorizzazione `CONTROL` per il catalogo full-text `ProductCatalog`.  
  
```  
GRANT CONTROL  
    ON FULLTEXT CATALOG :: ProductCatalog  
    TO Ted ;  
```  
  
### <a name="b-granting-permissions-to-a-stoplist"></a>B. Concessione di autorizzazioni per un elenco di parole non significative  
 Nell'esempio seguente, a `Mary` viene concessa l'autorizzazione `VIEW DEFINITION` per l'elenco di parole non significative full-text `ProductStoplist`.  
  
```  
GRANT VIEW DEFINITION  
    ON FULLTEXT STOPLIST :: ProductStoplist  
    TO Mary ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [sys.fn_my_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)  
  
  
