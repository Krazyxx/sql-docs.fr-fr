---
title: Position, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Position
helpviewer_keywords:
- Position property [ADO]
ms.assetid: daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 333b06ef76ae6407ca8a5605f1917dc0bb609aca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63027828"
---
# <a name="position-property-ado"></a>Position, propriété (ADO)
Indique la position actuelle dans un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Long** valeur qui indique l’offset, en octets, de la position actuelle à partir du début du flux. La valeur par défaut est 0, ce qui représente le premier octet dans le flux.  
  
## <a name="remarks"></a>Notes  
 La position actuelle peut être déplacée vers un point après la fin du flux. Si vous spécifiez la position actuelle après la fin du flux, le [taille](../../../ado/reference/ado-api/size-property-ado-stream.md) de la **Stream** objet augmente en conséquence. Les nouveaux octets ajoutés de cette façon sera null.  
  
> [!NOTE]
>  **Position** mesure toujours des octets. Pour les flux de texte à l’aide de jeux de caractères multioctets, multipliez la position par la taille des caractères pour déterminer le nombre de caractères. Par exemple, pour un jeu de caractères de deux octets, le premier caractère est à la position 0, le deuxième caractère à la position 2, le troisième caractère à la position 4 et ainsi de suite.  
  
> [!NOTE]
>  Les valeurs négatives ne peut pas être utilisés pour modifier la position actuelle dans un **Stream**. Seuls les nombres positifs peuvent être utilisés pour **Position**.  
  
> [!NOTE]
>  Pour en lecture seule **Stream** ADO ne renvoie pas une erreur si des objets **Position** a une valeur supérieure à la **taille** de la **Stream**. Cela ne modifie pas la taille de la **Stream**, ou modifiez la **Stream** contenu en aucune façon. Toutefois, cela doit être évité, car il en résulte un sans signification **Position**valeur.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Charset, propriété (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)
