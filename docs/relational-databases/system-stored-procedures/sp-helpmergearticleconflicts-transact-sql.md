---
title: sp_helpmergearticleconflicts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergearticleconflicts
- sp_helpmergearticleconflicts_TSQL
helpviewer_keywords:
- sp_helpmergearticleconflicts
ms.assetid: 4678a2b9-9a5f-4193-a20d-2e11fc896c3a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e02cbdeaaf754819b3a0efa15aa9515cc8515e62
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534031"
---
# <a name="sphelpmergearticleconflicts-transact-sql"></a>sp_helpmergearticleconflicts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie les articles de la publication qui sont en conflit. Cette procédure stockée est exécutée sur la base de données de publication du serveur de publication ou sur la base de données d'abonnement de fusion de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpmergearticleconflicts [ [ @publication = ] 'publication' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publsher_db' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication de fusion. *publication* est **sysname**, avec une valeur par défaut **%**, qui retourne tous les articles dans la base de données qui sont en conflit.  
  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *publisher* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'` Est le nom de la base de données du serveur de publication. *publisher_db* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**article**|**sysname**|Nom de l'article.|  
|**source_owner**|**sysname**|Propriétaire de l'objet source.|  
|**source_object**|**nvarchar(386)**|Nom de l'objet source.|  
|**conflict_table**|**nvarchar(258)**|Nom de la table stockant les conflits d'insertion ou de mise à jour.|  
|**guidcolname**|**sysname**|Nom du RowGuidCol de l'objet source.|  
|**centralized_conflicts**|**Int**|Spécifie si les enregistrements des conflits sont stockés sur le serveur de publication donné.|  
  
 Si l’article a une seule des conflits de suppression et aucun **conflict_table** lignes, le nom de la **conflict_table** dans le résultat de jeu est NULL.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpmergearticleconflicts** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe et le **db_owner** rôle de base de données fixe peuvent exécuter **sp_helpmergearticleconflicts**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
