---
title: 'La creazione di istanze di evento ADO: Visual Basic | Documenti Microsoft'
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
ms.assetid: dce0a2a3-326f-4aaf-a822-6c5549833afa
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91452f6f087cde82878a5478707f538fff284db5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ado-event-instantiation-visual-basic"></a>La creazione di istanze di evento ADO: Visual Basic
Per gestire gli eventi di ADO in Microsoft® Visual Basic®, è necessario dichiarare una variabile di a livello di modulo utilizzando la **WithEvents** (parola chiave). La variabile può essere dichiarata solo come parte di un modulo di classe e deve essere dichiarata a livello di modulo. Infatti, non come restrittivo come potrebbe sembrare Visual Basic **modulo** gli oggetti sono anche le classi. Il modo più semplice per gestire gli eventi ADO consiste nel dichiarare una variabile utilizzando **WithEvents**. L'esempio seguente viene gestito il **ConnectComplete** evento per un **connessione** oggetto:  
  
```  
' BeginEventExampleVB02  
Dim WithEvents connEvent As Connection  
Attribute connEvent.VB_VarHelpID = -1  
  
Private Sub Form_Load()  
Dim strConn As String  
  
   ' Create a new object with event  
   ' handling enabled.  
   strConn = "Provider=sqloledb;" & _  
      "Data Source=MyServer;" & _  
      "Initial Catalog=Northwind;" & _  
      "Integrated Security=SSPI;"  
   Set connEvent = New ADODB.Connection  
   connEvent.Open strConn  
End Sub  
  
Private Sub connEvent_ConnectComplete(ByVal pError As ADODB.Error, _  
    adStatus As ADODB.EventStatusEnum, _  
    ByVal pConnection As ADODB.Connection)  
Dim strMsg As String  
  
   If adStatus = adStatusErrorsOccurred Then  
      Select Case pError.Number  
         Case adErrOperationCancelled  
            ' The operation was cancelled in the  
            ' Will event. Notify the user and exit.  
            strMsg = "I'm sorry you can't connect right now." & vbCrLf  
            strMsg = strMsg & "Click OK to exit."  
            Unload Me  
         Case Else  
            strMsg = "Error " & Format(pError.Number) & vbCrLf  
            strMsg = strMsg & pError.Description  
            strMsg = strMsg & "Click OK to exit."  
            Unload Me  
      End Select  
   End If  
   frmWait.btnOK.Enabled = True  
End Sub  
' EndEventExampleVB02  
```  
  
 Il **connessione** oggetto è dichiarato nel **modulo** livello utilizzando il **WithEvents** parola chiave per consentire la gestione degli eventi. Il gestore dell'evento Form_Load crea l'oggetto tramite l'assegnazione di un nuovo **connessione** oggetto *connEvent* e quindi apre la connessione. Naturalmente, un'applicazione reale farebbe ulteriore elaborazione nel gestore eventi Form_Load rispetto a quella illustrata di seguito.
