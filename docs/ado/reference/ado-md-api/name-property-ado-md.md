---
title: Name, propriété (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Name
- CubeDef::Name
- Member::Name
- Catalog::Name
- Dimension::Name
- Name
- Axis::Name
- Hierarchy::Name
helpviewer_keywords:
- Name property [ADO MD]
ms.assetid: 4a04380b-51dc-4aaf-8d25-123cdd589641
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c6c9ba7f2981fd4162f93f37e6ad0eb2cbae882
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63311908"
---
# <a name="name-property-ado-md"></a>Name, propriété (ADO MD)
Indique le nom d’un objet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **chaîne** et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez récupérer le **nom** propriété d’un objet par référence ordinale, après quoi vous pouvez faire référence à l’objet directement par nom. Par exemple, si `cdf.CubeDefs(0).Name` génère « Vidéo de Bobs Store », vous pouvez vous reporter à [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) comme `cdf.CubeDefs("Bobs Video Store")`.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Axis, objet (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|[Catalog, objet (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[CubeDef, objet (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|  
|[Dimension, objet (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Hierarchy, objet (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|[Level, objet (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|  
|[Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)|||  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de catalogue (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Caption, propriété (ADO MD)](../../../ado/reference/ado-md-api/caption-property-ado-md.md)   
 [Description, propriété (ADO MD)](../../../ado/reference/ado-md-api/description-property-ado-md.md)   
 [UniqueName, propriété (ADO MD)](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)
