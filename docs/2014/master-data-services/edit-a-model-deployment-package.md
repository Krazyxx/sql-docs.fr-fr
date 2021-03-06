---
title: Modifier un package de déploiement de modèle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6b0fdb7d-83dd-4392-9011-4ae642c471f1
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 82f3e362643df17d9105ad6987a851211bd22865
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65479499"
---
# <a name="edit-a-model-deployment-package"></a>Modifier un package de déploiement de modèle
  Cette rubrique explique comment déployer les pièces sélectionnées d'un modèle dans MDS, plutôt qu'un modèle entier. Pour ce faire, vous modifiez un package de modèle MDS à l'aide de l'Éditeur de package de modèle.  
  
 L'assistant Éditeur de package de modèle vous permet de sélectionner les entités spécifiques, hiérarchies dérivées, vues d'abonnement et règles d'entreprise d'un modèle que vous souhaitez inclure dans un package MDS, puis déployer ultérieurement. Vous pouvez ignorer les parties du modèle que vous ne souhaitez pas déployer. Lorsque vous sélectionnez une entité, tous les objets dépendants de cette entité sont également automatiquement sélectionnés.  
  
 Vous utilisez l'Éditeur de package de modèle pour sélectionner des parties d'un modèle dans un fichier de package créé par l'outil MDSModelDeploy (qui crée un fichier de package incluant des objets et données) ou l'assistant Déploiement de modèle (qui crée un fichier comprenant uniquement la structure de modèle). Après modification du modèle dans le package, vous utilisez l'outil MDSModelDeploy pour déployer les objets et données, ou l'assistant Déploiement de modèle pour déployer uniquement la structure du modèle.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Pour que vous puissiez le modifier, un package de modèle doit exister. Pour plus d’informations, consultez [Déploiement de modèles &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md) et [Créer un package de déploiement de modèle à l’aide de l’Assistant](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md) ou [Créer un package de déploiement de modèle à l’aide de MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
### <a name="to-edit-a-model-deployment-package"></a>Pour modifier un package de déploiement de modèle  
  
1.  Dans l'Explorateur Windows sur le serveur MDS, accédez à *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.  
  
2.  Exécutez ModelPackageEditor.exe.  
  
3.  Dans l'assistant Éditeur de package de modèle, cliquez sur **Parcourir**, accédez au dossier contenant vos packages, sélectionnez un package, puis cliquez sur **Ouvrir**. Cliquer sur **Suivant**.  
  
4.  Sélectionnez les entités, hiérarchies dérivées, vues d'abonnements ou règles d'entreprise à déployer. Désélectionnez celles que vous ne souhaitez pas déployer. Cliquer sur **Suivant**.  
  
5.  Vérifiez la liste des sélections à déployer. Pour effectuer une modification, cliquez sur **Précédent** et répétez l'étape 4.  
  
6.  Cliquez sur **Parcourir**, accédez au dossier dans lequel vous souhaitez enregistrer le package partiel, puis entrez le nom de fichier du package partiel (avec l’extension .pkg). Cliquez sur **Enregistrer**.  
  
7.  Cliquez sur **Terminer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Déployer un package de déploiement de modèle à l’aide de l’Assistant](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
-   [Déployer un package de déploiement de modèle à l'aide de MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  
