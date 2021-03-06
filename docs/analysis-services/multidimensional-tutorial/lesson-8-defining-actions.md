---
title: 'Leçon 8 : Définition des Actions | Microsoft Docs'
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2f233bab0c90abf41ab8fbef923e7c7b920ff2c3
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403671"
---
# <a name="lesson-8-defining-actions"></a>Leçon 8 : Définition des actions
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Dans cette leçon, vous allez apprendre à définir des actions dans votre projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Une action est simplement une instruction MDX (Multidimensional Expressions) qui est stockée dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et peut être incorporée dans des applications clientes et démarrée par un utilisateur.  
  
> [!NOTE]  
> Les projets achevés de toutes les leçons de ce didacticiel sont disponibles en ligne. Vous pouvez sauter des leçons en utilisant le projet achevé de la leçon précédente comme point de départ. [Cliquez ici](http://go.microsoft.com/fwlink/?LinkID=221866) pour télécharger les exemples de projet de ce didacticiel.  
  
[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les types d’actions décrits dans le tableau suivant.  
  
|||  
|-|-|  
|CommandLine|Exécute une commande à partir de l'invite de commandes.|  
|Dataset|Renvoie un groupe de données à une application cliente.|  
|Extraction|Retourne une instruction d'extraction comme expression que le client exécute pour retourner un ensemble de lignes.|  
|Html|Exécute un script HTML dans un navigateur Internet.|  
|Propriétaire|Effectue une opération en utilisant une interface différente de celles répertoriées dans ce tableau.|  
|Rapport|Soumet une demande paramétrable basée sur une URL à un serveur de rapports et renvoie un rapport à une application cliente.|  
|Ensemble de lignes|Renvoie un ensemble de lignes à une application cliente.|  
|.|Exécute une commande OLE DB.|  
|URL|Affiche une page web dynamique dans un navigateur Internet.|  
  
Les actions permettent aux utilisateurs de démarrer une application ou d'effectuer d'autres étapes dans le contexte d'un élément sélectionné. Pour plus d’informations, consultez [Actions &#40;Analysis Services - Données multidimensionnelles&#41;](../multidimensional-models/actions-analysis-services-multidimensional-data.md), [Actions dans les modèles multidimensionnels](../multidimensional-models/actions-in-multidimensional-models.md)  
  
> [!NOTE]  
> Pour obtenir des exemples d'actions, consultez les exemples d'action de l'onglet Modèles du volet Outils de calcul ou dans les exemples de l'entrepôt de données [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] DW. Pour plus d’informations sur l’installation de cette base de données, consultez [Installer les exemples de données et de projets pour le didacticiel sur la modélisation multidimensionnelle Analysis Services](install-sample-data-and-projects.md).  
  
Cette leçon inclut la tâche suivante :  
  
[Définition et utilisation d'une action d'extraction](lesson-8-1-defining-and-using-a-drillthrough-action.md)  
Dans cette tâche, vous définissez, utilisez puis modifiez une action d'extraction à travers la relation de dimension de fait que vous avez définie antérieurement dans ce didacticiel.  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 9 : Définition de Perspectives et traductions](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a>Voir aussi  
[Scénario du tutoriel Analysis Services](analysis-services-tutorial-scenario.md)  
[Modélisation multidimensionnelle &#40;didacticiel Adventure Works&#41;](multidimensional-modeling-adventure-works-tutorial.md)  
[Actions &#40;Analysis Services - Données multidimensionnelles&#41;](../multidimensional-models/actions-analysis-services-multidimensional-data.md)  
[Actions dans les modèles multidimensionnels](../multidimensional-models/actions-in-multidimensional-models.md)  
  
  
  
