---
title: DELETE, méthode (Collection de paramètres ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Delete
- _DynaCollection::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8864ac47f3fa212cc6c204cc79d587b8952512cd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140162"
---
# <a name="delete-method-ado-parameters-collection"></a>Delete, méthode (collection Parameters ADO)
Supprime un objet à partir de la [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Index*  
 Un **chaîne** valeur qui contient le nom de l’objet que vous souhaitez supprimer, ou position ordinale de l’objet (index) dans la collection.  
  
## <a name="remarks"></a>Notes  
 À l’aide de la **supprimer** méthode sur une collection vous permet de supprimer un des objets dans la collection. Cette méthode est uniquement disponible sur le **paramètres** collection d’un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet. Vous devez utiliser le [paramètre](../../../ado/reference/ado-api/parameter-object.md) l’objet [nom](../../../ado/reference/ado-api/name-property-ado.md) propriété ou son index de collection lorsque vous appelez le **supprimer** variable méthode un objet n’est pas un argument valide.  
  
## <a name="applies-to"></a>S'applique à  
 [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, méthode (Collection de champs ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [DELETE, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord, méthode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
