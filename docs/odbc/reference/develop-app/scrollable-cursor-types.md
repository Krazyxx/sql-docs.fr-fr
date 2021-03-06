---
title: Types de curseur de défilement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: dbd32576-0453-4e90-ae45-1a81cee8259d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6290d18ec26fcfa6e2960c3a2c1c408938d9e0e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468576"
---
# <a name="scrollable-cursor-types"></a>Types de curseurs avec défilement
Les quatre types de curseurs avec défilement sont statiques, dynamiques, pilotés par jeu de clés et mixte. Curseurs statiques détectent peu ou aucune modification, mais sont relativement peu coûteuses à implémenter. Les curseurs dynamiques détectent toutes les modifications, mais sont coûteux à implémenter. Les curseurs pilotés par jeu de clés et mixtes se situent entre la détection de la plupart des modifications mais utilisent moins de ressources que les curseurs dynamiques.  
  
 Les termes suivants sont utilisés pour définir les caractéristiques de chaque type de curseur de défilement :  
  
-   **Propres mises à jour, suppressions et insertions.** Mises à jour, suppressions et insertions effectuées via le curseur, soit avec un appel à **SQLBulkOperations** ou **SQLSetPos** ou avec un texte positionné mettre à jour ou supprimer l’instruction.  
  
-   **Autres mises à jour, supprime et insère.** Mises à jour, suppressions et insertions ne pas effectuées par le curseur, y compris celles effectuées par d’autres opérations dans la même transaction, celles effectuées dans les autres transactions et celles effectuées par d’autres applications.  
  
-   **Appartenance.** L’ensemble de lignes du jeu de résultats.  
  
-   **Ordre.** L’ordre dans lequel les lignes sont retournées par le curseur.  
  
-   **valeurs.** Les valeurs dans chaque ligne du jeu de résultats.  
  
 Pour plus d’informations sur la façon de mettre à jour, supprimer et insérer des données, consultez [la mise à jour la vue d’ensemble des données](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Curseurs statiques dans ODBC](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [Curseurs dynamiques dans ODBC](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [Curseurs de jeu de clés](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [Curseurs mixtes](../../../odbc/reference/develop-app/mixed-cursors.md)
