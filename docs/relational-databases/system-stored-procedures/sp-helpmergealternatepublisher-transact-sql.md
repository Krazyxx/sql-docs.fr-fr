---
title: sp_helpmergealternatepublisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergealternatepublisher_TSQL
- sp_helpmergealternatepublisher
helpviewer_keywords:
- sp_helpmergealternatepublisher
ms.assetid: a96e365f-5967-4580-9d79-5bacf2d12211
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c00e7c26a429836f0d350e60530d2dc1db8c2a61
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526411"
---
# <a name="sphelpmergealternatepublisher-transact-sql"></a>sp_helpmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une liste de tous les serveurs activés en tant qu'autres serveurs de publication pour les publications de fusion. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpmergealternatepublisher [ @publisher = ] 'publisher', [ @publisher_db = ] 'publisher_db', [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` Est le nom de l’autre serveur de publication. *publisher* est **sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'` Est le nom de la base de données de publication. *publisher_db* est **sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**alternate_publisher**|**sysname**|Nom de l'autre serveur de publication.|  
|**alternate_publisher_db**|**sysname**|Nom de la base de données de publication.|  
|**alternate_publication**|**sysname**|Nom de la publication.|  
|**alternate_distributor**|**sysname**|Nom du serveur de distribution.|  
|**friendly_name**|**nvarchar(255)**|Description de l'autre serveur de publication.|  
|**enabled**|**bit**|Indique si le serveur est un autre serveur de publication. **1** Spécifie que le serveur de publication est activée en tant qu’un autre serveur de publication. **0** Spécifie qu’il n’est pas activé.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpmergealternatepublisher** est utilisé dans la réplication de fusion.  
  
 Pendant chaque session de fusion, le système interroge le serveur de publication et l'Abonné pour obtenir la liste des autres serveurs de publication de chacun d'eux. Le processus de fusion ajoute ou supprime des entrées dans la liste des serveurs de publication de remplacement ; la liste sur le serveur de publication et celle sur l'Abonné sont alors correspondantes à l'issue de l'opération.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la liste d’accès à la publication peuvent exécuter **sp_helpmergealternatepublisher**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
