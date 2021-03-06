---
title: Recherche et remplacement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- match case [SQL Server]
- undo operations
- searches [SQL Server Management Studio]
- replacing text
- quick search and replaces [SQL Server Management Studio]
- Query Editor [SQL Server Management Studio], undo
- Query Editor [SQL Server Management Studio], searching
- regular expressions [SQL Server Management Studio]
- finding text [SQL Server Management Studio]
- text [SQL Server], search and replace operations
- finding [SQL Server Management Studio]
- locating text
- Query Editor [SQL Server Management Studio], replacing text
- Find and Replace dialog box
- wildcard options [SQL Server Management Studio]
- match whole word [SQL Server]
- searches [SQL Server Management Studio], replacing
ms.assetid: 3641c7b3-3e3e-4ddd-af82-c15b50004f94
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 299cb79646ff7d0955ca25343fbe2a7d9c0b1140
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63135143"
---
# <a name="search-and-replace"></a>Recherche et remplacement
  Il existe plusieurs méthodes différentes pour rechercher et remplacer du texte. Sur le **modifier** menu, **rechercher et remplacer** propose quatre options : **Recherche rapide**, **remplacement rapide**, **rechercher dans les fichiers**, ou **remplacer dans les fichiers**. Chaque option ouvre une version de la boîte de dialogue **Rechercher et remplacer** . Vous pouvez également effectuer une recherche sans l'aide de l'une de ces boîtes de dialogue. Pour ce faire, il vous suffit d'utiliser les touches de raccourci clavier de la recherche incrémentielle. Ces techniques vous permettent de contrôler la portée de l'opération de recherche et de remplacement et de choisir la méthode de révision des occurrences trouvées et des remplacements.  
  
 Tenez compte des informations suivantes lorsque vous recherchez et remplacez du texte :  
  
-   Les options définies dans la boîte de dialogue **Rechercher et remplacer** affectent toutes les recherches. Ces options comprennent **Respecter la casse**, **Mot entier**, **Rechercher vers le haut**, **Rechercher le texte masqué**, **Caractères génériques**, **Expressions régulières**, **Regarder dans tous les documents ouverts**et **Regarder dans le projet en cours**. Les options ne sont pas toutes disponibles dans toutes les versions de la boîte de dialogue **Rechercher et remplacer** .  
  
-   La commande**Annuler** est disponible uniquement pour les documents qui sont restés ouverts après une opération de remplacement.  
  
-   L’action**Annuler** pour une opération **Remplacer tout** qui s’étend sur plusieurs fichiers est considérée comme une action en bloc sur tous les fichiers affectés. Par conséquent, vous ne pouvez pas annuler des modifications dans certains fichiers et les conserver dans d'autres.  
  
 En règle générale, vous ne pouvez pas rechercher des éléments avec des vues graphiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Effectuer une recherche incrémentielle dans un document actif](search-an-active-document-incrementally.md)   
 [Effectuer une recherche de façon interactive dans des documents](search-documents-interactively.md)   
 [Effectuer une recherche dans des documents à l'aide des listes de résultats](search-documents-using-results-lists.md)   
 [Rechercher du texte avec des caractères génériques](search-text-with-wildcards.md)   
 [Rechercher du texte avec des expressions régulières](search-text-with-regular-expressions.md)  
  
  
