---
title: InstanceOf (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf method
ms.assetid: 1eaed0e4-1c72-45a9-9926-5b513335cf33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e0ef6816efa98d3e9b2da27525d700fb4eba2501
ms.sourcegitcommit: c3b190f8f87a4c80bc9126bb244896197a6dc453
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56852994"
---
# <a name="instanceof-geography-data-type"></a>InstanceOf (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Teste si l’instance **geography** est du même type que l’instance spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
  
.InstanceOf ( 'geography_type')  
```  
  
## <a name="arguments"></a>Arguments  
*geography_type*  
Chaîne **nvarchar(4000)** spécifiant l’un des 16 types exposés dans la hiérarchie de type **geography**.  
  
## <a name="return-types"></a>Types de retour  
Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes   
Retourne 1 si le type d’une instance **geography** est identique au type spécifié, ou si le type spécifié est un ancêtre du type d’instance ; sinon, retourne 0.  
  
Cette méthode de type de données **geography** prend en charge les instances **FullGlobe** ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
L’entrée de la méthode doit être l’un de ces types : Geometry, Point, Curve, LineString, CircularString, Surface, Polygon, CurvePolygon, **GeometryCollection**, **MultiSurface**, **MultiPolygon, MultiCurve, MultiLineString**, **MultiPoint** ou **FullGlobe**.  
  
Cette méthode lève une `ArgumentException` si vous utilisez d’autres chaînes comme entrée.  
  
Cette méthode n'est pas précise.  
  
## <a name="examples"></a>Exemples  
L'exemple suivant crée une instance `MultiPoint` et utilise `InstanceOf()` pour voir si l'instance est de type `GeometryCollection`.  
  
```sql  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes étendues sur des instances geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
