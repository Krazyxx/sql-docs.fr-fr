---
title: Onglet Discrimination (visionneuse de modèle d’exploration de données) de cluster | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.discrimination.f1
ms.assetid: ae7cfff7-ab1c-4cf5-9a91-97b21d15d85f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 68f52f1e64d46b2509ae995a1f0dfa56c4dad22f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62680829"
---
# <a name="cluster-discrimination-tab-mining-model-viewer"></a>Onglet Discrimination de cluster (Visionneuse de modèle d'exploration de données)
  Utilisez l’onglet **Discrimination de cluster** pour comparer deux clusters qui existent dans un modèle Sequence Clustering. Vous pouvez voir comment différentes combinaisons d'attributs et de valeurs sont représentées dans les clusters.  
  
 **Pour plus d’informations :** [Algorithme de gestion de clusters Microsoft](data-mining/microsoft-clustering-algorithm.md), [Explorer un modèle à l’aide de Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données parmi ceux de la structure d'exploration de données active. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée pour les modèles de clustering, ou la visionneuse de contenu d’exploration de données ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer). Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Cluster 1**  
 Sélectionnez un cluster afin de le comparer à un autre cluster.  
  
 **Cluster 2**  
 Sélectionnez un deuxième cluster dans la liste de clusters du modèle d’exploration des données pour le comparer au **Cluster 1**. Vous pouvez également comparer un cluster à son complément, ce qui correspond à tous les cas du modèle à l'exception de ceux du cluster sélectionné.  
  
 **Scores de discrimination pour \<cluster 1 > et \<cluster 2 >**  
 Les colonnes dans le graphique fournissent des informations sur la façon dont chaque paire attribut-valeur se rapporte aux deux clusters sélectionnés.  
  
|||  
|-|-|  
|**Variables**|Attribut du modèle d'exploration de données.|  
|**Valeurs**|Valeur de l’attribut sélectionné dans **Variables**.|  
|**Privilégie \<cluster 1 >**|Le graphique à barres à gauche représente la probabilité que la paire attribut-valeur sélectionnée soit représentative du cluster sélectionné dans **Cluster 1**. Vous pouvez positionner la souris sur la barre pour afficher la valeur, représentée en pourcentage. Notez que même si la valeur est zéro, cela ne signifie pas que la valeur d’attribut est nécessairement manquante du cluster, simplement que la distribution privilégie fortement un cluster plutôt que l’autre.|  
|**Privilégie \<cluster 2 >**|Le graphique à barres à droite représente la probabilité que la paire attribut-valeur sélectionnée soit représentative du cluster sélectionné dans **Cluster 2**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  
