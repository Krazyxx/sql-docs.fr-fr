---
title: Créer des relations entre les Tables d’un schéma (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- diagrams [SQL Server], designing
ms.assetid: 28e9630c-dff4-46cc-bb0e-fe77998b6ac2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab36ebfefbfd3d8cee8e6da7caadf86eb4a10032
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184280"
---
# <a name="create-relationships-between-tables-on-a-diagram-visual-database-tools"></a>Créer des relations entre des tables sur un diagramme (Visual Database Tools)
  Vous pouvez créer des relations entre des colonnes dans différentes tables dans le Concepteur de diagrammes en faisant glisser les colonnes entre les tables.  
  
### <a name="to-create-a-relationship-graphically"></a>Pour créer une relation sous forme de graphique  
  
1.  Dans le Concepteur de diagrammes, cliquez sur le sélectionneur de ligne d'une ou de plusieurs colonnes de base de données que vous souhaitez associer à une colonne dans une autre table.  
  
2.  Faites glisser la ou les colonne(s) sélectionnée(s) vers la table associée.  
  
3.  Deux boîtes de dialogue apparaissent : **Relation de clé étrangère** et **Tables et colonnes**, cette dernière apparaissant au premier plan.  
  
4.  Le**nom de relation** a une nom fourni par le système au format FK_*localtable*_*foreigntable*. Vous pouvez modifier cette valeur.  
  
5.  Vérifiez que la **table de clé primaire** spécifie la bonne table.  
  
6.  La grille affiche les colonnes locales et leurs colonnes étrangères correspondantes. Vous pouvez ajouter ou supprimer des colonnes de table ou modifier les mappages.  
  
7.  Choisissez **OK**.  
  
     La boîte de dialogue **Relation de clé étrangère** s’ouvre. La**Relation sélectionnée** affiche la relation créée.  
  
8.  Modifiez les propriétés de la relation dans la grille.  
  
9. Choisissez **OK** pour créer la relation.  
  
     Le Concepteur de base de données affiche une relation entre les colonnes que vous avez choisies.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et la boîte de dialogue colonnes &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Contraintes uniques et les contraintes Check](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Utiliser des tables dans les schémas de base de données &#40;Visual Database Tools&#41;](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
