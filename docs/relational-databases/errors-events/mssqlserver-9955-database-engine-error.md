---
title: MSSQLSERVER_9955 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a7b77ea2e16a65d1fc93bc7199a8006c5e240561
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640097"
---
# <a name="mssqlserver9955"></a>MSSQLSERVER_9955
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9955|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|FTXT2_MSSEARCHACCESSDENY|  
|Texte du message|SQL Server n'a pas pu créer de canal nommé '%ls' pour communiquer avec le démon de filtre de texte intégral (erreur Windows : %d). Il existe déjà un canal nommé pour un processus hôte de démon de filtre, le système manque de ressources ou la recherche de numéro d'identification de sécurité (SID) du groupe de comptes du démon de filtre a échoué. Pour résoudre cette erreur, arrêtez les processus de démon de filtre de texte intégral en cours d'exécution et reconfigurez si nécessaire le compte de service du lanceur de démon de texte intégral.|  
  
## <a name="explanation"></a>Explication  
Ce message s'affiche parce que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas pu créer de canal nommé pour communiquer avec le démon de filtre de texte intégral. Il existe déjà un canal nommé pour un processus hôte de démon de filtre, le système manque de ressources ou la recherche de numéro d'identification de sécurité (SID) du groupe de comptes du démon de filtre a échoué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour résoudre cette erreur, arrêtez les processus de démon de filtre de texte intégral en cours d'exécution et reconfigurez si nécessaire le compte hôte du démon de texte intégral à l'aide du Gestionnaire de configuration SQL Server.  
  
## <a name="see-also"></a> Voir aussi  
[Gestionnaire de configuration SQL Server](~/relational-databases/sql-server-configuration-manager.md)  
[Définir le compte du service du Lanceur de démon de filtre de texte intégral](~/relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)  
[Recherche en texte intégral](~/relational-databases/search/full-text-search.md)  
  
