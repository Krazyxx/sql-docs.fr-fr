---
title: STGeometryType (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryType_TSQL
- STGeometryType (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryType (geometry Data Type)
ms.assetid: 224cdc83-aa83-4ad4-bb82-b7481031e910
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3c91ae4decb540d80e371153504121ee22bf3ccc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47663457"
---
# <a name="stgeometrytype-geometry-data-type"></a>STGeometryType (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne le nom de type OGC (Open Geospatial Consortium) représenté par une instance **geometry**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STGeometryType ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **nvarchar(4000)**  
  
 Type de retour CLR : **SqlString**  
  
## <a name="remarks"></a>Notes   
 Les noms de types OGC qui peuvent être retournés par `STGeometryType()` sont **Point**, **LineString**, **CircularString**, **CompoundCurve**, **Polygon, CurvePolygon**, **GeometryCollection**, **MultiPoint**, **MultiLineString** et **MultiPolygon**.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `Polygon` et utilise `STGeometryType()` pour confirmer qu'il s'agit d'un polygone.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0))', 0);  
SELECT @g.STGeometryType();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

