---
title: Base de données tempdb - Parallel Data Warehouse | Microsoft Docs
description: Base de données tempdb dans Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7e11f4eff980358f4b4906f8a100cfc509d19dd5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156961"
---
# <a name="tempdb-database-in-parallel-data-warehouse"></a>base de données tempdb dans Parallel Data Warehouse
**tempdb** est une base de données système SQL Server PDW stocke les tables temporaires locales pour les bases de données utilisateur. Tables temporaires sont souvent utilisés pour améliorer les performances de requête. Par exemple, vous pouvez utiliser une table temporaire d’organiser un script et réutiliser des données calculées.  
  
Pour plus d’informations sur les bases de données système, consultez [bases de données système](system-databases.md).  
  
## <a name="Basics"></a>Termes et concepts clés  
*table temporaire locale*  
Un *table temporaire locale* utilise le préfixe # avant le nom de table et est une table temporaire créée par une session d’utilisateur local. Chaque session peut accéder uniquement aux données dans les tables temporaires locales pour sa propre session.  
  
Chaque session peut afficher les métadonnées pour les tables temporaires locales dans toutes les sessions. Par exemple, toutes les sessions peuvent afficher les métadonnées pour toutes les tables temporaires locales avec le `SELECT * FROM tempdb.sys.tables` requête.  
  
table temporaire globale  
*Les tables temporaires globales*, pris en charge dans SQL Server avec le ## syntaxe, ne sont pas pris en charge dans cette version de SQL Server PDW.  
  
pdwtempdb  
**pdwtempdb** est la base de données qui stocke les tables temporaires locales.  
  
PDW n’implémente pas de tables temporaires à l’aide de SQL Server**tempdb** base de données. Au lieu de cela, PDW les stocke dans une base de données appelée pdwtempdb. Cette base de données existe sur chaque nœud de calcul et est invisible pour l’utilisateur via les interfaces PDW. Dans la Console d’administration, dans la page de stockage, vous verrez ces soit comptabilisée pour dans une base de données du système PDW appelé **tempdb sql**.  
  
tempdb  
**tempdb** est la base de données tempdb SQL Server. Il utilise une journalisation minimale. SQL Server utilise tempdb sur les nœuds de calcul pour stocker des tables temporaires dont il a besoin au cours de l’exécution d’opérations de SQL Server.  
  
SQL Server PDW supprime des tables à partir de **tempdb** lorsque :  
  
-   L’instruction DROP TABLE est exécutée.  
  
-   Une session est déconnectée. Uniquement les tables temporaires pour la session sont supprimées.  
  
-   L’appliance est arrêtée.  
  
-   Le nœud de contrôle a un basculement de cluster.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
SQL Server PDW effectue les mêmes opérations sur les tables temporaires et tables permanentes, sauf spécification contraire. Par exemple, les données dans des tables temporaires locales, comme des tables permanentes, sont distribuées ou répliquées entre les nœuds de calcul.  
  
## <a name="LimitationsRestrictions"></a>Limitations et restrictions  
Limitations et restrictions sur l’ordinateur SQL Server PDW**tempdb** base de données. Vous *ne peut pas :*  
  
-   Créer une table temporaire globale qui commence par ##.  
  
-   Effectuer une sauvegarde ou restauration de **tempdb**.  
  
-   Modifier les autorisations pour **tempdb** avec la **GRANT**, **DENY**, ou **RÉVOQUER** instructions.  
  
-   Exécutez **DBCC SHRINKLOG** pour **tempdb**tempdb.  
  
-   Effectuer des opérations DDL sur **tempdb**. Il existe deux exceptions à cela. Pour plus d’informations, consultez la liste suivante des limitations et restrictions sur les tables temporaires locales.  
  
Limitations et restrictions sur les tables temporaires locales. Vous *ne peut pas :*  
  
-   Renommer une table temporaire  
  
-   Créer des partitions, des vues ou des index non cluster sur une table temporaire. **ALTER INDEX** peut être utilisé pour reconstruire un index cluster pour une table créée à l’aide.  
  
-   Modifier les autorisations pour les tables temporaires avec GRANT, DENY, ou de refuser des instructions.  
  
-   Exécutez les commandes de console de base de données sur des tables temporaires.  
  
-   Utiliser le même nom pour les deux ou plusieurs tables temporaires dans le même lot. Si plusieurs tables temporaires locales sont utilisées dans un traitement, chacune doit avoir un nom unique. Si plusieurs sessions exécutent le même lot et création de la même table temporaire locale, SQL Server PDW ajoute en interne un suffixe numérique au nom de table temporaire locale pour maintenir un nom unique pour chaque table temporaire locale.  
  
> [!NOTE]  
> Vous *pouvez* créer et mettre à jour des statistiques sur une table temporaire. **ALTER INDEX** peut être utilisée pour reconstruire un index cluster.  
  
## <a name="permissions"></a>Autorisations  
Tous les utilisateurs peuvent créer des objets temporaires dans tempdb. Les utilisateurs n'ont accès qu'aux objets qu'ils possèdent, sauf s'ils ont reçu des autorisations supplémentaires. Il est possible de révoquer l’autorisation de connexion à tempdb pour empêcher un utilisateur d’utiliser tempdb. Cependant, cela n’est pas recommandé, car certaines opérations courantes nécessitent l’utilisation de tempdb.  
  
## <a name="RelatedTasks"></a>Tâches associées  
  
|Tâches|Description|  
|---------|---------------|  
|Créer une table dans **tempdb**.|Vous pouvez créer une table temporaire de l’utilisateur avec les instructions CREATE TABLE et CREATE TABLE AS SELECT. Pour plus d’informations, consultez [CREATE TABLE](../t-sql/statements/create-table-azure-sql-data-warehouse.md) et [CREATE TABLE AS SELECT](../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md).|  
|Afficher la liste des tables existantes dans **tempdb**.|`SELECT * FROM tempdb.sys.tables;`|  
|Afficher la liste des colonnes existantes dans **tempdb**.|`SELECT * FROM tempdb.sys.columns;`|  
|Afficher la liste des objets existants dans **tempdb**.|`SELECT * FROM tempdb.sys.objects;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
