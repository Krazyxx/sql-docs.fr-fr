---
title: Définir la réponse à une alerte (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], responding to
- responding to alerts
ms.assetid: c86ca6eb-c59f-46e9-bc32-d474e7c3b170
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6ac3e9ee443f0c10a39128fc1d6aab6813ec4f4d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62524069"
---
# <a name="define-the-response-to-an-alert-sql-server-management-studio"></a>Définir la réponse à une alerte (SQL Server Management Studio)
  Cette rubrique explique comment définir la manière dont [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] répond à des alertes de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour définir la réponse à une alerte, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les options du récepteur de radiomessagerie et **net send** seront supprimées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans une version future de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser ces fonctionnalités dans une nouvelle tâche de développement et prévoyez de modifier les applications qui les utilisent actuellement.  
  
-   Remarque : SQL Server Agent doit être configuré pour utiliser la messagerie de base de données pour envoyer des notifications aux opérateurs par messagerie électronique ou radiomessagerie. Pour plus d'informations, consultez [Affecter des alertes à un opérateur](assign-alerts-to-an-operator.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est un outil dont l'interface graphique permet de gérer facilement les travaux. Son utilisation est recommandée pour créer et gérer l'infrastructure des travaux.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent définir la réponse à une alerte.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-define-the-response-to-an-alert"></a>Pour définir la réponse à une alerte  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient l'alerte sur laquelle vous souhaitez définir une réponse.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Alertes** .  
  
4.  Cliquez avec le bouton droit sur l'alerte dont vous voulez définir une réponse, puis sélectionnez **Propriétés**.  
  
5.  Dans la boîte de dialogue _Propriétés de l'alerte_**nom_alerte** , sous **Sélectionner une page**, sélectionnez **Réponse**.  
  
6.  Sélectionnez la case à cocher **Exécuter le travail** , puis dans la liste figurant sous la case à cocher **Exécuter le travail** , sélectionnez un travail à exécuter quand une alerte se produit. Vous pouvez créer un nouveau travail en cliquant sur **Nouveau travail**. Vous pouvez afficher plus d'informations sur le travail en cliquant sur **Afficher le travail**. Pour plus d'informations sur les options disponibles dans les boîtes de dialogue **Nouveau travail** et **Propriétés du travail**_nom_travail_ , consultez [Créer un travail](create-a-job.md) et [Afficher un travail](view-a-job.md).  
  
7.  Activez la case à cocher **Notifier les opérateurs** si vous souhaitez avertir les opérateurs lorsque l'alerte est activée. Dans le **liste d’opérateurs**, sélectionnez un ou plusieurs des méthodes suivantes pour notifier l’ou les opérateurs : **Messagerie**, **radiomessagerie**, ou **Net Send**. Vous pouvez créer un nouvel opérateur en cliquant sur **Nouvel opérateur**. Vous pouvez afficher plus d'informations sur un opérateur en cliquant sur **Afficher l'opérateur**. Pour plus d'informations sur les options disponibles dans les boîtes de dialogue **Nouvel opérateur** et **Afficher les propriétés de l'opérateur** , consultez [Create an Operator](create-an-operator.md) et [View Information About an Operator](view-information-about-an-operator.md).  
  
8.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-define-the-response-to-an-alert"></a>Pour définir la réponse à une alerte  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- adds an e-mail notification for Test Alert.  
    -- assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).  
  
  
