---
title: syscollector_config_store (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syscollector_config_store_TSQL
- syscollector_config_store
dev_langs: TSQL
helpviewer_keywords:
- data collector view
- syscollector_config_store view
ms.assetid: f15f6b05-6808-4b76-b6a8-48dec844cf63
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6811c1ab9fef0f15422f1d51ac9b969476e58699
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="syscollectorconfigstore-transact-sql"></a>syscollector_config_store (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les propriétés qui s'appliquent à l'intégralité du collecteur de données, par opposition à une instance de jeu d'éléments de collection. Chaque ligne de cette vue décrit une propriété du collecteur de données spécifique, telle que le nom de l'entrepôt de données de gestion, et le nom de l'instance où l'entrepôt de données de gestion est situé.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|parameter_name|**nvarchar (128)**|Nom de la propriété. N'accepte pas la valeur NULL.|  
|parameter_value|**sql_variant**|Valeur réelle de la propriété. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation SELECT sur la vue ou l'appartenance dans les rôles de base de données fixes dc_operator, dc_proxy ou dc_admin.  
  
## <a name="remarks"></a>Notes  
 La liste des propriétés disponibles est corrigée et leurs valeurs ne peuvent être modifiées qu'à l'aide de la procédure stockée appropriée. La table suivante décrit les propriétés qui sont exposées par cette vue :  
  
|Nom de la propriété| Description|  
|-------------------|-----------------|  
|CacheDirectory|Nom du répertoire dans le système de fichiers où les packages du type de collecteur stockent les informations temporaires.<br /><br /> NULL = le répertoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] temporaire par défaut est utilisé.|  
|CacheWindow|Indique la stratégie de rétention de données du répertoire de cache pour les téléchargements de données non réussis.<br /><br /> -1 = Conservation des données de tous les échecs de téléchargement.<br /><br /> 0 = Ne pas conserver les données après un échec de téléchargement.<br /><br /> *n*= Conserver les données à partir de  *n*  les échecs de téléchargement précédents, où  *n*  > = 1.<br /><br /> Utilisez la procédure stockée sp_syscollector_set_cache_window pour modifier cette valeur.|  
|CollectorEnabled|Indique l'état du collecteur de données.<br /><br /> 0 = désactivé<br /><br /> 1 = activé<br /><br /> Utilisez la procédure stockée sp_syscollector_enable_collector ou sp_syscollector_disable_collector pour modifier cette valeur.|  
|MDWDatabase|Le nom de l'entrepôt de données de gestion. Utilisez la procédure stockée sp_syscollector_set_warehouse_database_name pour modifier cette valeur.|  
|MDWInstance|Nom de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l'entrepôt de données de gestion. Utilisez la procédure stockée sp_syscollector_set_warehouse_instance_name pour modifier cette valeur.|  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant interroge la vue syscollector_config_store.  
  
```tsql  
SELECT parameter_name, parameter_value  
FROM msdb.dbo.syscollector_config_store;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Vues du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)   
 [sp_syscollector_enable_collector &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql.md)   
 [sp_syscollector_disable_collector &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql.md)   
 [sp_syscollector_set_warehouse_database_name &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-database-name-transact-sql.md)   
 [sp_syscollector_set_warehouse_instance_name &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-instance-name-transact-sql.md)   
 [sp_syscollector_set_cache_window &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql.md)  
  
  