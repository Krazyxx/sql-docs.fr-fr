---
title: Vérification des propriétés de Dimension et de Cube | Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 97b12ad51affaebb87f152938bdfbfae16bd8900
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403731"
---
# <a name="lesson-2-4---reviewing-cube-and-dimension-properties"></a>Leçon 2-4 : examen des propriétés de Cube et Dimension
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Après avoir défini un cube, vous pouvez examiner les résultats en utilisant le Concepteur de cube. Dans la tâche suivante, vous examinez la structure du cube dans le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial.  
  
### <a name="to-review-cube-and-dimension-properties-in-cube-designer"></a>Pour vérifier les propriétés d'un cube et des dimensions dans le Concepteur de cube  
  
1.  Pour ouvrir le Concepteur de cube, double-cliquez sur le cube **Analysis Services Tutorial** dans le nœud **Cubes** de l’Explorateur de solutions.  
  
2.  Dans le volet **Mesures** de l'onglet **Structure de cube** dans le Concepteur de cube, développez le groupe de mesures **Internet Sales** pour révéler les mesures définies.  
  
    Vous pouvez modifier l'ordre en faisant glisser les mesures et en les plaçant dans l'ordre de votre choix. Cet ordre aura une incidence sur la façon dont certaines applications clientes classent ces mesures. Le groupe de mesures et chaque mesure dans ce groupe ont des propriétés que vous pouvez modifier dans la fenêtre des propriétés.  
  
3.  Dans le volet **Dimensions** de l'onglet **Structure de cube** du Concepteur de cube, vérifiez les dimensions de cube que contient le cube du didacticiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
    Notez que si seulement trois dimensions ont été créées au niveau base de données (affichées dans l'Explorateur de solutions), cinq dimensions de cube existent dans le cube du didacticiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Le cube contient davantage de dimensions que la base de données car la dimension de base de données Date est utilisée comme base pour trois dimensions de cube liées à la date distinctes, basées sur des faits liés à la date et différents dans la table de faits. Ces dimensions liées à la date sont également appelées des *dimensions de rôle actif*. Ces trois dimensions de cube liées à la date permettent aux utilisateurs de dimensionner le cube selon trois faits distincts liés à chaque vente de produits : la date de commande du produit, la date d'échéance de l'exécution de la commande et la date d'expédition de la commande. En réutilisant une seule dimension de base de données pour plusieurs dimensions de cube, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] simplifie la gestion des dimensions, utilise moins d'espace disque et réduit la durée globale de traitement.  
  
4.  Dans le volet **Dimensions** de l'onglet **Structure de cube** , développez **Customer**, puis cliquez sur **Edit Customer** pour ouvrir la dimension dans le Concepteur de dimensions.  
  
    Concepteur de dimensions contient ces onglets : **Structure de dimension**, **relations d’attributs**, **traductions**, et **navigateur**. Notez que le **Structure de Dimension** onglet comporte trois volets : **Attributs**, **hiérarchies**, et **vue de Source de données**. Les attributs que la dimension contient apparaissent dans le volet **Attributs** . Pour plus d’informations, consultez [Référence des propriétés d’attribut de dimension](../multidimensional-models/dimension-attribute-properties-reference.md), [Créer des hiérarchies définies par l’utilisateur](../multidimensional-models/user-defined-hierarchies-create.md) et [Définir des relations d’attributs](../multidimensional-models/attribute-relationships-define.md).  
  
5.  Pour basculer vers le Concepteur de cube, cliquez avec le bouton droit sur le cube **Analysis Services Tutorial** dans le nœud **Cubes** de l’Explorateur de solutions, puis cliquez sur **Concepteur de vues**.  
  
6.  Dans le Concepteur de cube, cliquez sur l'onglet **Utilisation de la dimension** .  
  
    Dans cette vue du cube du didacticiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous pouvez voir les dimensions du cube qui sont utilisées par le groupe de mesures Internet Sales. Vous pouvez également définir le type de relation entre chaque dimension et chaque groupe de mesures dans lequel elles sont utilisées.  
  
7.  Cliquez sur l'onglet **Partitions** .  
  
    L'Assistant Cube définit une seule partition pour le cube en utilisant le mode de stockage MOLAP (Multidimensional Online Analytical Processing) sans agrégations. Avec MOLAP, toutes les données de niveau feuille et toutes les agrégations sont stockées dans le cube de façon à obtenir des performances maximales. Les agrégations sont des données de synthèse précalculées qui améliorent les temps de réponse des requêtes, tout simplement parce que les réponses sont prêtes avant que les questions ne soient posées. Vous pouvez définir d'autres partitions, paramètres de stockage et paramètres d'écriture différée dans l'onglet **Partitions** . Pour plus d’informations, consultez [Partitions &#40;Analysis Services - Données multidimensionnelles&#41;](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) et [Agrégations et conceptions d’agrégation](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
8.  Cliquez sur l'onglet **Navigateur** .  
  
    Notez que le cube ne peut pas être exploré car il n'a pas encore été déployé sur une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. À ce stade, le cube du projet du didacticiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est simplement une définition de cube que vous pouvez déployer sur une instance quelconque de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Lorsque vous déployez et traitez un cube, vous créez les objets définis dans une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et remplissez les objets à partir des données issues des sources de données sous-jacentes.  
  
9. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Analysis Services Tutorial** dans le nœud **Cubes** , puis cliquez sur **Afficher le code**. Cela peut prendre un certain temps.  
  
    Le code XML du cube du didacticiel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est affiché sous l’onglet **[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial.cube [XML]** . Ce code est celui utilisé pour créer le cube dans une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] au cours du déploiement. Pour plus d’informations, consultez [Afficher le code XML d’un projet Analysis Services &#40;SSDT&#41;](../multidimensional-models/view-the-xml-for-an-analysis-services-project-ssdt.md).  
  
10. Fermez l'onglet du code XML.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Déploiement d’un projet Analysis Services](lesson-2-5-deploying-an-analysis-services-project.md)  
  
## <a name="see-also"></a>Voir aussi  
[Explorer les données d'une dimension dans le Concepteur de dimensions](../multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)  
  
  
  
