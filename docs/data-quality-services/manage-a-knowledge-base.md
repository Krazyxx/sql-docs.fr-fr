---
title: Gérer une base de connaissances | Microsoft Docs
ms.custom: ''
ms.date: 06/04/2013
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 9cfa9f3770c0a9ce5b5ac6ae176a33f92d9b79c9
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488300"
---
# <a name="manage-a-knowledge-base"></a>Gérer une base de connaissances

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Cette rubrique décrit comment remplir les fonctions de gestion sur une base de connaissances dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Vous pouvez supprimer une base de connaissances, la déverrouiller, ignorer vos modifications, la renommer et afficher ses propriétés.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
 Pour gérer une base de connaissances, la base de connaissances doit avoir été déjà créée, et publiée (si une autre personne l'a créée) ou fermée (si vous l'avez créée).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_kb_editor ou dqs_administrator sur la base de données DQS_MAIN pour ouvrir une base de connaissances.  
  
##  <a name="Manage"></a> Gérer une base de connaissances  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Exécutez l’application Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Ouvrir une base de connaissances**.  
  
3.  Cliquez avec le bouton droit sur une base de connaissances dans la table des bases de connaissances.  
  
4.  Dans le menu contextuel, vous pouvez effectuer les tâches suivantes :  
  
    1.  **Ouvrir** : cliquez pour ouvrir la base de connaissances dans l’activité sélectionnée dans le volet **Sélectionner une activité**.  
  
    2.  **Déverrouiller** : Vous pouvez déverrouiller la base de connaissances si vous êtes l’utilisateur qui travaillait sur la base de connaissances dans une des opérations de gestion de domaine, découverte des connaissances et l’activité de stratégie de correspondance et l’avait fermée. Si vous déchargez la base de connaissances, une autre personne peut l'ouvrir et travailler dessus. Cette commande n'est pas disponible si la base de connaissances n'est pas dans un état d'une activité. Pour plus d'informations, consultez [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    3.  **Ignorer le travail** : Cliquez sur la base de connaissances est dans un état de travail, comme illustré avec une entrée dans le champ d’état dans la table. Cette commande n'est pas disponible si la base de connaissances n'est pas dans un état d'une activité ou si la base de connaissances est verrouillée. Pour plus d'informations, consultez [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
    4.  **Renommer** : Cliquez pour modifier le champ de la Base de connaissances de la table de la base de connaissances que vous avez cliqué sur. Modifiez le nom, puis cliquez sur cette base de connaissances et sur une autre dans le champ pour accepter le changement de nom.  
  
    5.  **Supprimer** : Cliquez pour supprimer la base de connaissances à partir de la base de données DQS_MAIN sur [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
    6.  **Propriétés** : Cliquez pour afficher les propriétés de la base de données dans un affichage en lecture seule.  
  
        1.  **Base de connaissances source**: base de connaissances sur laquelle cette base de données était fondée. Ce paramètre est facultatif.  
  
        2.  **État** : indique si la base de connaissances est **En cours** et si elle est dans une activité spécifique de gestion des connaissances, comme déterminé lors de la dernière fermeture. L'état peut être **En cours**, à savoir que la base de connaissances est ouverte dans une session de gestion des connaissances, mais pas dans une activité spécifique, ou **En cours** plus une activité de gestion des connaissances, dans laquelle la base de connaissances est ouverte dans une session de gestion des connaissances, et dans une activité spécifique.  
  
        3.  **Est verrouillé** : **True** si la base de connaissances a été verrouillée, **False** dans le cas contraire  
  
        4.  **Contenu non publié** : True si la base de connaissances contient un contenu qui le n'a pas été enregistré par publication, False dans le cas contraire  
  
        5.  **Verrouillé par**: nom de l'utilisateur qui a fermé la base de connaissances et l'a verrouillée  
  
        6.  **Verrouillé le**: date du verrouillage  
  
        7.  **Créé par**: nom de l'utilisateur qui a créé la base de connaissances, avec le réseau auquel il appartient  
  
        8.  **Date de création**: date lors de la création  
  
##  <a name="FollowUp"></a> Suivi : Après la gestion d’une Base de connaissances  
 Après que vous avez géré une base de connaissances, l'étape suivante varie selon l'action effectuée sur la base de connaissances :  
  
-   Si vous avez ouvert la base de connaissances, vous continuerez dans l'activité que vous avez sélectionnée.  
  
-   Si vous l'avez déverrouillée, elle est disponible pour qu'une autre personne l'ouvre et travaille dessus, dans l'état indiqué.  
  
-   Si vous aviez ignoré le travail sur la base de connaissances, celle-ci sera disponible dans son dernier état publié.  
  
-   Si vous l'avez renommée, vous devez ouvrir la base de connaissances renommée pour travailler dessus.  
  
-   Si vous la supprimez, vous devrez sélectionner une autre base de connaissances sur laquelle travailler ou en créez une nouvelle.  
  
  
