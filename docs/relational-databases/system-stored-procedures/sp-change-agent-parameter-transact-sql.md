---
title: sp_change_agent_parameter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_change_agent_parameter_TSQL
- sp_change_agent_parameter
helpviewer_keywords:
- sp_change_agent_parameter
ms.assetid: f1fbecc7-e64f-405c-8067-6b38c1f3c0a0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 16de7ceaae80a2aebcf2ed40d2b06b9a6ccf0dc4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997033"
---
# <a name="spchangeagentparameter-transact-sql"></a>sp_change_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifications d’un paramètre d’un profil d’agent de réplication stocké dans le [MSagent_parameters](../../relational-databases/system-tables/msagent-parameters-transact-sql.md) (table système). Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de distribution sur lequel l'agent est en cours d'exécution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_change_agent_parameter [ @profile_id= ] profile_id, [ @parameter_name= ] 'parameter_name', [ @parameter_value= ] 'parameter_value'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @profile_id = ] profile_id,` Est l’ID du profil. *profile_id* est **int**, sans valeur par défaut.  
  
`[ @parameter_name = ] 'parameter_name'` Est le nom du paramètre. *parameter_name* est **sysname**, sans valeur par défaut. Pour les profils système, les paramètres modifiables dépendent du type d'Agent. Pour savoir de quel type d’agent *profile_id* représente, localisez le *profile_id* colonne dans le **Msagent_profiles** table et notez le *agent_type*  valeur.  
  
> [!NOTE]  
>  Si un paramètre est pris en charge pour une donnée *agent_type*, mais n’a ne pas été défini dans le profil d’agent, une erreur est retournée. Pour ajouter un paramètre à un profil d’agent que vous devez exécuter [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
 Pour un Agent d’instantané (*agent_type*=**1**), s’il est défini dans le profil, les propriétés suivantes peuvent être modifiées :  
  
-   **70Subscribers**  
  
-   **BcpBatchSize**  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxNetworkOptimization**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **QueryTimeout**  
  
-   **StartQueueTimeout**  
  
-   **UsePerArticleContentsView**  
  
 Pour un Agent de lecture du journal (*agent_type*=**2**), s’il est défini dans le profil, les propriétés suivantes peuvent être modifiées :  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **MessageInterval**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ReadBatchSize**  
  
-   **ReadBatchThreshold**  
  
 Pour un Agent de Distribution (*agent_type*=**3**), s’il est défini dans le profil, les propriétés suivantes peuvent être modifiées :  
  
-   **BcpBatchSize**  
  
-   **CommitBatchSize**  
  
-   **CommitBatchThreshold**  
  
-   **FileTransferType**  
  
-   **HistoryVerboseLevel**  
  
-   **KeepAliveMessageInterval**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDeliveredTransactions**  
  
-   **MessageInterval**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **QuotedIdentifier**  
  
-   **SkipErrors**  
  
-   **TransactionsPerHistory**  
  
 Pour un Agent de fusion (*agent_type*=**4**), s’il est défini dans le profil, les propriétés suivantes peuvent être modifiées :  
  
-   **AltSnapshotFolder**  
  
-   **BcpBatchSize**  
  
-   **ChangesPerHistory**  
  
-   **DestThreads**  
  
-   **DownloadGenerationsPerBatch**  
  
-   **DownloadReadChangesPerBatch**  
  
-   **DownloadWriteChangesPerBatch**  
  
-   **DynamicSnapshotLocation**  
  
-   **ExchangeType**  
  
-   **FastRowCount**  
  
-   **FileTransferType**  
  
-   **GenerationChangeThreshold**  
  
-   **HistoryVerboseLevel**  
  
-   **InputMessageFile**  
  
-   **InteractiveResolution**  
  
-   **InterruptOnMessagePattern**  
  
-   **KeepAliveMessageInterval**  
  
-   **LoginTimeout**  
  
-   **MaxBcpThreads**  
  
-   **MaxDownloadChanges**  
  
-   **MaxUploadChanges**  
  
-   **MetadataRetentionCleanup**  
  
-   **NumDeadlockRetries**  
  
-   **Output**  
  
-   **OutputMessageFile**  
  
-   **OutputVerboseLevel**  
  
-   **PacketSize**  
  
-   **ParallelUploadDownload**  
  
-   **PauseOnMessagePattern**  
  
-   **PauseTime**  
  
-   **PollingInterval**  
  
-   **ProcessMessagesAtPublisher**  
  
-   **ProcessMessagesAtSubscriber**  
  
-   **QueryTimeout**  
  
-   **QueueSizeMultiplier**  
  
-   **SrcThreads**  
  
-   **StartQueueTimeout**  
  
-   **SyncToAlternate**  
  
-   **UploadGenerationsPerBatch**  
  
-   **UploadReadChangesPerBatch**  
  
-   **UploadWriteChangesPerBatch**  
  
-   **UseInprocLoader**  
  
-   **Valider**  
  
-   **ValidateInterval**  
  
 Pour un Agent de lecture de file d’attente (*agent_type*=**9**), s’il est défini dans le profil, les propriétés suivantes peuvent être modifiées :  
  
-   **HistoryVerboseLevel**  
  
-   **LoginTimeout**  
  
-   **Output**  
  
-   **OutputVerboseLevel**  
  
-   **PollingInterval**  
  
-   **QueryTimeout**  
  
-   **ResolverState**  
  
-   **SQLQueueMode**  
  
 Pour voir quels paramètres ont été définies pour un profil donné, exécutez **sp_help_agent_profile** et notez le *profile_name* associé à la *profile_id*. Avec le bon *profile_id*, prochaine exécution **sp_help_agent_parameters** à l’aide qui *profile_id* pour afficher les paramètres associés au profil. Paramètres peuvent être ajoutés à un profil en exécutant [sp_add_agent_parameter](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md).  
  
`[ @parameter_value = ] 'parameter_value'` Est la nouvelle valeur du paramètre. *parameter_value* est **nvarchar (255)**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_change_agent_parameter** est utilisée dans tous les types de réplication.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_change_agent_parameter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Profils de l’Agent de réplication](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agent de lecture du journal de réplication](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agent de fusion de réplication](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agent de lecture de la file d'attente de réplication](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
