---
title: Créer des requêtes (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], creating
ms.assetid: 696a080d-848f-44d3-a918-e29bafaab85a
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fb03a941fa462f1b08157859335c94eedf31927d
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65097537"
---
# <a name="create-queries-visual-database-tools"></a>Créer des requêtes (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Les requêtes vous permettent de récupérer des données des tables et vues contenues dans votre base de données. Vous pouvez créer et utiliser des requêtes dans le **Concepteur de requêtes et de vues**, qui se compose de quatre volets : le [volet Schéma](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md), le [volet SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md), le [volet Critères](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)et le [volet Résultats](../../ssms/visual-db-tools/results-pane-visual-database-tools.md).  
  
### <a name="to-create-a-new-query"></a>Pour créer une requête  
  
1.  Dans **l’Explorateur d’objets**, développez le nœud **Tables** de la base de données à interroger. Cliquez avec le bouton droit sur la table à valider, puis cliquez sur **Ouvrir la table**.  
  
2.  Pour ajouter des tables supplémentaires à la requête, dans le menu Concepteur de requêtes, sélectionnez **Ajouter une table**.  
  
    > [!NOTE]  
    > Si les volets **Schéma**, **SQL**, **Critères**ou **Résultats** ne sont pas affichés, pointez sur **Volet** dans le menu Concepteur de requêtes et cliquez sur le volet que vous souhaitez ouvrir.  
  
3.  Dans la boîte de dialogue **Ajouter une table** , sélectionnez les tables que vous souhaitez interroger et cliquez sur **Ajouter** pour chacune d’elles.  
  
4.  Une fois que vous avez ajouté toutes les tables à interroger, cliquez sur **Fermer**.  
  
    Pour ajouter davantage de tables ultérieurement, cliquez avec le bouton droit sur l’espace ouvert dans le volet **Schéma** et cliquez sur **Ajouter une table**dans le menu contextuel.  
  
5.  Dans le **volet Schéma**, cochez les cases situées à côté des objets table de chaque colonne que vous souhaitez interroger.  
  
6.  Dans le menu Concepteur de requêtes, choisissez **Exécuter SQL** pour exécuter votre requête.  
  
Pour affiner davantage votre requête, vous pouvez modifier le code SQL dans le **Volet SQL** ou choisir des options telles que l’ordre de tri et les alias de colonne dans le **Volet Critères**.  
  
## <a name="see-also"></a> Voir aussi  
[Enregistrer des requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/save-queries-visual-database-tools.md)  
[Types de requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/types-of-queries-visual-database-tools.md)  
[Spécifier des critères de recherche &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Résumer les résultats de la requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Effectuer des opérations de base concernant les requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
