---
title: Prise en main 2017 du serveur SQL dans le Cloud | Documents Microsoft
description: "Ce didacticiel de démarrage rapide montre comment exécuter le 2017 du serveur SQL sur Linux dans le cloud de votre choix."
author: annashres
ms.author: annashres
manager: jhubbard
ms.date: 10/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.component: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.openlocfilehash: 5a7ea24d7563a7256c93dbfaa052bfb4041f9aa0
ms.sourcegitcommit: 085dd05d56afecbb454206ed8402cfbaa597cfbe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="run-the-sql-server-2017-in-the-cloud"></a>Exécutez le 2017 du serveur SQL dans le cloud

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Dans ce didacticiel de démarrage rapide, vous allez installer SQL Server 2017 sur Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) ou Ubuntu dans le cloud de votre choix. Accédez à [configure un ordinateur virtuel Linux SQL Server, dans le portail Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json) pour exécuter SQL Server sur Linux dans Azure.

    > [!NOTE]
    > If you choose to run a paid edition of SQL Server then you need to bring your own license (BYOL)

## <a name="amazon-web-services"></a>Amazon Web Services
1.  Créer un AMI Linux au moins 2 Go de mémoire à partir du marketplace 
    * [RHEL 7.3 +](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES v12 SP2](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  Se connecter à l’AMI avec ssh
1.  Suivez le démarrage rapide pour le distrbution de Linux que vous avez choisi : 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Configurer des connexions à distance : 
    * Ouvrez le [Amazon EC2 console]( https://console.aws.amazon.com/ec2/)
    * Dans le volet de navigation, choisissez **groupes de sécurité**. 
    * Choisissez **entrant, modifier, ajouter une règle**
    * Ajouter une règle de trafic entrant pour autoriser le trafic sur le port sur lequel SQL Server écoute (port TCP par défaut 1433)

    
## <a name="digital-ocean"></a>Numérique océan
1. Connexion à la [le panneau de configuration](https://cloud.digitalocean.com/login) et cliquez sur Créer un droplet
1. Choisissez un droplet Ubuntu 16.04 au moins 2 Go de mémoire
1. Se connecter au droplet avec ssh
1. Suivez les [démarrage rapide d’Ubuntu](quickstart-install-connect-ubuntu.md)
1. Configurer des connexions à distance :
    * En haut du Panneau de configuration, suivez la **réseau** lier, puis sélectionnez **les pare-feu**
    * Ajouter une règle de trafic entrant pour autoriser le trafic sur le port sur lequel SQL Server écoute (port TCP par défaut 1433)
    
## <a name="google-cloud-platform"></a>Plateforme de Cloud de Google
1.  Créer une image Linux au moins 2 Go de mémoire à partir du Lanceur de Cloud 
    * [RHEL 7.3 +](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES v12 SP2](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  Se connecter à l’image avec ssh
1.  Suivez le démarrage rapide pour le distrbution de Linux que vous avez choisi : 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Configurer des connexions à distance : 
    * Accédez à la [des règles de pare-feu](https://console.cloud.google.com/networking/firewalls)
    * Ajouter une règle de trafic entrant pour autoriser le trafic sur le port sur lequel SQL Server écoute (TCP : 1433 de la valeur par défaut)