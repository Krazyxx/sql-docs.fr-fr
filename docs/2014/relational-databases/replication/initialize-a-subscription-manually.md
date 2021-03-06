---
title: Initialiser manuellement un abonnement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
ms.assetid: 27a1bc38-e498-4fff-8082-04b52aa4b22c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3bd621890bad3bc42fb2d4d5289d71efcbdbcc2b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62721661"
---
# <a name="initialize-a-subscription-manually"></a>Initialiser manuellement un abonnement
  Cette rubrique explique comment initialiser manuellement un abonnement dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'instantané initial est normalement utilisé pour initialiser un abonnement, mais les abonnements aux publications peuvent être initialisés sans utiliser d'instantané, à condition que le schéma et les données initiales soient déjà présents sur l'Abonné.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   S'il existe une activité sur une base de données publiée à l'aide de la réplication transactionnelle entre le moment où les données et le schéma sont copiés vers l'Abonné et le moment auquel l'abonnement est initialisé manuellement, les modifications résultant de cette activité peuvent ne pas être répliquées vers l'Abonné.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Initialisez manuellement un abonnement à une publication en copiant le schéma (et généralement les données) dans la base de données d'abonnement. Le schéma et les données doivent correspondre à la base de données de publication. Précisez ensuite que l'abonnement ne nécessite pas de schéma et de données dans la page **Initialiser les abonnements** de l'Assistant Nouvel abonnement. Pour plus d'informations sur l'accès à cet Assistant, consultez [Initialiser un abonnement transactionnel sans instantané](initialize-a-transactional-subscription-without-a-snapshot.md) et [Créer un abonnement par extraction de données (pull)](create-a-pull-subscription.md).  
  
 Lors de la première synchronisation de l'abonnement, les objets et les métadonnées dont la réplication a besoin sont copiés dans la base de données d'abonnement.  
  
#### <a name="to-initialize-a-subscription-to-a-publication-manually"></a>Pour initialiser manuellement un abonnement à une publication  
  
1.  Vérifiez que le schéma et les données sont copiés dans la base de données d'abonnement.  
  
2.  Désactivez la case à cocher **Initialiser** dans la page **Initialiser les abonnements** de l'Assistant Nouvel abonnement. Procédez de même pour chaque abonnement nécessitant uniquement la copie des objets et des métadonnées de réplication.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les abonnements peuvent être initialisés manuellement à l'aide des procédures stockées de réplication.  
  
#### <a name="to-manually-initialize-a-pull-subscription-to-a-transactional-publication"></a>Pour initialiser manuellement un abonnement par extraction à une publication transactionnelle  
  
1.  Assurez-vous que le schéma et les données existent dans la base de données d'abonnement. Pour plus d’informations, consultez [Initialiser un abonnement transactionnel sans instantané](initialize-a-transactional-subscription-without-a-snapshot.md).  
  
2.  Au niveau du serveur de publication sur la base de données de publication, exécutez [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Spécifiez **@publication**, **@subscriber**, le nom de la base de données sur l'Abonné contenant les données publiées pour **@destination_db**, la valeur **pull** pour **@subscription_type**et la valeur **replication support only** pour **@sync_type**. Pour plus d’informations, consultez [Créer un abonnement par extraction de données (pull)](create-a-pull-subscription.md).  
  
3.  Sur l'Abonné, exécutez [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql). Pour les abonnements avec mise à jour, consultez [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
4.  Sur l'Abonné, exécutez [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql). Pour plus d’informations, consultez [Créer un abonnement par extraction de données (pull)](create-a-pull-subscription.md).  
  
5.  Démarrez l'Agent de distribution pour transférer des objets de réplication et télécharger les modifications les plus récentes à partir du serveur de publication. Pour plus d’informations, consultez [Synchroniser un abonnement par extraction (pull)](synchronize-a-pull-subscription.md).  
  
#### <a name="to-manually-initialize-a-push-subscription-to-a-transactional-publication"></a>Pour initialiser manuellement un abonnement par émission de données à une publication transactionnelle  
  
1.  Assurez-vous que le schéma et les données existent dans la base de données d'abonnement. Pour plus d’informations, consultez [Initialiser un abonnement transactionnel sans instantané](initialize-a-transactional-subscription-without-a-snapshot.md).  
  
2.  Au niveau du serveur de publication sur la base de données de publication, exécutez [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Spécifiez le nom de la base de données sur l'Abonné contenant les données publiées pour **@destination_db**, la valeur **push** pour **@subscription_type**et la valeur **replication support only** pour **@sync_type**. Pour les abonnements avec mise à jour, consultez [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](publish/create-an-updatable-subscription-to-a-transactional-publication.md).  
  
3.  Au niveau du serveur de publication sur la base de données de publication, exécutez [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql). Pour plus d’informations, consultez [Créer un abonnement par émission (push)](create-a-push-subscription.md).  
  
4.  Démarrez l'Agent de distribution pour transférer des objets de réplication et télécharger les modifications les plus récentes à partir du serveur de publication. Pour plus d’informations, consultez [Synchroniser un abonnement par émission (push)](synchronize-a-push-subscription.md).  
  
#### <a name="to-manually-initialize-a-pull-subscription-to-a-merge-publication"></a>Pour initialiser manuellement un abonnement par extraction à une publication de fusion  
  
1.  Assurez-vous que le schéma et les données existent dans la base de données d'abonnement. Pour cela, vous pouvez restaurer une sauvegarde de la base de données de publication sur l'Abonné.  
  
2.  Sur le serveur de publication, exécutez [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql). Spécifiez **@publication**, **@subscriber**, **@subscriber_db**et la valeur **pull** pour **@subscription_type**. L'abonnement par extraction est inscrit.  
  
3.  Exécutez [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)sur l'Abonné, sur la base de données contenant les données publiées. Spécifiez la valeur **none** pour **@sync_type**.  
  
4.  Sur l'Abonné, exécutez [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql). Pour plus d’informations, consultez [Créer un abonnement par extraction de données (pull)](create-a-pull-subscription.md).  
  
5.  Démarrez l'Agent de fusion pour transférer des objets de réplication et télécharger les modifications les plus récentes à partir du serveur de publication. Pour plus d’informations, consultez [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).  
  
#### <a name="to-manually-initialize-a-push-subscription-to-a-merge-publication"></a>Pour initialiser manuellement un abonnement par émission de données à une publication de fusion  
  
1.  Assurez-vous que le schéma et les données existent dans la base de données d'abonnement. Pour cela, vous pouvez restaurer une sauvegarde de la base de données de publication sur l'Abonné.  
  
2.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql). Spécifiez le nom de la base de données sur l'Abonné contenant les données publiées pour **@subscriber_db**, la valeur **push** pour **@subscription_type**et la valeur **none** pour **@sync_type**.  
  
3.  Sur la base de données de publication du serveur de publication, exécutez [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql). Pour plus d’informations, consultez [Créer un abonnement par émission (push)](create-a-push-subscription.md).  
  
4.  Démarrez l'Agent de fusion pour transférer des objets de réplication et télécharger les modifications les plus récentes à partir du serveur de publication. Pour plus d’informations, consultez [Synchroniser un abonnement par émission (push)](synchronize-a-push-subscription.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Initialiser un abonnement transactionnel sans instantané](initialize-a-transactional-subscription-without-a-snapshot.md)   
 [Sauvegarder et restaurer des bases de données répliquées](administration/back-up-and-restore-replicated-databases.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)  
  
  
