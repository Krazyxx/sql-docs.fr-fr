---
title: Propriétés du serveur dans Analysis Services | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ce74bb210e3d5d3cd01120b0bd406672db6dd5ed
ms.sourcegitcommit: f46fd79fd32a894c8174a5cb246d9d34db75e5df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/26/2018
ms.locfileid: "53785820"
---
# <a name="server-properties-in-analysis-services"></a>Propriétés du serveur dans Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Un administrateur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut modifier les propriétés de configuration par défaut du serveur d’une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Chaque instance a ses propriétés de configuration propres, qui sont définies indépendamment des autres instances présentes sur le même serveur.  
  
 Pour configurer le serveur, utilisez SQL Server Management Studio ou modifiez le fichier msmdsrv.ini d’une instance de SQL Server Analysis Services spécifique.  
 
Les pages de propriétés dans SQL Server Management Studio affichent un sous-ensemble des propriétés susceptibles d’être modifiées. La liste complète des propriétés figure dans le fichier msmdsrv.ini.   
  
> [!NOTE]  
>  Dans une installation de SQL Server Analysis Services par défaut, msmdsrv.ini peut être trouvé dans le Files\Microsoft SQL Server\MSAS13. Dossier de MSSQLSERVER\OLAP\Config.
> 
> Parmi les autres propriétés qui affectent la configuration du serveur figurent les propriétés de configuration de déploiement dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations sur ces propriétés, consultez [Spécification de paramètres de configuration pour le déploiement de solutions](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md).
 
## <a name="configure-properties-in-management-studio"></a>Configurer des propriétés dans Management Studio 
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2. Dans l’Explorateur d’objets, cliquez avec le bouton droit sur l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puis cliquez sur **Propriétés**. La page Général apparaît, affichant les propriétés couramment utilisées.  

3.  Pour afficher des propriétés supplémentaires, cochez la case **Afficher les propriétés avancées (toutes)** en bas de la page.  
  
     La modification des propriétés du serveur est prise en charge uniquement pour les serveurs en mode multidimensionnel et en mode tabulaire. Si vous avez installé [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], utilisez toujours les valeurs par défaut, sauf indication contraire fournie par le Support Microsoft.  
  
  
## <a name="configure-properties-in-msmdsrvini"></a>Configurer des propriétés dans msmdsrv.ini
  
Certaines propriétés ne peuvent être définies que dans le fichier msmdrsrv.ini. Ces propriétés ne s’appliquent pas à Azure Analysis Services.
Si la propriété qui vous intéresse n'est pas visible même après affichage des propriétés avancées, vous devrez la modifier directement dans le fichier msmdsrv.ini. 
  
1.  Consultez la propriété **DataDir** dans la page Propriétés générales de Management Studio pour vérifier l’emplacement des fichiers programmes Analysis Services, dont le fichier msmdsrv.ini.

     Sur un serveur ayant plusieurs instances, la vérification de l’emplacement du fichier programme permet de s’assurer que vous modifiez le fichier approprié.  
  
2.  Accédez au dossier **config** à l’emplacement du dossier de fichiers programmes.

3. Créez une sauvegarde du fichier, ce qui vous permettra de le restaurer en cas de besoin.  
  
4.  Utilisez un éditeur de texte pour afficher ou modifier le fichier msmdsrv.ini.  
  
5.  Enregistrez le fichier et redémarrez le service.  
  
##  <a name="server-property-reference"></a>Référence de propriété de serveur  
  
 Les rubriques suivantes décrivent les diverses propriétés de configuration de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Propriétés générales](../../analysis-services/server-properties/general-properties.md)|Les propriétés générales sont des propriétés fondamentales et avancées qui définissent notamment le répertoire de données, le répertoire de sauvegarde et d'autres comportements du serveur.|  
|[Propriétés de l'exploration de données](../../analysis-services/server-properties/data-mining-properties.md)|Les propriétés d'exploration de données déterminent les algorithmes d'exploration de données à activer ou à désactiver. Par défaut, tous les algorithmes sont activés.| 
|[Propriétés DAX](../../analysis-services/server-properties/dax-properties.md)|Définit les propriétés liées aux requêtes DAX.|
|DSO|DSO n'est plus pris en charge. Les propriétés DSO sont ignorées.|  
|[Propriétés de fonctionnalité](../../analysis-services/server-properties/feature-properties.md)|Les propriétés de fonctionnalité se rapportent à des fonctionnalités de produit, le plus souvent de caractère avancé. Il s'agit notamment de propriétés qui contrôlent les liaisons entre les instances de serveur.|  
|[Propriétés du cache de fichiers](../../analysis-services/server-properties/filestore-properties.md)|Les propriétés du stockage de fichiers s'adressent uniquement aux utilisateurs expérimentés. Elles contiennent des paramètres avancés de gestion de la mémoire.|  
|[Propriétés du gestionnaire de verrous](../../analysis-services/server-properties/lock-manager-properties.md)|Les propriétés du gestionnaire de verrous définissent les comportements du serveur en matière de verrouillage et de délais d'attente. La plupart de ces propriétés s'adressent uniquement aux utilisateurs expérimentés.|  
|[Propriétés du journal](../../analysis-services/server-properties/log-properties.md)|Les propriétés du journal contrôlent si des événements sont enregistrés sur le serveur et, dans l'affirmative, à quel emplacement et de quelle façon. Il s'agit en particulier de l'enregistrement des erreurs, des exceptions et des requêtes, de la boîte noire SQL et des traces.|  
|[Propriétés de mémoire](../../analysis-services/server-properties/memory-properties.md)|Les propriétés de la mémoire contrôlent la façon dont le serveur utilise la mémoire. Elles s'adressent essentiellement aux utilisateurs expérimentés.|  
|[Propriétés réseau](../../analysis-services/server-properties/network-properties.md)|Les propriétés réseau contrôlent le comportement du serveur en matière de réseau, et contiennent notamment des paramètres XML binaire et de compression. La plupart de ces propriétés s'adressent uniquement aux utilisateurs expérimentés.|  
|[Propriétés OLAP](../../analysis-services/server-properties/olap-properties.md)|Les propriétés OLAP contrôlent le traitement des cubes et des dimensions, le traitement différé, la mise en cache des données et le comportement des requêtes. Il s'agit de propriétés fondamentales et de propriétés avancées.|  
|[Propriétés de sécurité](../../analysis-services/server-properties/security-properties.md)|La section de la sécurité contient des propriétés fondamentales et avancées qui définissent les autorisations d'accès. Il s'agit de paramètres concernant les administrateurs et les utilisateurs.|  
|[Propriétés du pool de threads](../../analysis-services/server-properties/thread-pool-properties.md)|Les propriétés du pool de threads contrôlent le nombre de threads que crée le serveur. Il s'agit essentiellement de propriétés avancées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion d'instances Analysis Services](../../analysis-services/instances/analysis-services-instance-management.md)   
 [Spécification de paramètres de configuration pour le déploiement de solutions](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
