---
title: Présentation des différences entre l’exécution locale et l’exécution distante | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8b0379003ace2c693ab6c6734bc9dd4331872406
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290795"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a>Présentation des différences entre l'exécution locale et l'exécution distante
  Les développeurs et administrateurs de packages doivent savoir qu'il existe des restrictions quant à l'emplacement d'exécution d'un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   **Un package s’exécute sur le même ordinateur que le programme qui le lance**. Même lorsqu'un programme charge un package stocké à distance sur un autre serveur, le package s'exécute sur l'ordinateur local.  
  
-   **Vous pouvez exécuter un package à l’extérieur de l’environnement de développement uniquement sur un ordinateur où est installé Integration Services**. Vous ne pouvez pas exécuter de packages en dehors de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] sur un ordinateur client sur lequel [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n'est pas installé, et les termes de votre licence [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent ne pas vous permettre d'installer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur d'autres ordinateurs. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est un composant serveur et n’est pas redistribuable aux ordinateurs clients. Pour exécuter des packages à partir d'un ordinateur client, vous devez les lancer de manière à garantir leur exécution sur le serveur.  
  
 Pour plus d'informations sur le chargement et l'exécution d'un package enregistré, consultez :  
  
-   [Chargement et exécution d’un package local par programmation](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [Chargement et exécution d’un package distant par programmation](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 Pour plus d'informations sur l'exécution d'un package et le chargement de sa sortie dans un programme personnalisé, consultez :  
  
-   [Chargement de la sortie d’un package local](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Chargement et exécution d’un package local par programmation](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Chargement et exécution d’un package distant par programmation](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [Chargement de la sortie d’un package local](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
