---
title: PrimaryKey et Unique de propriétés, exemple (VB) | Microsoft Docs
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
- Unique property [ADOX], Visual Basic example
- PrimaryKey property [ADOX], Visual Basic example
ms.assetid: f536acac-06ea-4b39-bfba-ee9902b01615
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10f5a1a5c1436181a75329bfb0371c8836d7ac6e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62709871"
---
# <a name="primarykey-and-unique-properties-example-vb"></a>PrimaryKey et Unique, exemples de propriétés (VB)
Cet exemple montre la [PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md) et [Unique](../../../ado/reference/adox-api/unique-property-adox.md) propriétés d’un [Index](../../../ado/reference/adox-api/index-object-adox.md). Le code crée une nouvelle table avec deux colonnes. Le **PrimaryKey** et **Unique** propriétés sont utilisées pour définir une colonne clé primaire pour laquelle les valeurs en double ne sont pas autorisées.  
  
```  
' BeginPrimaryKeyVB  
Sub Main()  
    On Error GoTo PrimaryKeyXError  
  
    Dim catNorthwind As New ADOX.Catalog  
    Dim tblNew As New ADOX.Table  
    Dim idxNew As New ADOX.Index  
    Dim idxLoop As New ADOX.Index  
    Dim colLoop As New ADOX.Column  
  
    ' Connect the catalog  
    catNorthwind.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Name new table  
    tblNew.Name = "NewTable"  
  
    ' Append a numeric and a text field to new table.  
    tblNew.Columns.Append "NumField", adInteger, 20  
    tblNew.Columns.Append "TextField", adVarWChar, 20  
  
    ' Append new Primary Key index on NumField column  
    ' to new table  
    idxNew.Name = "NumIndex"  
    idxNew.Columns.Append "NumField"  
    idxNew.PrimaryKey = True  
    idxNew.Unique = True  
    tblNew.Indexes.Append idxNew  
  
    ' Append an index on Textfield to new table.  
    ' Note the different technique: Specifying index and  
    ' column name as parameters of the Append method  
    tblNew.Indexes.Append "TextIndex", "TextField"  
  
    ' Append the new table  
    catNorthwind.Tables.Append tblNew  
  
    With tblNew  
        Debug.Print tblNew.Indexes.Count & " Indexes in " & _  
            tblNew.Name & " Table"  
  
        ' Enumerate Indexes collection.  
        For Each idxLoop In .Indexes  
            With idxLoop  
                Debug.Print "Index " & .Name  
                Debug.Print "   Primary key = " & .PrimaryKey  
                Debug.Print "   Unique = " & .Unique  
  
                ' Enumerate Columns collection of each Index  
                ' object.  
                Debug.Print "    Columns"  
                For Each colLoop In .Columns  
                    Debug.Print "       " & colLoop.Name  
                Next colLoop  
            End With  
        Next idxLoop  
  
    End With  
  
    ' Delete new table as this is a demonstration.  
    catNorthwind.Tables.Delete tblNew.Name  
  
    'Clean up  
    Set catNorthwind.ActiveConnection = Nothing  
    Set catNorthwind = Nothing  
    Set tblNew = Nothing  
    Set idxNew = Nothing  
    Set idxLoop = Nothing  
    Set colLoop = Nothing  
    Exit Sub  
  
PrimaryKeyXError:  
  
    Set catNorthwind = Nothing  
    Set tblNew = Nothing  
    Set idxNew = Nothing  
    Set idxLoop = Nothing  
    Set colLoop = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndPrimaryKeyVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Index, objet (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [PrimaryKey, propriété (ADOX)](../../../ado/reference/adox-api/primarykey-property-adox.md)   
 [Unique, propriété (ADOX)](../../../ado/reference/adox-api/unique-property-adox.md)
