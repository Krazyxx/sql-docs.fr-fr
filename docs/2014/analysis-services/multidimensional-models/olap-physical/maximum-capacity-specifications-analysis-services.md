---
title: Capacité maximale (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], maximum number
- objects [Analysis Services], maximum size
ms.assetid: 49fe1673-b908-4c7a-88ff-415efd294d27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 561cbbb64734c117b295ca6d97420b6980fa5428
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62725493"
---
# <a name="maximum-capacity-specifications-analysis-services"></a>Caractéristiques de capacité maximale (Analysis Services)
  Les tableaux suivants spécifient les tailles maximales et les nombres des différents objets définis dans les composants [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] selon des modes de déploiement de serveur différents.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Multidimensionnel et exploration de données (DeploymentMode = 0)](#bkmk_OLAP)  
  
 [SharePoint (DeploymentMode=1)](#bkmk_sharepoint)  
  
 [Tabular (DeploymentMode=2)](#bkmk_vertipaq)  
  
##  <a name="bkmk_OLAP"></a> Multidimensionnel et exploration de données (DeploymentMode = 0)  
 Le mode de stockage MOLAP, qui stocke des données et des métadonnées, a des limites physiques supplémentaires concernant les tailles de fichier. Les fichiers du magasin de chaînes ont par défaut une taille maximale de 4 Go. Si vous avez besoin de fichiers de plus grande taille pour les magasins de chaînes, vous pouvez spécifier une architecture de stockage de chaînes différente. Pour plus d’informations, consultez [configurer le stockage des chaînes pour les Dimensions et Partitions](../configure-string-storage-for-dimensions-and-partitions.md).  
  
|Object|Tailles maximales/nombres maximaux|  
|------------|----------------------------|  
|Bases de données dans une instance|2^31-1 = 2,147,483,647|  
|Dimensions dans une base de données|2^31-1 = 2,147,483,647|  
|Attributs dans une dimension|2^31-1 = 2,147,483,647|  
|Membres dans un attribut de dimension|2^31-1 = 2,147,483,647|  
|Hiérarchies définies par l'utilisateur dans une dimension|2^31-1 = 2,147,483,647|  
|Niveaux dans une hiérarchie définie par l'utilisateur|2^31-1 = 2,147,483,647|  
|Cubes dans une base de données|2^31-1 = 2,147,483,647|  
|Groupes de mesures dans un cube|2^31-1 = 2,147,483,647|  
|Mesures dans un groupe de mesures|2^31-1 = 2,147,483,647|  
|Calculs dans un cube|2^31-1 = 2,147,483,647|  
|KPI dans un cube|2^31-1 = 2,147,483,647|  
|Actions dans un cube|2^31-1 = 2,147,483,647|  
|Partitions dans un cube|2^31-1 = 2,147,483,647|  
|Traductions dans un cube|2^31-1 = 2,147,483,647|  
|Agrégations dans une partition|2^31-1 = 2,147,483,647|  
|Cellules renvoyées par une requête|2^31-1 = 2,147,483,647|  
|Taille d'enregistrement de la requête source|64 Ko|  
|Longueur des noms d’objet|100 caractères|  
|Nombre maximal d'états distincts dans une colonne d'attribut de modèle d'exploration de données|2^31-1 = 2,147,483,647|  
|Nombre maximal d'attributs pris en compte (sélection de fonctionnalité)|2^31-1 = 2,147,483,647|  
  
 Pour plus d’informations sur les instructions de dénomination d’objet, consultez [objets ASSL et caractéristiques des objets](../scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
 Pour plus d’informations sur les limites de source de données pour le traitement analytique en ligne (OLAP) et d’exploration de données, consultez [Sources de données prises en charge &#40;multidimensionnels SSAS&#41;](../supported-data-sources-ssas-multidimensional.md), [Sources de données prises en charge de &#40;SSAS multidimensionnel&#41;](../supported-data-sources-ssas-multidimensional.md), et [objets ASSL et caractéristiques des objets](../scripting-language-assl/assl-objects-and-object-characteristics.md).  
  
##  <a name="bkmk_sharepoint"></a> SharePoint (DeploymentMode=1)  
  
|Object|Tailles maximales/nombres maximaux|  
|------------|----------------------------|  
|Bases de données dans une instance|2^31-1 = 2,147,483,647|  
|Tables dans une base de données|2^31-1 = 2,147,483,647|  
|Colonnes dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :**  Nombre total de colonnes dans une table dépend du nombre total de mesures et colonnes calculées associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Lignes dans une table|Illimité **Avertissement :**  Avec la restriction qu’aucune colonne ne peut contenir plus de 1 999 999 997 valeurs distinctes.|  
|Hiérarchies dans une table|2^31-1 = 2,147,483,647|  
|Niveaux dans une hiérarchie|2^31-1 = 2,147,483,647|  
|Relations|2^31-1 = 2,147,483,647|  
|Colonnes clés dans une table|2^31-1 = 2,147,483,647|  
|Mesures dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :**  Nombre total de mesures dans une table dépend du nombre total de colonnes et colonnes calculées associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Colonnes calculées dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :**  Nombre total de colonnes calculées dans une table varie selon le nombre total de colonnes et les mesures associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Cellules renvoyées par une requête|2^31-1 = 2,147,483,647|  
|Taille d'enregistrement de la requête source|64 Ko|  
|Longueur des noms d’objet|100 caractères|  
  
##  <a name="bkmk_vertipaq"></a> Tabulaire (DeploymentMode = 2)  
  
|Object|Tailles maximales/nombres maximaux|  
|------------|----------------------------|  
|Bases de données dans une instance|2^31-1 = 2,147,483,647|  
|Tables dans une base de données|2^31-1 = 2,147,483,647|  
|Colonnes dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :**  Nombre total de colonnes dans une table dépend du nombre total de mesures et colonnes calculées associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Lignes dans une table|Illimité **Avertissement :**  Avec la restriction qu’aucune colonne dans la table ne peut avoir plus de 1 999 999 997 valeurs distinctes.|  
|Hiérarchies dans une table|2^31-1 = 2,147,483,647|  
|Niveaux dans une hiérarchie|2^31-1 = 2,147,483,647|  
|Relations|2^31-1 = 2,147,483,647|  
|Colonnes clés dans une table|2^31-1 = 2,147,483,647|  
|Mesures dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :**  Nombre total de mesures dans une table dépend du nombre total de colonnes et colonnes calculées associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Colonnes calculées dans une table|2 ^ 31-1 = 2 147 483 647 **Avertissement :**  Nombre total de colonnes calculées dans une table varie selon le nombre total de colonnes et les mesures associées à la même table. Le nombre maximal de « Colonnes + Mesures + Colonnes calculées » pour une table est 2^31-1 = 2 147 483 647|  
|Cellules renvoyées par une requête|2^31-1 = 2,147,483,647|  
|Taille d'enregistrement de la requête source|64 Ko|  
|Longueur des noms d’objet|100 caractères|  
  
## <a name="see-also"></a>Voir aussi  
 [Déterminer le mode serveur d'une instance Analysis Services](../../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Propriétés générales](../../server-properties/general-properties.md)  
  
  
