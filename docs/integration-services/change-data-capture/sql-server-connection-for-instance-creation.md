---
title: Connexion SQL Server pour la création d’une instance | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7053b119e899e5f17043d3db64d09a18733eae0e
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58273845"
---
# <a name="sql-server-connection-for-instance-creation"></a>Connexion SQL Server pour la création d'une instance
  Une des premières étapes de la création d'une instance Oracle CDC est la création d'une base de données CDC sur l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible. Cette base de données CDC est activée pour SQL Server CDC et cette activation requiert une connexion membre du rôle serveur fixe `sysadmin` .  
  
 Quand un utilisateur qui démarre l’Assistant **Création d’une instance Oracle CDC** n’est pas membre du rôle serveur fixe `sysadmin` , la boîte de dialogue **Connexion à SQL Server** s’ouvre et vous invite à entrer les informations d’identification pour un membre du rôle `sysadmin` de façon à effectuer la tâche Activer la base de données pour SQL Server CDC. Lorsque la base de données CDC est créée, la connexion `sysadmin` est ignorée et la tâche reprend avec la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'origine utilisée lorsque la console du concepteur Oracle a été ouverte.  
  
## <a name="task-list"></a>Liste des tâches  
 Dans la boîte de dialogue **Connexion à SQL Server** , entrez les informations suivantes :  
  
 **Nom de serveur**  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Authentification**  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows**  
  
-   **Authentification SQL Server** : si vous sélectionnez cette option, vous devez taper **l’Identifiant** et le **Mot de passe** de l’utilisateur dans l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous vous connectez.  
  
 La connexion doit avoir un rôle de base de données qui permet l'accès à la base de données MSXCDCDB. Il est recommandé que la connexion ait également accès à toutes les bases de données supplémentaires qui sont utilisées, sinon l'utilisateur ne pourra pas afficher les données de ces bases de données.  
  
 **Options**  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
-   **Délai de connexion** : Tapez le délai (en secondes) pendant lequel le service de capture de données modifiées pour Oracle attend une connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant expiration. La valeur par défaut est **15**.  
  
-   **Délai d’exécution** : Tapez le délai (en secondes) pendant lequel le service Windows de capture de données modifiées Oracle attend l'exécution d'une commande avant expiration. La valeur par défaut est **30**.  
  
-   **Chiffrer la connexion** : sélectionnez **Chiffrer la connexion** pour utiliser une connexion chiffrée dans la communication entre Oracle CDC Service et l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible.  
  
-   **Avancé** : Cliquez sur **Avancé** et tapez toutes les propriétés de connexion supplémentaires dans la boîte de dialogue Propriétés avancées de connexion, si nécessaire.  
  
     Pour plus d’informations sur la boîte de dialogue Propriétés avancées de connexion, consultez [Propriétés avancées de connexion](../../integration-services/change-data-capture/advanced-connection-properties.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Créer la base de données de modification SQL Server](../../integration-services/change-data-capture/create-the-sql-server-change-database.md)   
 [Autorisations de connexion SQL Server requises pour le concepteur CDC](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
