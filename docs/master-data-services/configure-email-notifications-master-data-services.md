---
title: Configurer des notifications par e-mail (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- e-mail [Master Data Services], configuring
- notifications [Master Data Services], configuring notifications
ms.assetid: 4241a6ab-7465-471b-9890-57c6b572037e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 58c88e60e4d4b4fa0b25cb5bdafe3ad248a794de
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65484441"
---
# <a name="configure-email-notifications-master-data-services"></a>Configurer des notifications par courrier électronique (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Configurez des e-mail de notification lorsque vous souhaitez que [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] envoie automatiquement des e-mails.  
  
### <a name="to-configure-notifications"></a>Pour configurer des notifications  
  
1.  Dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], dans la page **Base de données** , sélectionnez votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Dans la section **Paramètres système** , cliquez sur **Créer un profil**.  
  
3.  Complétez tous les champs obligatoires. Pour plus d’informations, consultez [Boîte de dialogue Créer un compte et un profil de messagerie de base de données &#40;Gestionnaire de configuration des services de données de référence&#41;](../master-data-services/create-database-mail-profile-and-account-dialog-box.md).  
  
4.  Cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Après avoir configuré des notifications, vous ne pouvez pas utiliser le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] pour apporter des modifications. Vous devez apporter les modifications directement dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations, consultez [Objets de configuration de la messagerie de base de données](../relational-databases/database-mail/database-mail-configuration-objects.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Il existe des paramètres dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] qui affectent les notifications. Vous pouvez ajuster ces paramètres dans [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] ou directement dans la table Paramètres système dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Notifications &#40;Master Data Services&#41;](../master-data-services/notifications-master-data-services.md)   
 [Résolution des problèmes liés aux notifications par courrier électronique (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)   
 [Configurer des règles d’entreprise pour envoyer des notifications &#40;Master Data Services&#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
