---
title: Traitement des exigences et considérations (exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], objects
- mining structures [Analysis Services], processing
- mining models [Analysis Services], processing
ms.assetid: f7331261-6f1c-4986-b2c7-740f4b92ca44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 181e2a367f6196d50f90aee77ca9590f55ba0ce4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62733061"
---
# <a name="processing-requirements-and-considerations-data-mining"></a>Exigences et considérations concernant le traitement (exploration de données)
  Cette rubrique décrit quelques considérations techniques que vous devez garder à l'esprit lors du traitement des objets d'exploration de données. Pour une présentation générale du traitement et de la manière dont il s’applique à l’exploration de données, consultez [Traitement des objets d’exploration de données](processing-data-mining-objects.md).  
  
 [Requêtes sur le magasin relationnel](#bkmk_QueryReqs)  
  
 [Traitement des structures d'exploration de données](#bkmk_ProcessStructures)  
  
 [Traitement des modèles d'exploration de données](#bkmk_ProcessModels)  
  
##  <a name="bkmk_QueryReqs"></a> Requêtes sur le magasin relationnel au cours du traitement  
 Pour l'exploration de données, le traitement s'effectue en trois phases : l'interrogation des données sources, la détermination des statistiques brutes et l'utilisation de la définition et de l'algorithme du modèle pour l'apprentissage du modèle d'exploration de données.  
  
 Le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] émet des requêtes vers la base de données qui fournit les données brutes. Cette base de données peut être une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou d’une version antérieure du moteur de base de données SQL Server. Pendant le traitement d’une structure d’exploration de données, les données de la source sont transférées à cette structure et conservées sur le disque dans un nouveau format compressé. Seules certaines colonnes de la source de données sont traitées : il s’agit des colonnes incluses dans la structure d’exploration de données, comme défini par les liaisons.  
  
 À l'aide de ces données, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] génère un index de toutes les données et colonnes discrétisées, et crée un index séparé pour les colonnes continues. Une requête est émise pour chaque table imbriquée pour créer l'index. De plus, une requête supplémentaire par table imbriquée est générée pour traiter les relations entre chaque paire table imbriquée/table de cas. La raison pour laquelle il convient de créer plusieurs requêtes est le traitement d'une banque de données multidimensionnelle interne spéciale. Vous pouvez limiter le nombre de requêtes qu'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] envoie au magasin relationnel en définissant la propriété de serveur `DatabaseConnectionPoolMax`. Pour plus d’informations, consultez [Propriétés OLAP](../server-properties/olap-properties.md).  
  
 Lors du traitement du modèle, celui-ci ne relit pas les données à partir de la source de données, mais il récupère à la place un résumé des données à partir de la structure d'exploration de données. À l'aide du cube qui a été créé, ainsi que des données d'index et de cas mises en cache, le serveur crée des threads indépendants pour l'apprentissage des modèles.  
  
 Pour plus d’informations sur les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui prennent en charge le traitement de modèles parallèles, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).  
  
##  <a name="bkmk_ProcessStructures"></a> Traitement des structures d'exploration de données  
 Une structure d'exploration de données peut être traitée avec tous les modèles dépendants, ou séparément. Le traitement d'une structure d'exploration de données séparément des modèles peut être utile lorsqu'il est envisagé que le traitement de certains modèles prenne beaucoup de temps et que vous souhaitez différer cette opération.  
  
 Pour plus d’informations, consultez [Traiter une structure d’exploration de données](process-a-mining-structure.md).  
  
 Si vous êtes désireux de conserver de l'espace disponible sur le disque dur, notez que [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] conserve localement les caches de structure d'exploration de données. Cela signifie que toutes les données d'apprentissage sont recopiées sur votre disque dur local. Si vous ne voulez pas mettre en cache ces données, vous pouvez modifier le paramètre par défaut en attribuant à la propriété <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> sur la structure d'exploration de données la valeur `ClearAfterProcessing`. Cela aura pour conséquence de supprimer le cache une fois les modèles traités et de désactiver l'extraction sur la structure d'exploration de données. Pour plus d’informations, consultez [Requêtes d’extraction &#40;exploration de données&#41;](drillthrough-queries-data-mining.md).  
  
 Par ailleurs, si vous effacez le cache, vous ne pourrez pas utiliser le jeu de test d'exclusion (si vous en avez défini un) et la définition de la partition du jeu de test sera perdue. Pour plus d’informations sur les ensembles de tests d’exclusion, consultez [Jeux de données d’apprentissage et de test](training-and-testing-data-sets.md).  
  
##  <a name="bkmk_ProcessModels"></a> Traitement des modèles d'exploration de données  
 Vous pouvez traiter un modèle d'exploration de données séparément de la structure d'exploration de données associée, ou vous pouvez traiter tous les modèles basés sur la structure avec cette dernière.  
  
 Pour plus d’informations, consultez [Traiter un modèle d’exploration de données](process-a-mining-model.md).  
  
 Toutefois, dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous ne pouvez pas sélectionner plusieurs modèles d’exploration de données à traiter avec la structure. Si vous devez contrôler les modèles traités, vous devez les sélectionner individuellement, ou utiliser XMLA ou DMX pour les traiter en série.  
  
## <a name="when-reprocessing-is-required"></a>Lorsqu'un retraitement est requis  
 Vous devez traiter les modèles [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que vous définissez avant de commencer à les utiliser. Vous devez également retraiter les modèles d'exploration de données chaque fois que vous modifiez la structure d'exploration de données, mettez à jour les données d'apprentissage, modifiez un modèle d'exploration de données existant ou ajoutez un nouveau modèle d'exploration de données à la structure.  
  
 Les modèles d'exploration de données sont également traités dans les scénarios suivants :  
  
 **Déploiement d’un projet**: Selon les paramètres du projet et l’état actuel du projet, les modèles d’exploration de données dans le projet sont généralement traités intégralement lorsque le projet est déployé.  
  
 Lorsque vous commencez le déploiement, le traitement démarre automatiquement, à moins qu'il n'existe une version préalablement traitée sur le serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et qu'aucune modification sur la structure n'ait eu lieu. Vous pouvez déployer un projet en sélectionnant **Déployer la solution** dans la liste déroulante ou en appuyant sur la touche F5. Plusieurs possibilités s'offrent à vous :  
  
 Pour plus d’informations sur la définition des propriétés de déploiement d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contrôlent la manière dont les modèles d’exploration de données sont déployés, consultez [Déploiement de solutions d’exploration de données](deployment-of-data-mining-solutions.md).  
  
 **Déplacement d’un modèle d’exploration de données**: Lorsque vous déplacez un modèle d’exploration de données à l’aide de la commande d’exportation, uniquement la définition du modèle est exportée, qui inclut le nom de la structure d’exploration de données qui est censé fournir des données au modèle.  
  
 Exigences de retraitement pour les scénarios suivants utilisant les commandes EXPORT et IMPORT :  
  
-   La structure d'exploration de données existe sur l'instance cible et la structure d'exploration de données est dans un état non traité.  
  
     La structure et le modèle doivent être retraités.  
  
-   La structure d'exploration de données existe sur l'instance cible et la structure d'exploration de données a été traitée. Seul le modèle d'exploration de données a été exporté.  
  
     Le modèle peut être utilisé sans traitement.  
  
-   La définition de la structure d'exploration de données a également été exportée à l'aide du mot-clé WITH DEPENDENCIES.  
  
     La structure et le modèle doivent être retraités.  
  
 Pour plus d’informations, consultez [Exporter et importer des objets d’exploration de données](export-and-import-data-mining-objects.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Structures d’exploration de données &#40;Analysis Services – Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services – Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)   
 [Traitement des objets de modèle multidimensionnel](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  
