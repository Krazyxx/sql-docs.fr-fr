---
title: DateCreated et DateModified, exemples de propriétés (VB) | Microsoft Docs
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
- DateCreated property [ADOX], Visual Basic example
- DateModified property [ADOX], Visual Basic example
ms.assetid: d608ea35-6e68-402f-8184-a5041e408678
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59a54320cd3b1a90e832b474d5308086f018cc38
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281672"
---
# <a name="datecreated-and-datemodified-properties-example-vb"></a>DateCreated et DateModified, exemples de propriétés (VB)
Cet exemple montre la [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) et [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) propriétés en ajoutant une nouvelle [colonne](../../../ado/reference/adox-api/column-object-adox.md) à un existant [Table](../../../ado/reference/adox-api/table-object-adox.md) et par Création d’un nouveau **Table**. La procédure DateOutput est requise pour exécuter cet exemple.  
  
```  
' BeginDateCreatedVB  
Sub Main()  
    On Error GoTo DateCreatedXError  
  
    Dim cat As New ADOX.Catalog  
    Dim tblEmployees As ADOX.Table  
    Dim tblNewTable As ADOX.Table  
  
    ' Connect to the catalog.  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    With cat  
        Set tblEmployees = .Tables("Employees")  
  
        ' Print current information about the Employees table.  
        DateOutput "Current properties", tblEmployees  
  
        ' Create and append column to the Employees table.  
        tblEmployees.Columns.Append "NewColumn", adInteger  
        .Tables.Refresh  
  
        ' Print new information about the Employees table.  
        DateOutput "After creating a new column", tblEmployees  
  
        ' Delete new column because this is a demonstration.  
        tblEmployees.Columns.Delete "NewColumn"  
  
        ' Create and append new Table object to the Northwind database.  
        Set tblNewTable = New ADOX.Table  
        tblNewTable.Name = "NewTable"  
        tblNewTable.Columns.Append "NewColumn", adInteger  
        .Tables.Append tblNewTable  
        .Tables.Refresh  
  
        ' Print information about the new Table object.  
        DateOutput "After creating a new table", .Tables("NewTable")  
  
        ' Delete new Table object because this is a demonstration.  
        .Tables.Delete tblNewTable.Name  
    End With  
  
    'Clean up.  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
DateCreatedXError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
  
Sub DateOutput(strTemp As String, tblTemp As ADOX.Table)  
    ' Print DateCreated and DateModified information about  
    ' specified Table object.  
    Debug.Print strTemp  
    Debug.Print "    Table: " & tblTemp.Name  
    Debug.Print "        DateCreated = " & tblTemp.DateCreated  
    Debug.Print "        DateModified = " & tblTemp.DateModified  
    Debug.Print  
End Sub  
' EndDateCreatedVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DateCreated, propriété (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)   
 [DateModified, propriété (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)   
 [Objet de procédure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)   
 [Procedures, Collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Objet de vue (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)   
 [Views, collection (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
