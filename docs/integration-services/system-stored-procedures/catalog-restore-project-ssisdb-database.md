---
title: catalog.restore_project (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 8adee525-579b-4d2f-b807-e2ecc07fb2e9
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ce136d3f87c2f654bd562c0dd58dfb262cc47c85
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="catalogrestoreproject-ssisdb-database"></a>catalog.restore_project (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Viene ripristinata la versione precedente di un progetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.restore_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project _name  
    , [ @object_version_lsn = ] object_version_lsn  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name = ] *folder_name*  
 Nome della cartella in cui è contenuto il progetto. *folder_name* è di tipo **nvarchar(128)**.  
  
 [ @project _name = ] *project_name*  
 Nome del progetto. *project_name* è di tipo **nvarchar(128)**.  
  
 [ @object_version_lsn = ] *object_version_lsn*  
 Versione del progetto. *object_version_lsn* è di tipo **bigint**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 I dettagli del progetto vengono restituiti come **varbinary(MAX)** come parte del set di risultati se viene trovato *project_name*.  
  
 **NO RESULT SET** viene restituito se non è possibile ripristinare il progetto nella cartella specificata.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sul progetto  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Versione del progetto inesistente o non corrispondente al nome del progetto  
  
-   Progetto inesistente  
  
-   Utente senza autorizzazioni appropriate.  
  
## <a name="remarks"></a>Remarks  
 Quando viene ripristinato un progetto, a tutti i parametri vengono assegnati i valori predefiniti mentre tutti i riferimenti all'ambiente rimangono invariati. Il numero massimo di versioni del progetto mantenute nel catalogo è determinato dalla proprietà del catalogo **MAX_VERSIONS_PER_PROJECT**, come mostrato nella vista [catalog_property](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md).  
  
> [!WARNING]  
>  I riferimenti all'ambiente potrebbero non essere più validi dopo il ripristino di un progetto.  
  
  
