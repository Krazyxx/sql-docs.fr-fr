---
title: sys.registered_search_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.registered_search_properties
- registered_search_properties
- sys.registered_search_properties_TSQL
- registered_search_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search properties [SQL Server]
- property searching [SQL Server], viewing registered properties
- search property lists [SQL Server], viewing registered properties
- sys.registered_search_properties catalog view
ms.assetid: 1b9a7a5c-8c05-4819-83c3-7487dd08fcf7
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fb85c0b4804a3b8b775b80649ed3d449eb307589
ms.sourcegitcommit: 04c031f7411aa33e2174be11dfced7feca8fbcda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64946521"
---
# <a name="sysregisteredsearchproperties-transact-sql"></a>sys.registered_search_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contient une ligne pour chaque propriété de recherche contenue par une liste de propriétés de recherche sur la base de données actuelle.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**property_list_id**|**Int**|ID de la liste de propriétés de recherche à laquelle cette propriété appartient.|  
|**property_set_guid**|**uniqueidentifier**|L'identificateur global unique GUID qui identifie le jeu de propriétés auquel appartient la propriété de recherche.|  
|**property_int_id**|**Int**|L'entier qui identifie cette propriété de recherche dans le jeu de propriétés. **property_int_id** est unique dans le jeu de propriétés.|  
|**property_name**|**nvarchar(64)**|Nom qui identifie cette propriété de recherche de manière unique dans la liste de propriétés de recherche.<br /><br /> Remarque : Pour effectuer une recherche sur une propriété, spécifiez ce nom de propriété dans le [CONTAINS](../../t-sql/queries/contains-transact-sql.md) prédicat.|  
|**property_description**|**nvarchar(512)**|Description de la propriété.|  
|**property_id**|**Int**|ID de propriété interne de la propriété de recherche dans la liste de propriétés de recherche identifiée par le **property_list_id** valeur.<br /><br /> Lorsqu'une propriété donnée est ajoutée à une liste de propriétés de recherche donnée, le moteur d'indexation et de recherche en texte intégral inscrit la propriété et lui affecte un ID de propriété interne qui est spécifique à cette liste de propriétés. L'ID de propriété interne, qui est un entier, est unique à une liste de propriétés de recherche donnée. Si une propriété donnée est enregistrée pour plusieurs listes de propriétés de recherche, un ID de propriété interne différent peut être affecté pour chaque liste de propriétés de recherche.<br /><br /> Remarque : L’ID de propriété interne est différent de l’identificateur entier de propriété qui est spécifié lors de l’ajout de la propriété à la liste de propriétés de recherche. Pour plus d’informations, consultez [Rechercher les propriétés du document à l’aide des listes de propriétés de recherche](../../relational-databases/search/search-document-properties-with-search-property-lists.md).<br /><br /> Pour afficher le contenu tout lié à la propriété dans l’index de recherche en texte intégral : <br />                  [sys.dm_fts_index_keywords_by_property &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les listes de propriétés de recherche, consultez [Rechercher les propriétés du document à l’aide des listes de propriétés de recherche](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="permissions"></a>Autorisations  
 La visibilité des métadonnées pour les propriétés de recherche est limitée à celles qui figurent dans les listes de propriétés de recherche que vous détenez ou pour lesquelles une autorisation REFERENCE vous a été accordée.  
  
> [!NOTE]  
>  Le propriétaire d'une liste de propriétés de recherche peut accorder des autorisations REFERENCE ou CONTROL dans la liste. Les utilisateurs disposant de l'autorisation CONTROL peuvent également accorder l'autorisation REFERENCE à d'autres utilisateurs.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant répertorie toutes les métadonnées pour les propriétés de recherche inscrites.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.registered_search_properties;   
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [Rechercher les propriétés du document à l’aide des listes des propriétés de recherche](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
