---
title: SetObjectOwner, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43f325382cc556d75d7ab08c5b3dbdc94f68704f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281772"
---
# <a name="setobjectowner-method"></a>SetObjectOwner, méthode
Spécifie le propriétaire d’un objet dans un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ObjectName*  
 Un **chaîne** valeur qui spécifie le nom de l’objet pour lequel spécifier le propriétaire.  
  
 *ObjectType*  
 Un **Long** valeur qui peut être une de le [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) constantes qui spécifie le type de propriétaire.  
  
 *OwnerName*  
 Un **chaîne** valeur qui spécifie le [nom](../../../ado/reference/adox-api/name-property-adox.md) de la [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) ou [groupe](../../../ado/reference/adox-api/group-object-adox.md) au propriétaire de l’objet.  
  
 *ObjectTypeId*  
 Facultatif. Un **Variant** valeur qui spécifie le GUID d’un type d’objet de fournisseur qui n’est pas défini par la spécification OLE DB. Ce paramètre est obligatoire si *ObjectType* a la valeur **adPermObjProviderSpecific**; sinon, il n’est pas utilisé.  
  
## <a name="remarks"></a>Notes  
 Une erreur se produit si le fournisseur ne prend pas en charge en spécifiant les propriétaires d’objets.  
  
## <a name="applies-to"></a>S'applique à  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetObjectOwner et SetObjectOwner, exemples de méthodes (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner, méthode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
