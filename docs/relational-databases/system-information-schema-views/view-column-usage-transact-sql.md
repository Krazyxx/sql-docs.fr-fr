---
title: VIEW_COLUMN_USAGE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- VIEW_COLUMN_USAGE
- VIEW_COLUMN_USAGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.VIEW_COLUMN_USAGE view
- VIEW_COLUMN_USAGE view
ms.assetid: fc0b3608-a7e8-4532-8215-32235d6670f1
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c666150eea9e6f99cc3c9e555b4aeb5caf45bf96
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54255094"
---
# <a name="viewcolumnusage-transact-sql"></a>VIEW_COLUMN_USAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie une ligne pour chaque colonne de la base de données active qui est utilisée dans la définition d'une vue. Cette vue de schémas d'informations renvoie des informations sur les objets pour lesquels l'utilisateur actuel dispose d'autorisations.  
  
 Pour récupérer des informations à partir de ces vues, spécifiez le nom qualifié complet de **INFORMATION_SCHEMA.** _nom_vue_.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**VIEW_CATALOG**|**nvarchar(** 128 **)**|Qualificateur de la vue.|  
|**VIEW_SCHEMA**|**nvarchar(** 128 **)**|Nom du schéma qui contient la vue.<br /><br /> **&#42;&#42;Important &#42; &#42;**  n’utilisez pas les vues INFORMATION_SCHEMA pour déterminer le schéma d’un objet. La seule méthode fiable pour rechercher le schéma d’un objet est d’interroger l’affichage catalogue sys.objects.|  
|**VIEW_NAME**|**sysname**|Nom de la vue.|  
|**TABLE_CATALOG**|**nvarchar(** 128 **)**|Qualificateur de la table.|  
|**TABLE_SCHEMA**|**nvarchar(** 128 **)**|Nom du schéma qui contient la table.<br /><br /> **&#42;&#42;Important &#42; &#42;**  n’utilisez pas les vues INFORMATION_SCHEMA pour déterminer le schéma d’un objet. La seule méthode fiable pour rechercher le schéma d’un objet est d’interroger l’affichage catalogue sys.objects.|  
|**TABLE_NAME**|**sysname**|Table de base.|  
|**COLUMN_NAME**|**sysname**|Nom de colonne.|  
  
## <a name="see-also"></a>Voir aussi  
 [System Views &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Vues de schémas d’informations &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.sql_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
