---
title: Configurer le site Web et la base de données pour Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 426b165aa99dad2bda0fd7428d4100d384ae66e1
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65482794"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>Configurer la base de données et le site web de Master Data Services
  Utilisez le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] pour configurer la base de données et le site web pour [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS)  
  
 Pour configurer la base de données et le site web, effectuez les tâches suivantes :  
  
1.  Créer une base de données en utilisant le **Configuration de la base de données** page [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Pour plus d’informations, consultez [Page de Configuration de base de données &#40;Gestionnaire de Configuration de Master Data Services&#41; ](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) et [Assistant Création de la base de données &#40;Gestionnaire de Configuration de Master Data Services&#41; ](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
2.  Créer un nouveau site Web, sélectionnez le site Web par défaut ou sélectionnez un autre site Web existant, à l’aide de la **Configuration Web** page [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Associez ensuite la base de données MDS à l'application web sélectionnée ou créée.  
  
     Pour plus d’informations, consultez [Page Configuration Web &#40;Gestionnaire de Configuration de Master Data Services&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) et [créer une boîte de dialogue site Web &#40;Gestionnaire de Configuration de Master Data Services&#41; ](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).  
  
3.  (Facultatif) Activer l’intégration avec Data Quality Services à l’aide de la **Configuration Web** page [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Pour plus d’informations, consultez [Page Configuration Web &#40;Gestionnaire de Configuration de Master Data Services&#41; ](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) et [activer l’intégration Data Quality Services avec Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 Vous pouvez utiliser [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] pour spécifier des paramètres pour les applications et services web associés à la base de données MDS. Par exemple, vous pouvez spécifier la fréquence à laquelle les données sont chargées ou des e-mails de validation envoyés. Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Base de données Master Data Services](../../2014/master-data-services/master-data-services-database.md)   
 [Application web Master Data Manager](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
