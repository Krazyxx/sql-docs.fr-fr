---
title: Dossier d’instantanés | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5f8e3050afe889fd1c7f7de489b7ed6d22d3a50f
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54133199"
---
# <a name="snapshot-folder"></a>Dossier d'instantanés
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La page **Dossier d'instantanés** figure dans l'Assistant Configuration de la distribution et l'Assistant Nouvelle publication. L'emplacement que vous définissez pour le dossier d'instantanés est utilisé par défaut pour tous les serveurs de publication activés dans cet Assistant (le dossier par défaut des instantanés ne s'applique pas aux serveurs de publication qui sont ensuite activés dans la boîte de dialogue **Propriétés du serveur de distribution** ). Vous pouvez changer ce dossier par défaut pour n'importe quel serveur de publication dans la page **Serveurs de publication** de l'Assistant Configuration de la distribution ou la boîte de dialogue **Propriétés du serveur de distribution** .  
  
 Le dossier d'instantanés correspond à un simple répertoire que vous définissez sous la forme d'un partage ; les agents qui lisent et écrivent dans le dossier doivent disposer des autorisations suffisantes pour pouvoir y accéder. Pour plus d’informations sur une sécurisation appropriée du dossier, consultez [Sécuriser le dossier d’instantanés](../../relational-databases/replication/security/secure-the-snapshot-folder.md). Avant d'implémenter la réplication, vérifiez que les agents de réplication peuvent se connecter au dossier d'instantanés. Connectez-vous sous le compte qu'utilisera chaque agent et essayez ensuite d'accéder au dossier d'instantanés.  
  
## <a name="options"></a>Options  
 **Snapshot folder**  
 Entrez le chemin d'accès au dossier où vous souhaitez stocker les fichiers d'instantanés.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'utiliser un partage réseau comme emplacement pour le dossier d'instantanés. Les chemins locaux (ceux qui commencent par une lettre de lecteur, tel que C:\\) ne sont pas accessibles aux agents sur les autres ordinateurs.  
  
## <a name="see-also"></a> Voir aussi  
 [Modifier les options d’instantané](../../relational-databases/replication/snapshot-options.md)   
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
