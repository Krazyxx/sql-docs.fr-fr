---
title: Impossible de charger le fichier ou l’assembly &#39;Microsoft.Data.Services, Version = 3.5.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089&#39; ou une de ses dépendances. Le système ne trouve pas le fichier spécifié. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 49e2ce59b8662a8deaf47099c967355150dca201
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62749577"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a>Impossible de charger le fichier ou l’assembly &#39;Microsoft.Data.Services, Version = 3.5.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089&#39; ou une de ses dépendances. Le système ne trouve pas le fichier spécifié.
  Dans les environnements SharePoint 2010 qui disposent de PowerPivot pour SharePoint, cette erreur se produira si vous tentez une exportation de flux de données et que la version requise de Microsoft ADO.NET Data Services n'est pas disponible sur le système.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S'applique à|PowerPivot pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|ADO.NET Data Services 3.5 SP1 est introuvable.|  
|Texte du message|Impossible de charger le fichier ou l'assembly 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' ou une de ses dépendances. Le système ne trouve pas le fichier spécifié.|  
  
## <a name="explanation"></a>Explication  
 SharePoint 2010 inclut un bouton Exporter en tant que flux que vous pouvez utiliser pour exporter une liste SharePoint en tant que flux de données XML. De plus, Reporting Services en mode SharePoint et PowerPivot pour SharePoint prennent tous les deux en charge les fonctionnalités de flux requises par ADO.NET Data Services.  
  
 Si ADO.NET Data Services n'est pas installé, cette erreur se produira lorsque vous demanderez un flux.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
1.  Accédez à la documentation relative à la configuration requise matérielle et logicielle pour SharePoint 2010, [déterminer la configuration matérielle et logicielle requise (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) (https://go.microsoft.com/fwlink/?LinkId=169734).  
  
2.  Dans **Installer les logiciels requis**, recherchez le lien pour ADO.NET Data Services 3.5 correspondant au système d'exploitation que vous utilisez.  
  
3.  Cliquez sur le lien, puis exécutez le programme d'installation qui installe le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer des Solutions PowerPivot pour SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
