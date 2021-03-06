---
title: AbsolutePage, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AbsolutePage
helpviewer_keywords:
- AbsolutePage property [ADO]
ms.assetid: ddb58a35-ec3a-423c-a504-3c65e62c23d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efdbd68bf464fea3a0d59396380b082eb66375b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156586"
---
# <a name="absolutepage-property-ado"></a>AbsolutePage, propriété (ADO)
Indique la page sur laquelle réside l’enregistrement actif.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Pour le code 32 bits, définit ou retourne un **Long** valeur entre 1 et le nombre de pages dans le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet ([PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)), ou retourne une de la [PositionEnum ](../../../ado/reference/ado-api/positionenum.md) valeurs.  
  
 Pour le code de 64 bits, utilisez un type de données qui fournit pour le stockage d’une valeur 64 bits. Par exemple, vous pouvez utiliser soit **Long** ou une autre valeur peut être de longueur de 64 bits comme DBORDINAL. N’utilisez pas **PositionEnum** valeurs, car ils sont limités à la longueur de 32 bits.  
  
## <a name="remarks"></a>Notes  
 Cette propriété peut être utilisée pour identifier le numéro de page sur lequel se trouve l’enregistrement actif. Il utilise le [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) propriété pour séparer logiquement le nombre total de lignes de la **Recordset** objet en une série de pages, chacun d’eux possède le nombre d’enregistrements égales à **PageSize** (à l’exception de la dernière page, qui peut avoir moins d’enregistrements). Le fournisseur doit prendre en charge les fonctionnalités requises pour cette propriété doit être disponible.  
  
-   Lors de l’obtention ou la définition du **AbsolutePage** propriété, ADO utilise le [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) propriété et la [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) propriété ensemble comme suit :  
  
-   Pour obtenir le **AbsolutePage**, ADO récupère d’abord le **AbsolutePosition**et il divise par la **PageSize**.  
  
-   Pour définir le **AbsolutePage**, ADO déplace le **AbsolutePosition** comme suit : elle multiplie la **PageSize** par la nouvelle **AbsolutePage** valeur, puis ajoute 1 à la valeur. Par conséquent, la position actuelle dans le **Recordset** une fois la valeur **AbsolutePage** est le premier enregistrement de cette page.  
  
 Comme le **AbsolutePosition** propriété, **AbsolutePage** basé sur 1 et est égale à 1 lors de l’enregistrement actif est le premier enregistrement dans le **Recordset**. Définissez cette propriété pour déplacer vers le premier enregistrement d’une page particulière. Obtenir le nombre total de pages à partir de la **PageCount** propriété.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AbsolutePage, PageCount et PageSize, exemple de propriétés (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount et PageSize, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePosition, propriété (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [PageCount, propriété (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)   
 [PageSize, propriété (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)
