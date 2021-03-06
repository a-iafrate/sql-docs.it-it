---
title: Raccolta di parametri, esempio di comando di proprietà (VB) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Command property [ADOX], Visual Basic example
ms.assetid: 7df1089e-69b7-476e-9244-19947c087351
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7bd2ffb544690129e761814b281252a76b89588f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="parameters-collection-command-property-example-vb"></a>Raccolta di parametri, esempio di proprietà di comando (Visual Basic)
Il codice seguente viene illustrato come utilizzare il [comando](../../../ado/reference/adox-api/command-property-adox.md) proprietà con il [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto per recuperare informazioni sui parametri per la procedura.  
  
```  
' BeginParametersVB  
Sub Main()  
    On Error GoTo ProcedureParametersError  
  
    Dim cnn As New ADODB.Connection  
    Dim cmd As ADODB.Command  
    Dim prm As ADODB.Parameter  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Connection  
    cnn.Open _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Open the catalog  
    Set cat.ActiveConnection = cnn  
  
    ' Get the command object  
    Set cmd = cat.Procedures("CustomerById").Command  
  
    ' Retrieve Parameter information  
    cmd.Parameters.Refresh  
    For Each prm In cmd.Parameters  
        Debug.Print prm.Name & ":" & prm.Type  
    Next  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set cmd = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
ProcedureParametersError:  
  
    Set cat = Nothing  
    Set cmd = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndParametersVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Oggetto del catalogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Proprietà dei comandi (ADOX)](../../../ado/reference/adox-api/command-property-adox.md)   
 [Oggetto procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)   
 [Raccolta di oggetti Procedure (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
