---
title: Journal des requêtes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 165d3833-0493-490c-9f63-8a134a7fafb8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 521d40529501d761b8e50300c16a816284109695
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62770886"
---
# <a name="request-log"></a>Journal des requêtes
  Utilisez la boîte de dialogue **Journal des requêtes** pour afficher les événements journalisés lors de la demande qui est effectuée au système SAP Netweaver BW pour les exemples de données. Ces informations peuvent être utiles si vous devez dépanner votre configuration de la source SAP BW.  
  
 Pour en savoir plus sur le composant source SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [SAP BW Source](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
 **Pour ouvrir la boîte de dialogue Journal des requêtes**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la source SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source SAP BW.  
  
3.  Dans **l’Éditeur de source SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Après avoir configuré la source SAP BW, cliquez sur **Aperçu** pour afficher un aperçu des événements dans la boîte de dialogue **Journal des requêtes** .  
  
    > [!NOTE]  
    >  Cliquer sur **Aperçu** ouvre également la boîte de dialogue **Aperçu** . Pour plus d'informations sur cette boîte de dialogue, consultez [Preview](preview.md).  
  
## <a name="options"></a>Options  
 **Time**  
 Affiche l'heure à laquelle l'événement a été journalisé.  
  
 **Type**  
 Affiche le type de l'événement qui a été journalisé. Le tableau suivant répertorie les types d'événements possibles.  
  
|Value|Description|  
|-----------|-----------------|  
|S|Message de réussite.|  
|E|Message d'erreur|  
|W|Message d'avertissement.|  
|I|Message d’information.|  
|A|L'opération a été abandonnée.|  
  
 **Message**  
 Affiche le texte du message associé à l'événement journalisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de source SAP BW &#40;page Gestionnaire de connexions&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
