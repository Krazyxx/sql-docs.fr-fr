---
title: Configurer des points de contrôle pour redémarrer un Package ayant échoué | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 220440313f0a06efb4ad55156a41fee18c61ab62
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834417"
---
# <a name="configure-checkpoints-for-restarting-a-failed-package"></a>Configurer des points de contrôle pour redémarrer un package ayant échoué
  Vous pouvez configurer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] de sorte qu'ils redémarrent à partir d'un point d'arrêt au lieu de réexécuter l'ensemble du package. Pour ce faire, vous devez définir les propriétés des points de contrôle.  
  
### <a name="to-configure-a-package-to-restart"></a>Pour configurer le redémarrage d'un package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package à configurer.  
  
2.  Dans **l’Explorateur de solutions**, double-cliquez sur le package pour l’ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Cliquez avec le bouton droit n’importe où dans l’arrière-plan de la surface de dessin du flux de contrôle, puis cliquez sur **Propriétés**.  
  
5.  Définissez la propriété SaveCheckpoints sur `True`.  
  
6.  Tapez le nom du fichier point de contrôle dans la propriété CheckpointFileName.  
  
7.  Définissez la propriété CheckpointUsage sur l’une des deux valeurs suivantes :  
  
    -   Sélectionnez `Always` pour toujours redémarrer le package à partir du point d'arrêt.  
  
        > [!IMPORTANT]  
        >  Une erreur se produit si le fichier de point d'arrêt n'est pas disponible.  
  
    -   Sélectionnez `IfExists` pour redémarrer le package uniquement si le fichier de point d'arrêt est disponible.  
  
8.  Configurez les tâches et les conteneurs à partir desquels le package peut redémarrer.  
  
    -   Cliquez avec le bouton droit sur une tâche ou un conteneur, puis cliquez sur **Propriétés**.  
  
    -   Affectez à la propriété FailPackageOnFailure `True` pour chaque tâche et conteneur sélectionnés.  
  
## <a name="see-also"></a>Voir aussi  
 [Redémarrer des packages à l'aide de points de contrôle](packages/restart-packages-by-using-checkpoints.md)  
  
  
