---
title: sp_help_jobserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobserver
- sp_help_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobserver
ms.assetid: 57971787-f9f5-4199-9f64-c2b61a308906
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ba2120b4c48ac9df9cc901b4ee789d95f9fc0357
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533291"
---
# <a name="sphelpjobserver-transact-sql"></a>sp_help_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur le serveur pour un travail donné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_jobserver  
     { [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name' }  
     [ , [ @show_last_run_details = ] show_last_run_details ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_id = ] job_id` Numéro d’identification pour lequel retourner les informations. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
`[ @job_name = ] 'job_name'` Le nom du travail pour lequel retourner les informations. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
`[ @show_last_run_details = ] show_last_run_details` Est que les informations de dernière exécution font partie du jeu de résultats. *afficher_les_détails_de_dernière_exécution* est **tinyint**, avec une valeur par défaut **0**. **0** n’inclut pas les informations de la dernière exécution, et **1** est.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**Int**|Numéro d'identification du serveur cible.|  
|**server_name**|**nvarchar(30)**|Nom de l'ordinateur du serveur cible.|  
|**enlist_date**|**datetime**|Date d'inscription du serveur cible sur le serveur maître.|  
|**last_poll_date**|**datetime**|Date à laquelle le serveur cible a interrogé pour la dernière fois le serveur maître.|  
  
 Si **sp_help_jobserver** est exécutée avec *afficher_les_détails_de_dernière_exécution* définie sur **1**, le jeu de résultats comporte ces colonnes supplémentaires.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**last_run_date**|**Int**|Date du début de la dernière exécution du travail sur ce serveur cible.|  
|**last_run_time**|**Int**|Heure du début de la dernière exécution du travail sur ce serveur.|  
|**last_run_duration**|**Int**|Durée du travail lors de sa dernière exécution sur ce serveur cible (en secondes).|  
|**last_outcome_message**|**nvarchar(1024)**|Décrit le dernier résultat du travail.|  
|**last_run_outcome**|**Int**|Résultat du travail à l'issue de sa dernière exécution sur ce serveur.<br /><br /> **0** = Échec<br /><br /> **1** = a réussi<br /><br /> **3** = annulée<br /><br /> **5** = inconnu|  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Membres de **SQLAgentUserRole** peuvent uniquement afficher les informations sur les travaux dont ils sont propriétaires.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renvoie des informations, dont les informations sur la dernière exécution, du travail `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobserver  
    @job_name = N'NightlyBackups',  
    @show_last_run_details = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
