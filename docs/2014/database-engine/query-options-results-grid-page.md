---
title: Options de requête (Page de grille) de résultats | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.grid.f1
ms.assetid: 764bf435-3aab-4c62-b4e0-64fe020a5a95
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: a0351173100703b8b78f7b4b019fcd2c63688918
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843688"
---
# <a name="query-options-results-grid-page"></a>Options de requête – Résultats (page Grille)
  Cette page vous permet de spécifier les options d'affichage du jeu de résultats d'une requête au format grille.  
  
## <a name="options"></a>Options  
 **Inclure la requête dans l'ensemble de résultats**  
 Retourne le texte de la requête dans l'ensemble de résultats.  
  
 **Inclure des en-têtes de colonne lors de la copie ou de l'enregistrement de résultats**  
 Permet d'inclure les en-têtes (titres) des colonnes lorsque les résultats sont copiés dans le Presse-papiers ou enregistrés dans un fichier. Désactivez cette case à cocher si vous voulez que les résultats copiés ou enregistrés contiennent seulement les données, sans les en-têtes des colonnes.  
  
 **Ignorer les résultats après l'exécution**  
 Permet de libérer de la mémoire en ignorant les résultats de la requête une fois qu'ils ont été affichés à l'écran.  
  
 **Afficher les résultats dans un onglet séparé**  
 Permet d'afficher l'ensemble de résultats dans une nouvelle fenêtre de document et non pas en bas de la fenêtre de requête de document.  
  
 **Basculer vers l'onglet des résultats après l'exécution de la requête**  
 Affiche automatiquement l'ensemble de résultats à l'écran.  
  
 **Nombre maximal de caractères récupérés**  
 **Données non-XML :**  
  
 Entrez un nombre compris entre 1 et 65 535 pour indiquer le nombre maximal de caractères affichés dans chaque cellule.  
  
> [!NOTE]  
>  Si vous précisez un nombre trop élevé, les données de l'ensemble de résultats risquent d'être tronquées à l'affichage. Le nombre maximal de caractères affichés dans chaque cellule dépend de la taille de police. Si les ensembles de résultats retournés sont volumineux, il est préférable de ne pas spécifier une valeur trop élevée sans quoi vous risquez d'être confronté à une mémoire insuffisante pour l'exécution de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou à une dégradation des performances système.  
  
 **Données XML :**  
  
 Sélectionnez **1 Mo**, **2 Mo**ou **5 Mo**. Sélectionnez **Illimité** pour récupérer tous les caractères.  
  
 **Rétablir les valeurs par défaut**  
 Rétablit toutes les valeurs par défaut initiales des options de cette page.  
  
  
