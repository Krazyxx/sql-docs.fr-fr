---
title: Contrôle de code source
titleSuffix: Azure Data Studio
description: Découvrez comment configurer le contrôle de code source dans Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 7adcae568e97d4bbecd5f901a76dc465dad53ba7
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089723"
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>Utilisation du contrôle de code source dans[!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] prend en charge de Git pour le contrôle de version/source.


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Prise en charge de Git dans[!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] est fourni avec un gestionnaire de contrôle de source de Git (SCM), mais vous devez toujours [installer Git (version 2.0.0 ou version ultérieure)](https://git-scm.com/download) avant que ces fonctionnalités sont disponibles. 



## <a name="open-an-existing-git-repository"></a>Ouvrir un dépôt Git existant

1. Sous le menu **Fichier** , sélectionnez **Ouvrir un dossier...**
2. Accédez au dossier qui contient vos fichiers suivis par Git, puis cliquez sur **Sélectionner le dossier**.  Vous pouvez sélectionner ici les sous-dossiers de votre dépôt local.


## <a name="initialize-a-new-git-repository"></a>Initialiser un nouveau dépôt Git

1. Sélectionnez **Contrôle de code source**, puis sélectionnez l’icône Git.

   ![Icône du contrôle de code source Git](media/source-control/source-control.png)

1. Entrez le chemin du dossier que vous voulez initialiser comme dépôt Git, puis appuyez sur **Entrée**.

   ![initialiser le référentiel Git](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Utilisation des référentiels Git

[!INCLUDE[name-sos](../includes/name-sos-short.md)]hérite son implémentation Git de Visual Studio Code, mais ne prend pas actuellement en charge d'autres fournisseurs SCM. Pour plus d’informations sur l’utilisation de Git après avoir ouvert ou initialisé un dépôt, consultez [prise en charge de Git dans VS Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).


## <a name="additional-resources"></a>Ressources supplémentaires
- [Documentation de Git](https://git-scm.com/documentation)
