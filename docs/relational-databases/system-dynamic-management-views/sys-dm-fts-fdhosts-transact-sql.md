---
title: sys.dm_fts_fdhosts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_fdhosts
- dm_fts_fdhosts_TSQL
- sys.dm_fts_fdhosts
- sys.dm_fts_fdhosts_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_fdhosts dynamic management view
- troubleshooting [SQL Server], full-text search
ms.assetid: d42a6334-4362-4361-83da-f8324fe55ec7
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: faa79f48a4f3b8ac70984c3b02c8863d7d37e8ac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026718"
---
# <a name="sysdmftsfdhosts-transact-sql"></a>sys.dm_fts_fdhosts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur l'activité actuelle de l'hôte ou des hôtes de démon de filtre sur l'instance de serveur.  
  
 
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**fdhost_id**|**Int**|ID de l'hôte de démon de filtre.|  
|**fdhost_name**|**nvarchar(120)**|Nom de l'hôte de démon de filtre.|  
|**fdhost_process_id**|**Int**|ID de processus Windows de l'hôte de démon de filtre.|  
|**fdhost_type**|**nvarchar(120)**|Type de document traité par l'hôte de démon de filtre, l'un des types suivants :<br /><br /> Thread unique<br /><br /> Multithread<br /><br /> Document énorme|  
|**max_thread**|**Int**|Nombre maximal de threads dans l'hôte de démon de filtre.|  
|**batch_count**|**Int**|Nombre des lots traités dans l'hôte de démon de filtre.|  
  
## <a name="permissions"></a>Autorisations  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   

## <a name="examples"></a>Exemples  
 L'exemple suivant retourne le nom de l'hôte de démon de filtre et le nombre maximal de threads dans cet hôte. Il contrôle également le nombre de lots traités actuellement dans le démon de filtre. Ces informations peuvent être utilisées pour diagnostiquer les performances.  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche en texte intégral et les fonctions et vues de gestion dynamique de la recherche sémantique &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Recherche en texte intégral](../../relational-databases/search/full-text-search.md)  
  
  
