---
title: AddNew (metodo) (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AddNew
- Recordset15::raw_AddNew
helpviewer_keywords:
- AddNew method [ADO]
ms.assetid: a9f54be9-5763-45d0-a6eb-09981b03bc08
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 315eec5a4cddccb55be1ad9b8bd9d8bc4ded99cf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="addnew-method-ado"></a>AddNew (metodo) (ADO)
Crea un nuovo record per un aggiornabile [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.AddNew FieldList, Values  
```  
  
#### <a name="parameters"></a>Parametri  
 *recordset*  
 Oggetto **Recordset** oggetto.  
  
 *FieldList*  
 Facoltativa. Un singolo nome o una matrice di nomi o posizioni ordinali dei campi nel nuovo record.  
  
 *Valori*  
 Facoltativa. Un singolo valore o una matrice di valori per i campi nel nuovo record. Se *elenco campi* è una matrice, *valori* deve essere una matrice con lo stesso numero di membri in caso contrario, si verifica un errore. L'ordine dei nomi di campo deve corrispondere all'ordine dei valori di campo in ogni matrice.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **AddNew** per creare e inizializzare un nuovo record. Utilizzare il [supporta](../../../ado/reference/ado-api/supports-method.md) metodo con **adAddNew** (un [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) valore) per verificare se è possibile aggiungere record corrente **Recordset**oggetto.  
  
 Dopo aver chiamato il **AddNew** (metodo), il nuovo record diventa il record corrente e rimane tale dopo la chiamata di [aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo. Poiché viene aggiunto il nuovo record per il **Recordset**, una chiamata a **MoveNext** dopo l'aggiornamento passerà oltre la fine del **Recordset**, rendendo **EOF**  True. Se il **Recordset** oggetto non supporta i segnalibri, potrebbe non essere in grado di accedere al nuovo record dopo il passaggio a un altro record. A seconda del tipo di cursore, è necessario chiamare il [Requery](../../../ado/reference/ado-api/requery-method.md) metodo per rendere accessibile il nuovo record.  
  
 Se si chiama **AddNew** durante la modifica del record corrente o durante l'aggiunta di un nuovo record, ADO chiama il **aggiornamento** per salvare le modifiche e quindi crea il nuovo record.  
  
 Il comportamento del **AddNew** metodo dipende dalla modalità di aggiornamento del **Recordset** oggetto e se si passa il *elenco campi* e *valori*argomenti.  
  
 In *modalità di aggiornamento immediato* (in cui il provider scrive le modifiche all'origine dati sottostante non appena viene chiamato il **aggiornare** metodo), la chiamata di **AddNew** metodo senza set di argomenti di [EditMode](../../../ado/reference/ado-api/editmode-property.md) proprietà **adEditAdd** (un [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) valore). Il provider memorizza nella cache qualsiasi valore di campo modificato in locale. La chiamata di **aggiornamento** metodo invia il nuovo record nel database e reimposta il **EditMode** proprietà **adEditNone** (un **EditModeEnum**valore). Se si passa il *elenco campi* e *valori* argomenti, ADO invia immediatamente il nuovo record per il database (non **aggiornamento** è necessario chiamare); il **EditMode**  valore proprietà non viene modificato (**adEditNone**).  
  
 In *modalità di aggiornamento batch* (in cui il provider memorizza nella cache più modifiche e li scrive all'origine dati sottostante solo quando si chiama il [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodo), la chiamata di **AddNew** metodo senza argomenti imposta la **EditMode** proprietà **adEditAdd**. Il provider memorizza nella cache qualsiasi valore di campo modificato in locale. La chiamata di **aggiornamento** metodo aggiunge il nuovo record corrente **Recordset**, ma il provider non registra le modifiche al database sottostante, o la reimpostazione di **EditMode** per **adEditNone**, finché non si chiama il **UpdateBatch** metodo. Se si passa il *elenco campi* e *valori* argomenti, ADO invia il nuovo record per il provider di archiviazione in una cache e imposta il **EditMode** a **adEditAdd** ; è necessario chiamare il **UpdateBatch** metodo per registrare il nuovo record nel database sottostante.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo AddNew con l'elenco di campo e un elenco di valori incluso, per informazioni su come includere l'elenco dei campi e un elenco di valori come matrici.  
  
```  
create table aa1 (intf int, charf char(10))  
insert into aa1 values (2, 'aa')  
  
Dim cn As New adodb.Connection  
Dim rs As New adodb.Recordset  
Dim cmd As New adodb.Command  
  
cn.ConnectionString = "Provider=SQLOLEDB;Data Source=alexverb2;uid=sa;pwd=foo$bar00;"  
  
cn.Open  
rs.Open "select * from xxx..aa1", cn, adOpenKeyset, adLockOptimistic  
  
Dim fieldsArray(1) As Variant  
fieldsArray(0) = "intf"  
fieldsArray(1) = "charf"  
Dim values(1) As Variant  
values(0) = 4  
values(1) = "as"  
rs.AddNew fieldsArray, values  
rs.Update  
```  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio del metodo AddNew (VB)](../../../ado/reference/ado-api/addnew-method-example-vb.md)   
 [Esempio del metodo AddNew (VBScript)](../../../ado/reference/ado-api/addnew-method-example-vbscript.md)   
 [Esempio del metodo AddNew (VC + +)](../../../ado/reference/ado-api/addnew-method-example-vc.md)   
 [Metodo CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Proprietà EditMode](../../../ado/reference/ado-api/editmode-property.md)   
 [Requery (metodo)](../../../ado/reference/ado-api/requery-method.md)   
 [Supporta (metodo)](../../../ado/reference/ado-api/supports-method.md)   
 [Update (metodo)](../../../ado/reference/ado-api/update-method.md)   
 [Metodo UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
