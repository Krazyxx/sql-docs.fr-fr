---
title: Supprimer des jointures (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6e1de076e5882be92a1ed3b9f2d16eac7c5e062f
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65098207"
---
# <a name="remove-joins-visual-database-tools"></a>Supprimer des jointures (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Si vous ne souhaitez pas que les tables soient liées par une jointure interne ou externe, vous pouvez supprimer celle-ci. Vous pouvez par exemple supprimer une jointure créée automatiquement entre deux tables par le [Concepteur de requêtes et de vues](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) .  
  
> [!NOTE]  
> La suppression d'une jointure n'a aucune répercussion sur la relation sous-jacente existant dans la base de données.  
  
Si deux tables jointes font partie de votre requête et que vous supprimez toutes les conditions de jointure entre elles, la requête obtenue devient le produit des deux tables, en d’autres termes une instruction CROSS JOIN.  
  
### <a name="to-remove-a-join"></a>Pour supprimer une jointure  
  
-   Dans le [volet Schéma](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md), sélectionnez la ligne de jointure à supprimer, puis appuyez sur la touche Suppr. Il est possible de sélectionner et supprimer plusieurs lignes de jointure à la fois.  
  
Le Concepteur de requêtes et de vues supprime la ligne de jointure et modifie l’instruction dans le [volet SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a> Voir aussi  
[Joindre automatiquement des tables &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)  
[Joindre manuellement des tables &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md)  
[Interroger avec des jointures &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
