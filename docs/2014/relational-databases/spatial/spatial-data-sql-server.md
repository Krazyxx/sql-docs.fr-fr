---
title: Données spatiales (SQL Server) | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fb30ce3e7115bad41d26dd126b6f8b9ae9e0b934
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199055"
---
# <a name="spatial-data-sql-server"></a>Données spatiales (SQL Server)
  Les données spatiales représentent des informations relatives à l'emplacement physique et à la forme d'objets géométriques. Ces objets peuvent être des emplacements de points ou des objets plus complexes tels que des pays, des routes ou des lacs.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge deux types de données spatiales : le type de données `geometry` et le type de données `geography`.  
  
-   Le type `geometry` représente des données dans un système de coordonnées euclidien (plat).  
  
-   Le type `geography` représente des données dans un système de coordonnées de monde sphérique.  
  
 Ces deux types de données sont implémentés comme types de données CLR .NET dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Pour obtenir une description détaillée et des exemples des fonctionnalités spatiales introduites dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], téléchargez le livre blanc intitulé [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407)(Nouvelles fonctionnalités spatiales dans SQL Server 2012).  
  
##  <a name="reltasks"></a> Tâches associées  
 [Créer, construire et interroger des instances geometry](create-construct-and-query-geometry-instances.md)  
 Décrit les méthodes que vous pouvez utiliser avec des instances du type de données geometry.  
  
 [Créer, construire et interroger des instances geography](create-construct-and-query-geography-instances.md)  
 Décrit les méthodes que vous pouvez utiliser avec des instances du type de données geography.  
  
 [Interroger des données spatiales au sujet du plus proche voisin](query-spatial-data-for-nearest-neighbor.md)  
 Décrit le modèle de requête commun qui est utilisé pour rechercher les objets spatiaux les plus proches d'un objet spatial spécifique.  
  
 [Créer, modifier et supprimer les index spatiaux](create-modify-and-drop-spatial-indexes.md)  
 Fournit des informations sur la création, la modification et la suppression d'un index spatial.  
  
## <a name="related-content"></a>Contenu associé  
 [Présentation des types de données spatiales](spatial-data-types-overview.md)  
 Présente les types de données spatiales.  
  
-   [Point](point.md)  
  
-   [LineString](linestring.md)  
  
-   [CircularString](circularstring.md)  
  
-   [CompoundCurve](compoundcurve.md)  
  
-   [Polygone](polygon.md)  
  
-   [CurvePolygon](curvepolygon.md)  
  
-   [MultiPoint](multipoint.md)  
  
-   [MultiLineString](multilinestring.md)  
  
-   [MultiPolygon](multipolygon.md)  
  
-   [GeometryCollection](geometrycollection.md)  
  
 [Vue d'ensemble des index spatiaux](spatial-indexes-overview.md)  
 Présente les index spatiaux et décrit le pavage et les schémas de pavage.  
  
  
