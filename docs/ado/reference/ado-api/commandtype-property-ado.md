---
title: CommandType Property (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6612a90b94f10bdd08441d7814a7137121659045
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63315999"
---
# <a name="commandtype-property-ado"></a>CommandType, propriété (ADO)
Indique le type d’un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un ou plusieurs [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valeurs.  
  
> [!NOTE]
>  N’utilisez pas le **CommandTypeEnum** les valeurs de **adCmdFile** ou **adCmdTableDirect** avec **CommandType**. Ces valeurs peuvent uniquement être utilisées en tant qu’options avec les [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) et [Requery](../../../ado/reference/ado-api/requery-method.md) méthodes d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="remarks"></a>Notes  
 Utilisez le **CommandType** propriété pour optimiser l’évaluation de la [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) propriété.  
  
 Si le **CommandType** valeur de propriété est définie sur la valeur par défaut, **adCmdUnknown**, vous pouvez rencontrer les performances diminuent, car ADO doit effectuer des appels au fournisseur pour déterminer si le  **CommandText** propriété est une instruction SQL, une procédure stockée ou un nom de table. Si vous connaissez le type de commande que vous utilisez, la définition de la **CommandType** propriété à ADO d’accéder directement au code approprié. Si le **CommandType** propriété ne correspond pas au type de commande dans le **CommandText** propriété, une erreur se produit lorsque vous appelez le [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) (méthode).  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, taille et Direction, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
