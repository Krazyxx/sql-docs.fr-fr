---
title: MSmerge_partition_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_partition_groups_TSQL
- MSmerge_partition_groups
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_partition_groups system table
ms.assetid: 5d56d780-ee40-4afc-9c2a-d1723d86e430
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cb8c77ba54e25c574d5f751febe8bdac3ba1dfbf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911248"
---
# <a name="msmergepartitiongroups-transact-sql"></a>MSmerge_partition_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_partition_groups** table stocke une ligne pour chaque partition précalculée dans une base de données. Outre les colonnes répertoriées, une colonne est ajoutée à cette table pour chaque fonction utilisée dans un filtre de lignes paramétrable. Par exemple, une colonne nommée **HOST_NAME_FN** est ajouté à la table si un filtre utilise le [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) (fonction). Une ligne est stockée pour chaque jeu unique de valeurs de fonction synchronisées avec ce serveur de publication. Deux ou plusieurs abonnés qui synchronisent avec exactement la même valeur pour toutes ces fonctions partageront la même ligne dans cette table et par conséquent partagent tous le même id de partition. Cette table est stockée dans la base de données de publication.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**Int**|Colonne d'identité fournissant un numéro d'identification unique pour la partition précalculée.|  
|**publication_number**|**smallint**|Le numéro de publication, qui est stocké dans **sysmergepublications**.|  
|**maxgen_whenadded**|**bigint**|Génération la plus élevée connue sur le serveur de publication au moment de l'insertion de la ligne dans cette table.|  
|**using_partition_groups**|**bit**|Indique si la partition appartient à une publication qui utilise des partitions précalculées. Peut être l'une des valeurs suivantes :<br /><br /> **0** = publication n’utilise pas les partitions précalculées.<br /><br /> **1** = la publication utilise des partitions précalculées<br /><br /> Pour plus d’informations, consultez [Optimiser les performances des filtres paramétrés avec des partitions précalculées](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).|  
|**HOST_NAME_FN**|**nvarchar(128)**|Valeur fournie lors de l'utilisation du filtre de lignes paramétrable en vue de générer des partitions. Pour plus d'informations, voir [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
