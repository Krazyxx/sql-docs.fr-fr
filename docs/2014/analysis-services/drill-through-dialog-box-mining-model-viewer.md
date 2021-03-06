---
title: Extraction de la boîte de dialogue (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.drillthrough.f1
ms.assetid: 42b78399-143d-4f44-90e0-b545ffb79e10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d26fcb3d26570adafe340f190e7a91c82fd2ef3a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62731548"
---
# <a name="drill-through-dialog-box-mining-model-viewer"></a>Boîte de dialogue Extraire (Visionneuse de modèle d'exploration de données)
  Quand vous affichez un modèle d’exploration de données sous l’onglet **Visionneuse de modèle d’exploration de données** du concepteur de modèle d’exploration de données, vous pouvez extraire les détails des données de cas, à condition que l’extraction ait été activée sur le modèle. De plus, si l'extraction a été activée sur la structure d'exploration de données sous-jacente, vous pouvez aussi afficher les colonnes dans la structure d'exploration de données, même si ces colonnes n'ont pas été incluses dans le modèle d'exploration de données. Dans la liste de colonnes, les colonnes de structure portent un préfixe par l’étiquette « Structure. ».  
  
> [!NOTE]  
>  Vous ne pouvez pas activer l'extraction sur une structure d'exploration de données existante. Au lieu de cela, vous devez recréer la structure d'exploration de données et activer l'extraction au cours du processus de création.  
  
 Pour plus d’informations sur l’accès aux données de cas à partir de chacune des visionneuses de modèles d’exploration de données qui prennent en charge l’extraction, **consultez** [Extraire des données de cas à partir d’un modèle d’exploration de données](data-mining/drill-through-to-case-data-from-a-mining-model.md).  
  
## <a name="options"></a>Options  
 **Cas classés dans**  
 Affiche la définition de la règle, le jeu d'éléments et le cluster qui sont contenus dans le nœud sélectionné.  
  
 **Liste des colonnes**  
 Affiche les colonnes dans le modèle, suivies des colonnes de structure.  
  
 **Remarque** Les colonnes de structure sont affichées uniquement si l’extraction est activée sur la structure d’exploration de données et si vous avez sélectionné l’option **Colonnes de structure et de modèle**. De plus, vous devez posséder des autorisations d'extraction à la fois sur le modèle d'exploration de données et sur la structure d'exploration de données pour afficher les colonnes.  
  
 Colonnes de structure qui ne sont pas incluses dans le modèle apparaissent sous la forme **Structure.\< nom de colonne >**.  
  
> [!NOTE]  
>  Vous pouvez cliquer avec le bouton droit n’importe où dans la grille de colonnes et sélectionner **Copier tout** pour copier les données d’extraction, au format séparé par des tabulations, dans le Presse-papiers. Les données copiées comprennent uniquement les données de cas, et non la définition du nœud.  
  
 **Play**  
 Cliquez sur le bouton fléché vert pour actualiser les données.  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes d’extraction &#40;exploration de données&#41;](data-mining/drillthrough-queries-data-mining.md)   
 [Visionneuses de modèles d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Tâches et procédures de la visionneuse de modèle d’exploration de données](data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
