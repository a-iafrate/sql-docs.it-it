---
title: Esempio di proprietà DefinedSize (VC + +) e ActualSize | Documenti Microsoft
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
dev_langs:
- C++
helpviewer_keywords:
- ActualSize property [ADO], VC++ example
- DefinedSize property [ADO], VC++ example
ms.assetid: 05f7cc97-b806-41d2-939d-a955d10844c4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe74dafe719743f9726d8e5980091865b500c48f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="actualsize-and-definedsize-properties-example-vc"></a>Esempio ActualSize e DefinedSize proprietà (VC + +)
Questo esempio viene utilizzato il [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) e [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) proprietà per visualizzare le dimensioni definite e le dimensioni effettive di un campo.  
  
## <a name="example"></a>Esempio  
  
```  
// BeginActualSizeCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include "conio.h"   
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void ActualSizeX();  
void PrintProviderError(_ConnectionPtr pConnection);  
  
int main() {  
   if (FAILED(::CoInitialize(NULL)))  
      return -1;  
   ActualSizeX();  
   ::CoUninitialize();  
}  
  
void ActualSizeX() {  
   HRESULT hr = S_OK;  
  
   // Define ADO object pointers. Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _RecordsetPtr pRstStores = NULL;  
  
   // Define Other variables  
   _bstr_t strMessage;  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      // Open a recordset for the stores table.  
      TESTHR(pRstStores.CreateInstance(__uuidof(Recordset)));  
  
      // You have to explicitly pass the Cursor type and LockType to the Recordset here.  
      hr = pRstStores->Open("stores", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable);  
  
      // Loop through the recordset displaying the contents of the stor_name field,   
      // the field's defined size, and its actual size.  
      pRstStores->MoveFirst();  
  
      while (!(pRstStores->EndOfFile)) {  
         strMessage = "Store Name: ";  
         strMessage += (_bstr_t)pRstStores->Fields->Item["stor_name"]->Value + "\n";  
         strMessage += "Defined Size: ";   
         strMessage += (_bstr_t)pRstStores->Fields->Item["stor_name"]->DefinedSize + "\n";  
         strMessage += "Actual Size: ";  
         strMessage += (_bstr_t) pRstStores->Fields->Item["stor_name"]->ActualSize + "\n";   
  
         printf("%s\n",(LPCSTR)strMessage);  
         pRstStores->MoveNext();  
      }  
   }  
   catch(_com_error &e) {  
      _variant_t vtConnect = pRstStores->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
         case VT_BSTR:  
            printf("Error:\n");  
            printf("Code = %08lx\n", e.Error());  
            printf("Message = %s\n", e.ErrorMessage());  
            printf("Source = %s\n", (LPCSTR) e.Source());  
            printf("Description = %s\n", (LPCSTR) e.Description());  
            break;  
         case VT_DISPATCH:  
            PrintProviderError(vtConnect);  
            break;  
         default:  
            printf("Errors occured.");  
            break;  
      }  
   }  
  
   // Clean up objects before exit.  
   if (pRstStores)  
      if (pRstStores->State == adStateOpen)  
         pRstStores->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
   long nCount = 0;      
   long i = 0;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for (i = 0 ; i < nCount ; i++) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("\t Error number: %x\t%s", pErr->Number,(LPCSTR ) pErr->Description);  
      }  
   }  
}  
```  
  
 **Nome dell'archivio: Eric i libri di lettura**  
**Definite dimensioni: 40**  
**Dimensioni effettive: 19**  
**Nome dell'archivio: Barnum**  
**Definite dimensioni: 40**  
**Dimensioni effettive: 8**  
**Nome dell'archivio: Notizie & Brews**  
**Definite dimensioni: 40**  
**Dimensioni effettive: 12**  
**Nome dell'archivio: Doc-U-Mat: bucato qualità e documentazione**  
**Definite dimensioni: 40**  
**Dimensioni effettive: 36**  
**Nome dell'archivio: Fricative Bookshop**  
**Definite dimensioni: 40**  
**Dimensioni effettive: 18**  
**Nome dell'archivio: Bookbeat**  
**Definite dimensioni: 40**  
**Dimensioni effettive: 8**   
## <a name="see-also"></a>Vedere anche  
 [Proprietà ActualSize (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)   
 [Proprietà DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)
