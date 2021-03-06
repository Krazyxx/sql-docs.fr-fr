---
title: Associer des conditions avec priorité à l’opérateur AND (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], combining
- precedence [SQL Server], Criteria pane
- search criteria [SQL Server], combining conditions
- combining search conditions
- AND, Criteria pane
ms.assetid: 450eb2eb-6ea3-405b-8dd2-1ff926c016e7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4d0a0bcb7115255c3c6b3750cd930e7d06b9e2df
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225813"
---
# <a name="combine-conditions-when-and-has-precedence-visual-database-tools"></a>Associer des conditions avec priorité à l'opérateur AND (Visual Database Tools)
  Pour associer des conditions avec AND, vous ajoutez deux fois la colonne à la requête, une fois pour chaque condition. Pour associer des conditions à l’aide de l’opérateur OR, vous indiquez la première condition dans la colonne Filtre et les autres conditions dans une colonne **Ou...** .  
  
 Imaginez que vous souhaitiez, par exemple, rechercher des employés travaillant dans la société depuis plus de cinq ans à des postes de faible niveau ou des employés occupant des postes de moyen niveau quelle que soit leur date d'embauche. Cette requête nécessite trois conditions, deux d'entre elles étant reliées à l'aide de l'opérateur AND :  
  
-   Employés dont la date d'embauche remonte à plus de cinq ans ET dont le niveau de poste s'élève à 100.  
  
     -ou-  
  
-   Employés dont le niveau de poste s'élève à 200.  
  
### <a name="to-combine-conditions-when-and-has-precedence"></a>Pour associer des conditions avec priorité à l'opérateur AND  
  
1.  Dans le [volet Critères](visual-database-tools.md), ajoutez les colonnes de données dans lesquelles vous souhaitez effectuer la recherche. Si vous souhaitez effectuer la recherche dans une même colonne à l'aide de deux conditions (voire plus) reliées à l'aide de l'opérateur AND, vous devez ajouter le nom de cette colonne de données à la grille pour chacune des valeurs que vous souhaitez rechercher.  
  
2.  Dans la colonne **Filtre** , entrez toutes les conditions que vous souhaitez relier à l’aide de l’opérateur AND. Par exemple, pour relier à l'aide de l'opérateur AND des conditions effectuant une recherche dans les colonnes `hire_date` et `job_lvl` , entrez respectivement les valeurs `< '1/1/91'` et `= 100`dans la colonne Filtre.  
  
     Les entrées effectuées dans la grille donnent lieu à la clause WHERE suivante dans l’instruction figurant dans le [volet SQL](sql-pane-visual-database-tools.md):  
  
    ```  
    WHERE (hire_date < '01/01/91') AND  
      (job_lvl = 100)  
    ```  
  
3.  Dans la colonne de la grille **Ou...** , entrez les conditions que vous souhaitez relier à l’aide de l’opérateur OR. Pour ajouter, par exemple, une condition recherchant une autre valeur dans la colonne `job_lvl` , entrez dans la colonne **Ou...** une valeur supplémentaire telle que `= 200`.  
  
     Quand vous ajoutez une valeur à la colonne **Ou...** , une autre condition vient s’ajouter à la clause WHERE dans l’instruction figurant dans le volet SQL :  
  
    ```  
    WHERE (hire_date < '01/01/91' ) AND  
      (job_lvl = 100) OR   
      (job_lvl = 200)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Associer des Conditions OR a une priorité &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md)   
 [Conventions pour la combinaison de Conditions de recherche dans le volet Critères &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)   
 [Valeurs de recherche de règles pour l’entrée &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Spécifier des critères de recherche &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
