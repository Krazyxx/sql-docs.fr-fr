---
title: À propos de l’accès de la connexion client aux réplicas de disponibilité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], readable secondary replicas
- active secondary replicas [SQL Server], read-only access to
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], client connectivity
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 29027e46-43e4-4b45-b650-c4cdeacdf552
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 13a863603353ee47639cd327c8c5eebd6df8e12a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789841"
---
# <a name="about-client-connection-access-to-availability-replicas-sql-server"></a>À propos de l'accès de la connexion client aux réplicas de disponibilité (SQL Server)
  Dans un groupe de disponibilité AlwaysOn, vous pouvez configurez un ou plusieurs réplicas de disponibilité pour autoriser les connexions en lecture seule lors d'une exécution sous le rôle secondaire (autrement dit, avec une exécution en tant que réplica secondaire). Vous pouvez également configurer chaque réplica de disponibilité afin d'autoriser ou exclure les connexions en lecture seule lors d'une exécution sous le rôle principal (autrement dit, avec une exécution comme réplica principal).  
  
 Pour faciliter l'accès client aux bases de données primaires ou secondaires d'un groupe de disponibilité donné, vous devez définir un écouteur de groupe de disponibilité. Par défaut, l'écouteur de groupe de disponibilité dirige les connexions entrantes vers le réplica principal. Toutefois, vous pouvez configurer un groupe de disponibilité pour prendre en charge le routage en lecture seule, qui permet à son écouteur de groupe de disponibilité de rediriger les demandes de connexion des applications avec intention de lecture vers un réplica secondaire accessible en lecture. Pour plus d’informations, consultez [Configurer le routage en lecture seule pour un groupe de disponibilité &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md).  
  
 Lors d'un basculement, un réplica secondaire adopte le rôle principal et l'ancien réplica principal joue le rôle secondaire. Pendant le processus de basculement, toutes les connexions clientes au réplica principal et aux réplicas secondaires prennent fin. Après le basculement, lorsqu'un client se reconnecte à l'écouteur de groupe de disponibilité, l'écouteur reconnecte le client au nouveau réplica principal, sauf dans le cas d'une demande de connexion avec intention de lecture. Si le routage en lecture seule est configuré sur le client et sur les instances de serveur qui hébergent le nouveau réplica principal et sur au moins un réplica secondaire accessible en lecture, les demandes de connexion avec intention de lecture sont à nouveau routées vers un réplica secondaire qui prend en charge le type d'accès à la connexion dont le client a besoin. Pour garantir une expérience naturelle pour le client après un basculement, il est important de configurer l'accès à la connexion pour les rôles secondaires et principaux de chaque réplica de disponibilité.  
  
> [!NOTE]  
>  Pour plus d’informations sur l’écouteur de groupe de disponibilité, qui traite les demandes de connexion des clients, consultez [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).  
  
 **Dans cette rubrique :**  
  
-   [Types d'accès à la connexion pris en charge par le rôle secondaire](#ConnectAccessForSecondary)  
  
-   [Types d'accès à la connexion pris en charge par le rôle principal](#ConnectAccessForPrimary)  
  
-   [Comment la configuration d'accès à la connexion affecte la connectivité client](#HowConnectionAccessAffectsConnectivity)  
  
-   [Tâches associées](#RelatedTasks)  
  
-   [Contenu connexe](#RelatedContent)  
  
##  <a name="ConnectAccessForSecondary"></a> Types d'accès à la connexion pris en charge par le rôle secondaire  
 Le rôle secondaire prend en charge trois méthodes pour les connexions clientes, comme suit :  
  
 Aucune connexion  
 Aucune connexion utilisateur n'est autorisée. Les bases de données secondaires ne sont pas disponibles pour l'accès en lecture. Il s'agit du comportement par défaut dans le rôle secondaire.  
  
 Connexions d'intention en lecture seule  
 Les bases de données secondaire sont disponibles uniquement pour la connexion pour laquelle le `Application Intent` a la valeur de propriété de connexion `ReadOnly` (*les connexions en lecture*).  
  
 Pour plus d'informations sur cette propriété, consultez [Prise en charge des fonctionnalités de récupération d'urgence, haute disponibilité par SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
 Autoriser toute connexion en lecture seule  
 La ou les bases de données secondaires sont toutes disponibles pour les connexions d'accès en lecture. Cette option permet aux clients disposant d'une version antérieure de se connecter.  
  
 Pour plus d’informations, consultez [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
##  <a name="ConnectAccessForPrimary"></a> Types d'accès à la connexion pris en charge par le rôle principal  
 Le rôle principal prend en charge deux méthodes pour les connexions clientes, comme suit :  
  
 Toutes les connexions sont autorisées  
 Les connexions en lecture-écriture et en lecture seule sont autorisées aux bases de données primaires. Il s'agit du comportement par défaut pour le rôle principal.  
  
 Autoriser uniquement les connexions en lecture-écriture  
 Lorsque le `Application Intent` a la valeur de propriété de connexion **ReadWrite** ou n’est pas définie, la connexion est autorisée. Les connexions pour lesquelles le `Application Intent` mot clé de chaîne de connexion est définie sur `ReadOnly` ne sont pas autorisés. L'autorisation des seules connexions en lecture-écriture peut empêcher vos clients de connecter une charge de travail avec intention de lecture au réplica principal, par erreur.  
  
 Pour plus d'informations sur cette propriété de connexion, consultez [Utilisation de mots clés de chaîne de connexion avec SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
 Pour plus d’informations, consultez [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
##  <a name="HowConnectionAccessAffectsConnectivity"></a> Comment la configuration d'accès à la connexion affecte la connectivité client  
 Les paramètres d'accès à la connexion d'un réplica déterminent si une tentative de connexion échoue ou réussit. Le tableau suivant récapitule si une tentative de connexion donnée réussit ou échoue pour chaque paramètre d'accès à la connexion.  
  
|Rôle de réplica|Accès à la connexion pris en charge sur le réplica|Intention de connexion|Résultat de la tentative de connexion|  
|------------------|--------------------------------------------|-----------------------|--------------------------------|  
|Secondary|All|Intention de lecture, lecture-écriture, ou aucune intention de connexion spécifiée|Opération réussie|  
|Secondary|Aucun (il s'agit du comportement secondaire par défaut.)|Intention de lecture, lecture-écriture, ou aucune intention de connexion spécifiée|Failure|  
|Secondary|Intention de lecture uniquement|Intention de lecture|Opération réussie|  
|Secondary|Intention de lecture uniquement|Lecture-écriture ou aucune intention de connexion spécifiée|Failure|  
|Principale|Tous (il s'agit du comportement principal par défaut.)|Lecture seule, lecture-écriture ou aucune intention de connexion spécifiée|Opération réussie|  
|Principale|Lecture-écriture|Intention de lecture uniquement|Failure|  
|Principale|Lecture-écriture|Lecture-écriture ou aucune intention de connexion spécifiée|Opération réussie|  
  
 Pour plus d’informations sur la configuration d’un groupe de disponibilité pour accepter les connexions clientes à ses réplicas, consultez [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).  
  
### <a name="example-connection-access-configuration"></a>Exemple de configuration d'accès à la connexion  
 Selon la façon dont différents réplicas de disponibilité sont configurés pour l'accès à la connexion, la prise en charge des connexions clientes peut changer après le basculement d'un groupe de disponibilité. Par exemple, considérez un groupe de disponibilité pour lequel la création de rapports est exécutée sur des réplicas secondaires distants avec validation asynchrone. Toutes les applications en lecture seule des bases de données dans ce groupe de disponibilité définissent leur propriété de connexion `Application Intent` avec la valeur `ReadOnly`, de sorte que toutes les connexions en lecture seule soient des connexions avec intention de lecture.  
  
 Cet exemple de groupe de disponibilité compte deux réplicas de validation synchrone au centre de calcul principal et deux réplicas de validation asynchrone sur un site satellite. Pour le rôle principal, tous les réplicas sont configurés pour l'accès en lecture-écriture, ce qui empêche les connexions avec intention de lecture au réplica principal dans tous les cas. Le rôle secondaire avec validation synchrone utilise la configuration par défaut d'accès à la connexion (« aucun »), ce qui empêche toute connexion cliente sous le rôle secondaire.  Par opposition, les réplicas avec validation asynchrone sont configurés pour autoriser les connexions avec intention de lecture sous le rôle secondaire. Le tableau suivant récapitule cette configuration d'exemple :  
  
|Réplica|Mode de validation|Rôle initial|Accès à la connexion pour le rôle secondaire|Accès à la connexion pour le rôle principal|  
|-------------|-----------------|------------------|------------------------------------------|----------------------------------------|  
|Replica1|Synchrone|Principale|None|Lecture-écriture|  
|Replica2|Synchrone|Secondary|None|Lecture-écriture|  
|Replica3|Asynchrone|Secondary|Intention de lecture uniquement|Lecture-écriture|  
|Replica4|Asynchrone|Secondary|Intention de lecture uniquement|Lecture-écriture|  
  
 En général, dans ce scénario d'exemple, les basculements se produisent uniquement entre les réplicas avec validation synchrone, et immédiatement après le basculement, les applications avec intention de lecture peuvent se reconnecter à l'un des réplicas secondaires avec validation asynchrone. Toutefois, lorsqu'un incident se produit au centre de calcul principal, les deux réplicas avec validation synchrone sont perdus. L'administrateur de base de données sur le site satellite répond en effectuant un basculement manuel forcé vers un réplica secondaire avec validation asynchrone. Les bases de données secondaires sur le réplica secondaire restant sont interrompues par le basculement forcé, ce qui les rend indisponibles pour les charges de travail en lecture seule. Le nouveau réplica principal, qui est configuré pour les connexions en lecture-écriture, empêche la charge de travail avec intention de lecture de concurrencer la charge de travail en lecture-écriture. Cela signifie que tant que l'administrateur de base de données n'a pas repris les bases de données secondaires sur le réplica secondaire restant avec validation asynchrone, les clients avec intention de lecture ne peuvent se connecter à aucun réplica de disponibilité.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Configurer le routage en lecture seule pour un groupe de disponibilité &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Surveiller des groupes de disponibilité &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)  
  
-   [Afficher les propriétés d’un réplica de disponibilité &#40;SQL Server&#41;](view-availability-replica-properties-sql-server.md)  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   [Guide de Solutions Microsoft SQL Server AlwaysOn pour une haute disponibilité et récupération d’urgence](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [Blog de l’équipe AlwaysOn SQL Server : Blog officiel de SQL Server AlwaysOn Team](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Statistiques](../../../relational-databases/statistics/statistics.md)  
  
  
