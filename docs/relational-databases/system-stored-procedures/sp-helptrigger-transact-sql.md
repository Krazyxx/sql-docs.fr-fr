---
title: sp_helptrigger (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helptrigger
- sp_helptrigger_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helptrigger
ms.assetid: e486d39b-771d-488d-a786-7136433a2203
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d59f7e05180ce2f0528159d64b0199ae8975464a
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528591"
---
# <a name="sphelptrigger-transact-sql"></a>sp_helptrigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne le ou les types de déclencheurs DML définis sur la table spécifiée de la base de données actuelle. Impossible d’utiliser sp_helptrigger avec des déclencheurs DDL. Requête la [procédures stockées système](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) vue de catalogue à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helptrigger [ @tabname = ] 'table'   
     [ , [ @triggertype = ] 'type' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @tabname = ] 'table'` Est le nom de la table dans la base de données en cours pour lequel retourner des informations sur le déclencheur. *table* est **nvarchar(776)**, sans valeur par défaut.  
  
`[ @triggertype = ] 'type'` Est le type de déclencheur DML pour retourner des informations. *type* est **char (6)**, avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**DELETE**|Renvoie des informations sur le déclencheur DELETE.|  
|**INSERT**|Renvoie des informations sur le déclencheur INSERT.|  
|**UPDATE**|Renvoie des informations sur le déclencheur UPDATE.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 La table ci-dessous décrit les informations figurant dans le jeu de résultats.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**trigger_name**|**sysname**|Nom du déclencheur.|  
|**trigger_owner**|**sysname**|Nom du propriétaire de la table pour laquelle le déclencheur est défini.|  
|**isupdate**|**Int**|1 = déclencheur UPDATE<br /><br /> 0 = n'est pas un déclencheur UPDATE|  
|**isdelete**|**Int**|1 = déclencheur DELETE<br /><br /> 0 = n'est pas un déclencheur DELETE|  
|**isinsert**|**Int**|1 = déclencheur INSERT<br /><br /> 0 = n'est pas un déclencheur INSERT|  
|**isafter**|**Int**|1 = déclencheur AFTER<br /><br /> 0 = n'est pas un déclencheur AFTER|  
|**isinsteadof**|**Int**|1 = déclencheur INSTEAD OF<br /><br /> 0 = n'est pas un déclencheur INSTEAD OF|  
|**trigger_schema**|**sysname**|Nom du schéma auquel le déclencheur appartient.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md) autorisation sur la table.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant exécute `sp_helptrigger` pour produire des informations sur le ou les déclencheurs de la table `Person.Person`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptrigger 'Person.Person';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du moteur de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
