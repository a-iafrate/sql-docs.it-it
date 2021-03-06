---
title: sp_set_database_firewall_rule (Database SQL di Azure) | Documenti Microsoft
ms.custom: ''
ms.date: 08/04/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_set_database_firewall_rule
- sp_set_database_firewall_rule_TSQL
- sys.sp_set_database_firewall_rule
- sys.sp_set_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_database_firewall_rule
- firewall_rules, setting database rules
ms.assetid: 8f0506b6-a4ac-4e4d-91db-8077c40cb17a
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 6fa2b1effae12bd8132c331d4e1ba33055c656e0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="spsetdatabasefirewallrule-azure-sql-database"></a>sp_set_database_firewall_rule (Database di SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Crea o aggiorna le regole del firewall a livello di database per il [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Le regole firewall del database possono essere configurate per il **master** database e per i database utente [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Le regole firewall del database sono particolarmente utili quando si usano gli utenti di database indipendente. Per altre informazioni, vedere [Utenti di database indipendente: rendere portabile un database](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_set_database_firewall_rule [@name = ] [N]'name'  
, [@start_ip_address =] 'start_ip_address'  
, [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 **[@name**  =] [N]'*nome*'  
 Il nome utilizzato per descrivere e distinguere l'impostazione del firewall a livello di database. *nome* viene **nvarchar (128)** non prevede alcun valore predefinito. L'identificatore Unicode `N` è facoltativo per [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]. 
  
 **[@start_ip_address**  =] '*start_ip_address*'  
 L'indirizzo IP più basso nell'intervallo dell'impostazione del firewall a livello di database. Gli indirizzi IP uguali o maggiori di questo possono tentare la connessione all'istanza del [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L'indirizzo IP più basso possibile è `0.0.0.0`. *start_ip_address* viene **varchar (50)** non prevede alcun valore predefinito.  
  
 [**@end_ip_address** =] '*end_ip_address*'  
 L'indirizzo IP più alto nell'intervallo dell'impostazione del firewall a livello di database. Gli indirizzi IP uguali o minori di questo possono tentare la connessione all'istanza del [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L'indirizzo IP più alto possibile è `255.255.255.255`. *end_ip_address* viene **varchar (50)** non prevede alcun valore predefinito.  
  
 Nella tabella seguente vengono illustrati gli argomenti supportati e le opzioni [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
> [!NOTE]  
>  Tentativi di connessione di Azure sono consentiti quando sia questo campo e *start_ip_address* campo uguale a `0.0.0.0`.  
  
## <a name="remarks"></a>Osservazioni  
 I nomi delle impostazioni del firewall a livello di database per un database devono essere univoci. Se il nome dell'impostazione del firewall a livello di database fornito per la stored procedure esiste già nella tabella delle impostazioni del firewall a livello di database, gli indirizzi IP iniziale e finale verranno aggiornati. In caso contrario, verrà creata un'impostazione del firewall a livello di database.  
  
 Quando si aggiunge un'impostazione del firewall a livello di database in cui iniziale e finale di indirizzi IP sono uguali a `0.0.0.0`, si abilita l'accesso al database nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server da qualsiasi risorsa di Azure. Specificare un valore per il *nome* parametro che consenta di ricordare che cos'è l'impostazione del firewall per.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione **CONTROL** per il database.  
  
## <a name="examples"></a>Esempi  
 Il codice seguente crea un database a livello di impostazione del firewall denominata `Allow Azure` che consente l'accesso al database da Azure.  
  
```  
-- Enable Azure connections.  
EXECUTE sp_set_database_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 Il codice seguente consente di creare un'impostazione del firewall a livello di database denominata `Example DB Setting 1` solo per l'indirizzo IP `0.0.0.4`. Quindi, `sp_set_database firewall_rule` stored procedure viene chiamata nuovamente per aggiornare l'indirizzo IP finale per `0.0.0.6`, nell'impostazione del firewall. Questo consente di creare un intervallo che consente di indirizzi IP `0.0.0.4`, `0.0.0.5`, e `0.0.0.6` per accedere al database.
  
```  
-- Create database-level firewall setting for only IP 0.0.0.4  
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.4';  
  
-- Update database-level firewall setting to create a range of allowed IP addresses
EXECUTE sp_set_database_firewall_rule N'Example DB Setting 1', '0.0.0.4', '0.0.0.6';  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Firewall del Database SQL di Azure](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Procedura: configurare le impostazioni del Firewall (Database SQL di Azure)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Database SQL di Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;Database SQL di Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [Sys. database_firewall_rules &#40;Database SQL di Azure&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  
