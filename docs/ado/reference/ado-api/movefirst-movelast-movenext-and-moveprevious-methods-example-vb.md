---
title: Déplacer le pointeur d’enregistrement du jeu d’enregistrements, exemple (VB) | Microsoft Docs
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
- MovePrevious method [ADO], Visual Basic example
- MoveLast method [ADO], Visual Basic example
- MoveFirst method [ADO], Visual Basic example
- MoveNext method [ADO], Visual Basic example
ms.assetid: 31d3b083-c677-423e-8d26-a212eaeea281
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 573c433dbcf6ee7bb32f7a83639836f30bd43025
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242457"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-example-vb"></a>MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes-exemple (VB)
Cet exemple utilise le [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), et [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) méthodes pour déplacer le pointeur d’enregistrement d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) selon la commande fournie. La procédure MoveAny est nécessaire pour exécuter cette procédure.  
  
```  
'BeginMoveFirstVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    ' connection and recordset variables  
    Dim rstAuthors As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLAuthors  
     ' record variables  
    Dim strMessage As String  
    Dim intCommand As Integer  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open recordset from Authors table  
    Set rstAuthors = New ADODB.Recordset  
    rstAuthors.CursorLocation = adUseClient  
    ' Use client cursor to enable AbsolutePosition property  
    strSQLAuthors = "Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenStatic, adLockReadOnly, adCmdTable  
  
    ' Show current record information and get user's method choice  
    Do  
        strMessage = "Name: " & rstAuthors!au_fname & " " & _  
            rstAuthors!au_lname & vbCr & "Record " & _  
            rstAuthors.AbsolutePosition & " of " & _  
            rstAuthors.RecordCount & vbCr & vbCr & _  
            "[1 - MoveFirst, 2 - MoveLast, " & vbCr & _  
            "3 - MoveNext, 4 - MovePrevious]"  
        intCommand = Val(Left(InputBox(strMessage), 1))  
  
         ' for exiting the loop  
        If intCommand < 1 Or intCommand > 4 Then  
            MsgBox "You either entered a non-number or canceled the input box. Exit the application."  
            Exit Do  
        End If  
  
        ' Use specified method while trapping for BOF and EOF  
        Select Case intCommand  
            Case 1  
                rstAuthors.MoveFirst  
            Case 2  
                rstAuthors.MoveLast  
            Case 3  
                rstAuthors.MoveNext  
                If rstAuthors.EOF Then  
                    MsgBox "Already at end of recordset!"  
                    rstAuthors.MoveLast  
                End If  
            Case 4  
                rstAuthors.MovePrevious  
                If rstAuthors.BOF Then  
                    MsgBox "Already at beginning of recordset!"  
                    rstAuthors.MoveFirst  
                End If  
        End Select  
    Loop  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
  
'EndMoveFirstVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
