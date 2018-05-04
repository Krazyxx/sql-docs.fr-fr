---
title: Type de propriété (ADO) | Documents Microsoft
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
apitype: COM
f1_keywords:
- _Parameter::Type
- Field20::Type
helpviewer_keywords:
- Type property [ADO]
ms.assetid: 8a4c079f-9f4f-4545-801d-85983b8db71e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91e4e4e3b7a4c1c16b16cb5ffc61c5337b761260
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="type-property-ado"></a>Type, propriété (ADO)
Indique le type de données ou de type opérationnel d’un [paramètre](../../../ado/reference/ado-api/parameter-object.md), [champ](../../../ado/reference/ado-api/field-object.md), ou [propriété](../../../ado/reference/ado-api/property-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) valeur.  
  
## <a name="remarks"></a>Notes  
 Pour **paramètre** objets, la **Type** propriété est en lecture/écriture. Pour les nouveaux **champ** les objets qui ont été ajoutées à la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), **Type** est en lecture/écriture uniquement après le [ Valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété pour le **champ** a été spécifié et le fournisseur de données a ajouté le nouveau **champ** en appelant le [mettre à jour](../../../ado/reference/ado-api/update-method.md)(méthode) de la **champs** collection.  
  
 Pour tous les autres objets, la **Type** propriété est en lecture seule.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Field, objet](../../../ado/reference/ado-api/field-object.md)|[Parameter, objet](../../../ado/reference/ado-api/parameter-object.md)|[Property, objet (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de type de propriété (champ) (VB)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Exemple de propriété de type (propriété) (VC ++)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [RecordType, propriété (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type, propriété (objet Stream ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)