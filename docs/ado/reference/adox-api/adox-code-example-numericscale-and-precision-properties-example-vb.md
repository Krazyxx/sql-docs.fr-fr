---
title: NumericScale et Precision, propriétés, exemple (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Precision property [ADOX], Visual Basic example
- NumericScale property [ADOX], Visual Basic example
ms.assetid: ea2ec614-34c8-41b7-8ebd-063798bd56b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d4fece6307ff005031e7ab770b14bd5fbca541d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63308799"
---
# <a name="adox-code-example-numericscale-and-precision-properties-example-vb"></a>Exemple de code ADOX : NumericScale et Precision, exemple de propriétés (VB)
Cet exemple montre la [NumericScale](../../../ado/reference/adox-api/numericscale-property-adox.md) et [précision](../../../ado/reference/adox-api/precision-property-adox.md) propriétés de la [colonne](../../../ado/reference/adox-api/column-object-adox.md) objet. Ce code affiche leur valeur pour le **Order Details** table de la *Northwind* base de données.  
  
```  
' BeginNumericScalePrecVB  
Sub Main()  
    On Error GoTo NumericScalePrecXError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tblOD As ADOX.Table  
    Dim colLoop As ADOX.Column  
  
    ' Connect the catalog.  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "data source='Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
  
    ' Retrieve the Order Details table  
    Set tblOD = cat.Tables("Order Details")  
  
    ' Display numeric scale and precision of  
    ' small integer fields.  
    For Each colLoop In tblOD.Columns  
        If colLoop.Type = adSmallInt Then  
            MsgBox "Column: " & colLoop.Name & vbCr & _  
                "Numeric scale: " & _  
                colLoop.NumericScale & vbCr & _  
                "Precision: " & colLoop.Precision  
        End If  
    Next colLoop  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
NumericScalePrecXError:  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndNumericScalePrecVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de colonne (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [NumericScale, propriété (ADOX)](../../../ado/reference/adox-api/numericscale-property-adox.md)   
 [Precision, propriété (ADOX)](../../../ado/reference/adox-api/precision-property-adox.md)
