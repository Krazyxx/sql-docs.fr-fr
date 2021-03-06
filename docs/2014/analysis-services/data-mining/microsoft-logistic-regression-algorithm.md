---
title: Algorithme de régression logistique de Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logical regression algorithms [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 3dd54d07-1c3b-4b87-b7f0-b962ed8cf844
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 577ab402178272c5f20f3a17f167c8dadb4fe7fd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62733747"
---
# <a name="microsoft-logistic-regression-algorithm"></a>Algorithme MLR (Microsoft Logistic Regression)
  La régression logistique est une technique statistique connue utilisée pour modéliser les résultats binaires.  
  
 Il existe différentes implémentations de régression logistique dans la recherche de statistiques, qui utilisent différentes techniques d'apprentissage. L'algorithme de régression logistique de [!INCLUDE[msCoName](../../includes/msconame-md.md)] a été implémenté en utilisant une variante de l'algorithme MNN de réseau neuronal de [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Cet algorithme partage un grand nombre des qualités des réseaux neuronaux, mais son apprentissage est plus aisé.  
  
 L'un des avantages de la régression logistique vient du fait que l'algorithme est très flexible (acceptant tout type d'entrée) et prend en charge plusieurs tâches analytiques différentes :  
  
-   Utilisation des statistiques démographiques pour élaborer des prédictions sur les résultats, tels que le risque de contracter une certaine maladie.  
  
-   Exploration et évaluation des facteurs qui contribuent à un résultat. Par exemple, vous pouvez rechercher les facteurs qui influencent les clients à se rendre plusieurs fois dans un magasin.  
  
-   Classification de documents, messages électroniques ou autres objets ayant de nombreux attributs.  
  
## <a name="example"></a>Exemple  
 Considérez un groupe de personnes qui partagent des informations démographiques similaires et qui achètent des produits de la société Adventure Works. En modélisant les données à lier à un résultat spécifique, tel que l'achat d'un produit cible, vous pouvez voir comment les informations démographiques contribuent à la probabilité de l’achat du produit cible.  
  
## <a name="how-the-algorithm-works"></a>Fonctionnement de l'algorithme  
 La régression logistique est une méthode statistique connue qui permet de déterminer la contribution de plusieurs facteurs à une paire de résultats. L'implémentation Microsoft utilise un réseau neuronal modifié pour modéliser les relations entre les entrées et les sorties. L'effet de chaque entrée sur la sortie est mesuré, et les diverses entrées sont pondérées dans le modèle fini. Le nom de régression logistique vient du fait que la courbe de données est compressée par une transformation logistique afin de réduire l'effet des valeurs extrêmes. Pour plus d’informations sur l’implémentation et sur la façon de personnaliser l’algorithme, consultez [Références techniques relatives à l’algorithme MLR (Microsoft Logistic Regression)](microsoft-logistic-regression-algorithm-technical-reference.md).  
  
## <a name="data-required-for-logistic-regression-models"></a>Données requises pour les modèles de régression logistique  
 Lorsque vous préparez des données à utiliser pour l'apprentissage d'un modèle de régression logistique, vous devez vous familiariser avec les spécifications liées à l'algorithme, y compris la quantité de données requises et leur mode d'utilisation.  
  
 Les spécifications liées à un modèle de régression logistique sont les suivantes :  
  
 **Colonne à index unique** : chaque modèle doit contenir une colonne numérique ou une colonne de texte qui identifie de façon unique chaque enregistrement. Les clés composées ne sont pas autorisées.  
  
 **Colonnes d'entrée** Chaque modèle doit posséder au moins une colonne d'entrée qui contient les valeurs utilisées comme facteurs dans l’analyse. Vous pouvez avoir autant de colonnes d'entrée que vous le souhaitez. Toutefois, en fonction du nombre de valeurs dans chaque colonne, l'ajout de colonnes supplémentaires peut accroître le temps nécessaire à l'apprentissage du modèle.  
  
 **Au moins une colonne prédictible** Le modèle doit contenir au moins une colonne prédictible de tout type de données, y compris les données numériques continues. Les valeurs de la colonne prédictible peuvent également être traitées en tant qu'entrées du modèle, ou vous pouvez spécifier qu'elle soit utilisée uniquement à des fins de prédiction. Les tables imbriquées ne sont pas prévues pour les colonnes prédictibles, mais elles peuvent être utilisées comme entrées.  
  
 Pour de plus amples informations sur les types de contenu et les types de données pris en charge pour les modèles de régression logistique, consultez la section relative aux spécifications dans [Références techniques relatives à l’algorithme MLR (Microsoft Logistic Regression)](microsoft-logistic-regression-algorithm-technical-reference.md).  
  
## <a name="viewing-a-logistic-regression-model"></a>Affichage d'un modèle de régression logistique  
 Pour explorer le modèle, vous pouvez utiliser la Visionneuse de l'algorithme MNN (Microsoft Neural Network) ou la Visionneuse de l'arborescence de contenu générique Microsoft.  
  
 Lorsque vous affichez le modèle avec la Visionneuse de l'algorithme MNN (Microsoft Neural Network), Analysis Services présente les facteurs qui contribuent à un résultat donné, classés par ordre d’importance. Vous pouvez choisir un attribut et les valeurs à comparer. Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’algorithme MNN (Microsoft Neural Network)](browse-a-model-using-the-microsoft-neural-network-viewer.md).  
  
 Si vous voulez en savoir plus, vous pouvez parcourir les détails du modèle dans la Visionneuse de l'arborescence de contenu générique Microsoft. Le contenu d’un modèle de régression logistique inclut un nœud marginal qui affiche toutes les entrées utilisées pour le modèle, ainsi que les sous-réseaux pour les attributs prédictibles. Pour plus d’informations, consultez [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).  
  
## <a name="creating-predictions"></a>Création de prédictions  
 Après avoir formé le modèle, vous pouvez créer des requêtes sur son contenu pour obtenir les coefficients de régression et d'autres détails, ou vous pouvez utiliser ce modèle pour élaborer des prédictions.  
  
-   Pour obtenir des informations générales sur la façon de créer des requêtes sur un modèle d’exploration de données, consultez [Requêtes d’exploration de données](data-mining-queries.md).  
  
-   Pour obtenir des exemples de requêtes sur un modèle de régression logistique, consultez [Exemples de requêtes de modèle de clustering](clustering-model-query-examples.md).  
  
## <a name="remarks"></a>Notes  
  
-   Ne prend pas en charge l’extraction. Cela est dû au fait que la structure des nœuds du modèle d'exploration de données ne correspond pas nécessairement directement aux données sous-jacentes.  
  
-   Ne prend pas en charge la création de dimensions d’exploration de données.  
  
-   Prend en charge l'utilisation de modèles d'exploration de données OLAP.  
  
-   Ne prend pas en charge l’utilisation du langage PMML (Predictive Model Markup Language) pour créer des modèles d’exploration de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu du modèle d’exploration de données pour les modèles de régression logistique &#40;Analysis Services – Exploration de données&#41;](mining-model-content-for-logistic-regression-models.md)   
 [Références techniques relatives à l’algorithme MLR (Microsoft Logistic Regression)](microsoft-logistic-regression-algorithm-technical-reference.md)   
 [Exemples de requêtes de modèle de régression logistique](logistic-regression-model-query-examples.md)  
  
  
