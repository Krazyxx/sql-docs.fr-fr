---
title: sp_help_proxy (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_proxy
- sp_help_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_proxy
ms.assetid: a2fce164-2b64-40c2-8f35-6eeb7844abf1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5e0bbf6e8befa751ee680cd97c2a29ad9f0fe084
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527691"
---
# <a name="sphelpproxy-transact-sql"></a>sp_help_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie les informations d'un ou plusieurs serveurs proxy.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @subsystem_name = ] 'subsystem_name' ,  
    [ @name = ] 'name'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @proxy_id = ] id` Le numéro d’identification du proxy à répertorier des informations. Le *proxy_id* est **int**, avec NULL comme valeur par défaut. Soit le *id* ou *proxy_name* peut être spécifié.  
  
`[ @proxy_name = ] 'proxy_name'` Le nom du proxy à répertorier des informations. Le *proxy_name* est **sysname**, avec NULL comme valeur par défaut. Soit le *id* ou *proxy_name* peut être spécifié.  
  
`[ @subsystem_name = ] 'subsystem_name'` Nom du sous-système pour lequel énumérer les serveurs proxy. Le *subsystem_name* est **sysname**, avec NULL comme valeur par défaut. Lorsque *subsystem_name* est spécifié, *nom* doit également être spécifié.  
  
 Le tableau suivant répertorie les valeurs possibles pour chaque sous-système.  
  
|Value|Description|  
|-----------|-----------------|  
|ActiveScripting|Script ActiveX|  
|CmdExec|Système d'exploitation (CmdExec)|  
|Snapshot|Agent d'instantané de réplication|  
|LogReader|Agent de lecture du journal des réplications|  
|Distribution|Agent de Distribution de réplication|  
|Fusion|Replication Merge Agent|  
|QueueReader|Agent de lecture de la file d'attente de réplication|  
|ANALYSISQUERY|Commandes Analysis Services|  
|ANALYSISCOMMAND|Requête Analysis Services|  
|Dts|Exécution de package SSIS|  
|PowerShell|script PowerShell|  
  
`[ @name = ] 'name'` Le nom d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion pour énumérer les serveurs proxy. Le nom est **nvarchar (256)**, avec NULL comme valeur par défaut. Lorsque *nom* est spécifié, *subsystem_name* doit également être spécifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**Int**|Numéro d'identification du proxy.|  
|**nom**|**sysname**|Nom du proxy.|  
|**credential_identity**|**sysname**|Nom du domaine Microsoft Windows et nom d'utilisateur pour les informations d'identification associées au serveur proxy.|  
|**enabled**|**tinyint**|Indique si ce serveur proxy est activé. { **0** = non activé, **1** = activé}|  
|**description**|**nvarchar(1024)**|Description de ce serveur proxy.|  
|**user_sid**|**varbinary(85)**|Numéro d'identification de sécurité (SID) Windows de l'utilisateur Windows pour ce serveur proxy.|  
|**credential_id**|**Int**|Identifiant des informations d'identification associées à ce serveur proxy.|  
|**credential_identity_exists**|**Int**|Indique si l'identifiant des informations d'identification existe. { 0 = inexistant, 1 = existant }|  
  
## <a name="remarks"></a>Notes  
 Lorsque aucun paramètre n’est fourni, **sp_help_proxy** répertorie des informations pour tous les proxys de l’instance.  
  
 Pour déterminer quels serveurs proxy qu’une connexion peuvent utiliser pour un sous-système donné, spécifiez *nom* et *subsystem_name*. Lorsque ces arguments sont fournis, **sp_help_proxy** répertorie les proxys auxquels la connexion spécifiée peut accéder et qui peuvent être utilisés pour le sous-système spécifié.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer du rôle de base de données fixe **SQLAgentOperatorRole** dans la base de données **msdb** .  
  
 Pour plus d’informations sur **SQLAgentOperatorRole**, consultez [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
> [!NOTE]  
>  Le **credential_identity** et **user_sid** colonnes sont uniquement renvoyées dans le jeu de résultats lorsque les membres de **sysadmin** exécuter cette procédure stockée.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-listing-information-for-all-proxies"></a>A. Affichage des informations pour tous les serveurs proxy  
 L'exemple ci-dessous répertorie les informations pour tous les serveurs proxy de l'instance.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_proxy ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-proxy"></a>B. Affichage des informations pour un serveur proxy spécifique  
 L'exemple ci-dessous répertorie les informations pour le serveur proxy nommé `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_proxy  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)  
  
  
