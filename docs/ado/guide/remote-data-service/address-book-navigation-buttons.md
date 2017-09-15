---
title: Pulsanti di spostamento della Rubrica indirizzi | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS scenarios [ADO], navigation buttons
- address book application scenario [ADO], navigation buttons
ms.assetid: f0dd84c6-5c33-4ab9-82b4-4c42dfdd2277
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f8e7c2a6b16b8190a86f2c656fcb0a76b2e6984a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="address-book-navigation-buttons"></a>Pulsanti di spostamento della Rubrica di indirizzi
L'applicazione Address Book Visualizza i pulsanti di navigazione nella parte inferiore della pagina Web. È possibile utilizzare i pulsanti di navigazione per spostarsi tra i dati nella visualizzazione della griglia HTML selezionando la prima o nell'ultima riga di dati o righe adiacenti alla selezione corrente.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="navigation-sub-procedures"></a>Navigazione Sub (routine)  
 L'applicazione Address Book contiene varie procedure che consentono agli utenti di selezionare il **prima**, **Avanti**, **precedente**, e **ultimo** pulsanti per spostarsi tra i dati.  
  
 Ad esempio, facendo clic su di **prima** pulsante per attivare la routine Sub VBScript First_OnClick. La procedura esegue un [MoveFirst](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) metodo, che rende la prima riga di dati la selezione corrente. Fare clic sul **ultimo** pulsante Attiva la routine Sub Last_OnClick, che richiama la [MoveLast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) (metodo), rendendo l'ultima riga di dati la selezione corrente. Gli altri pulsanti di spostamento funzionano in modo simile.  
  
```  
' Move to the first record in the bound Recordset.  
Sub First_OnClick  
   DC1.Recordset.MoveFirst  
End Sub  
  
' Move to the next record from the current position   
' in the bound Recordset.  
Sub Next_OnClick  
   If Not DC1.Recordset.EOF Then    ' Cannot move beyond bottom record.  
      DC1.Recordset.MoveNext  
      Exit Sub  
   End If     
End Sub  
  
' Move to the previous record from the current position in the bound   
' Recordset.  
Sub Prev_OnClick  
   If Not DC1.Recordset.BOF Then    ' Cannot move beyond top record.  
      DC1.Recordset.MovePrevious  
      Exit Sub  
   End If  
End Sub  
  
' Move to the last record in the bound Recordset.  
Sub Last_OnClick  
   DC1.Recordset.MoveLast  
End Sub  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [MoveFirst, MoveLast, MoveNext e MovePrevious metodi (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)



