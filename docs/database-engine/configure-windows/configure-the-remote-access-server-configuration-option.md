---
title: Configurer l’option de configuration du serveur remote access | Microsoft Docs
ms.custom: ''
ms.date: 08/11/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], stored procedure execution
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 80c8b1690a4a0e38b591fe0614bb13e4ab028e1a
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51605149"
---
# <a name="configure-the-remote-access-server-configuration-option"></a>Configurer l'option de configuration du serveur remote access
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Cette rubrique concerne la fonctionnalité remote access. Cette option de configuration est une fonctionnalité de communication peu intelligible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Elle est dépréciée et son utilisation n’est pas recommandée. Si vous êtes sur cette page en raison de problèmes de connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez plutôt l’une des rubriques suivantes :  
  
-   [Didacticiel : mise en route du moteur de base de données](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)  
  
-   [Connexion à SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)  
  
-   [Se connecter à SQL Server lorsque les administrateurs système n'y ont plus accès](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
-   [Se connecter à un serveur inscrit &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/connect-to-a-registered-server-sql-server-management-studio.md)  
  
-   [Se connecter à n'importe quel composant de SQL Server à partir de SQL Server Management Studio](../../ssms/f1-help/connect-to-any-sql-server-component-from-sql-server-management-studio.md)  
  
-   [Se connecter au moteur de base de données avec sqlcmd](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md)  
  
-   [Comment faire pour résoudre les problème de connexion au moteur de base de données SQL Server](https://social.technet.microsoft.com/wiki/contents/articles/2102.how-to-troubleshoot-connecting-to-the-sql-server-database-engine.aspx)  
  
 Les programmeurs peuvent s’intéresser aux rubriques suivantes :  
  
-   [How To: Connect to SQL Server Using SQL Authentication in ASP.NET 2.0 (Comment : établir une connexion à SQL Server à l’aide de l’authentification SQL dans ASP.NET 2.0)](https://msdn.microsoft.com/library/ff648340.aspx)  
  
-   [Connexion à une instance de SQL Server](../../relational-databases/server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)  
  
-   [Comment : créer des connexions à des bases de données SQL Server](https://msdn.microsoft.com/library/s4yys16a.aspx)  
  
 **Le corps de cette rubrique commence ici.**  
  
 Cette rubrique explique comment configurer l'option de configuration de serveur **remote access** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'option **remote access** contrôle l'exécution des procédures stockées depuis les serveurs locaux ou distants sur lesquels des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont en cours d'exécution. La valeur par défaut de cette option est 1. Cette valeur autorise l'exécution des procédures stockées locales depuis des serveurs distants, ou des procédures stockées distantes depuis le serveur local. Pour empêcher l'exécution des procédures stockées locales depuis un serveur distant ou des procédures stockées distantes depuis le serveur local, attribuez la valeur 0 à cette option.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilisez de préférence [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) .
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option remote access, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option remote access](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   L’option **remote access** ne s’applique qu’aux serveurs ajoutés au moyen de [sp_addserver](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)et n’est incluse que pour des raisons de compatibilité descendante.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-access-option"></a>Pour configurer l'option remote access  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Connexions** .  
  
3.  Sous **Connexions au serveur distant**, activez ou désactivez la case à cocher **Autoriser les accès distants à ce serveur** .  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-remote-access-option"></a>Pour configurer l'option remote access  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour définir l’option `remote access` sur `0`.  
  
```sql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option remote access  
 SQL Server doit être redémarré pour que ce paramètre prenne effet.  
  
## <a name="see-also"></a> Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
