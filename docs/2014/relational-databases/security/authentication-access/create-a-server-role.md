---
title: Créer un rôle serveur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverrole.members.f1
- SQL12.SWB.SERVERROLE.GENERAL.F1
- sql12.swb.serverrole.memberships.f1
helpviewer_keywords:
- SERVER ROLE, creating
ms.assetid: 74f19992-8082-4ed7-92a1-04fe676ee82d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 22e08b5eb0bccc02303201b7fae46b55f1012fd8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63011961"
---
# <a name="create-a-server-role"></a>Créer un rôle serveur
  Cette rubrique explique comment créer un rôle de serveur dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer un nouveau rôle serveur, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 L'autorisation sur les éléments sécurisables au niveau de la base de données ne peut pas être accordée aux rôles de serveur. Pour créer des rôles de base de données, consultez [CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
  
-   Requiert l’autorisation CREATE SERVER ROLE ou l’appartenance au rôle serveur fixe sysadmin.  
  
-   Requiert également IMPERSONATE sur *server_principal* pour les connexions, l’autorisation ALTER pour les rôles serveur utilisés comme *server_principal*ou l’appartenance à un groupe Windows utilisé comme server_principal.  
  
-   Lorsque vous utilisez l'option AUTHORIZATION pour affecter la propriété de rôle de serveur, les autorisations suivantes sont également requises :  
  
    -   Pour affecter la propriété d'un rôle de serveur à un autre compte de connexion, l'autorisation IMPERSONATE est requise pour ce compte.  
  
    -   Pour affecter la propriété d'un rôle de serveur à un autre rôle de serveur, l'appartenance au rôle de serveur destinataire ou l'autorisation ALTER est requise sur ce rôle.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-new-server-role"></a>Pour créer un rôle serveur  
  
1.  Dans l'Explorateur d'objets, développez le serveur sur lequel vous souhaitez créer le rôle serveur.  
  
2.  Développez le dossier **Sécurité** .  
  
3.  Cliquez avec le bouton droit sur le dossier **Rôles de serveur**, puis sélectionnez **Nouveau rôle de serveur...**.  
  
4.  Dans le **nouveau rôle de serveur -**_nom_rôle_serveur_ boîte de dialogue le **général** page, entrez un nom pour le nouveau rôle de serveur dans le **nom du rôle serveur**boîte.  
  
5.  Dans la zone **Propriétaire** , entrez le nom du principal de serveur qui détiendra le nouveau rôle. Vous pouvez également cliquer sur les points de suspension **(…)** pour ouvrir la boîte de dialogue **Sélectionner la connexion au serveur ou le rôle de serveur**.  
  
6.  Sous **Éléments sécurisables**, sélectionnez un ou plusieurs éléments sécurisables au niveau du serveur. Lorsqu'un élément sécurisable est sélectionné, ce rôle de serveur peut se voir accorder ou refuser des autorisations sur cet élément sécurisable.  
  
7.  Dans le **autorisations : Explicite** , sélectionnez la case à cocher pour accorder, droit d’accorder ou refuser l’autorisation à ce rôle de serveur pour les éléments sécurisables sélectionnés. Si une autorisation ne peut pas être accordée ou refusée à tous les éléments sécurisables sélectionnés, l'autorisation est représentée sous forme de sélection partielle.  
  
8.  Dans la page **Membres** , utilisez le bouton **Ajouter** pour ajouter des connexions qui représentent des individus ou des groupes au nouveau rôle serveur.  
  
9. Un rôle du serveur défini par l'utilisateur peut être membre d'un autre rôle du serveur. Dans la page **Appartenances** , cochez une case pour rendre le rôle serveur défini par l’utilisateur actuel membre d’un rôle serveur sélectionné.  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-new-server-role"></a>Pour créer un rôle serveur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    --Creates the server role auditors that is owned the securityadmin fixed server role.  
    USE master;  
    CREATE SERVER ROLE auditors AUTHORIZATION securityadmin;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql).  
  
  
