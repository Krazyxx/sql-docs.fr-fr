---
title: Sys.dm_xe_database_sessions (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 33ea5179-16bb-4abd-96cc-9bc696e80987
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ba1a198e9550f72f3e6781659f1cba39bd3d5d1f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013510"
---
# <a name="sysdmxedatabasesessions-azure-sql-database"></a>sys.dm_xe_database_sessions (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les événements de la session. Les événements sont des points d'exécution discrets. Des prédicats peuvent être appliqués aux événements pour les empêcher de se déclencher si ces événements ne contiennent pas les informations requises.  
  
||  
|-|  
|**S’applique à** : [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et les versions ultérieures.|  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Adresse mémoire de la session d'événements. N'accepte pas la valeur NULL.|  
|event_name|**nvarchar(60)**|Nom de l'événement auquel est liée une action. N'accepte pas la valeur NULL.|  
|event_package_guid|**uniqueidentifier**|GUID pour le package contenant l'événement. N'accepte pas la valeur NULL.|  
|event_predicate|**nvarchar(2048)**|Représentation XML de l'arborescence prédicat qui est appliquée à l'événement. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalités de la relation  
À compter de 2015-07-13, « sys.dm_xe_objects » est un de ces DMV des événements étendus qui ne contiennent pas « _database » dans leur nom. Pas une faute de frappe ou dans la colonne de droite de la table suivante. Le nom est le même dans Microsoft SQL Server et de la base de données SQL Azure.  
  
|From|Pour|Relation|  
|--------|------|----------------|  
|sys.dm_xe_database_session_events.event_session_address|sys.dm_xe_database_sessions.address|Plusieurs-à-un|  
|sys.dm_xe_database_session_events.event_package_guid, sys.dm_xe_database_session_events.event_name|sys.dm_xe_objects.name, sys.dm_xe_objects.package_guid|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
[Événements étendus dans la base de données SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)  
[Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
 
