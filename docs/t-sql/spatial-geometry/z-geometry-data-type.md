---
title: Z (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Z (geometry Data Type)
- Z_(geometry_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Z (geometry Data Type)
ms.assetid: a62ed736-44df-4591-9109-ce90e1df9bd3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f48bfcf74a53cec829dba8171c9c66abc3c0254b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607681"
---
# <a name="z-geometry-data-type"></a>Z (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Valeur Z (élévation) de l'instance. La sémantique de la valeur d'élévation est définie par l'utilisateur.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>Types de retour  
 Type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes   
 La valeur de cette propriété est Null si l’instance geometry n’est pas un point, ainsi que pour toute instance **Point** pour laquelle elle n’est pas définie.  
  
 Cette propriété est en lecture seule.  
  
 Les coordonnées Z ne sont pas utilisées dans les calculs effectués par la bibliothèque et ne sont pas reportées dans les calculs de bibliothèque.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `Point` avec des valeurs Z (élévation) et M (mesure) et utilise `Z` pour extraire la valeur Z de l'instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a> Voir aussi  
 [M &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [AsTextZM &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/astextzm-geometry-data-type.md)   
 [Méthodes étendues sur des instances geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

