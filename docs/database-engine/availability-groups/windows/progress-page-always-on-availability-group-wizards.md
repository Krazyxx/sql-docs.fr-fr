---
title: Page Progression (Assistants de groupe de disponibilité Always On)
description: Description des options disponibles dans la « page Progression » de « l’Assistant Groupe de disponibilité Always On » dans SQL Server Management Studio.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.failoverwizard.progress.f1
- sql13.swb.adddatabasewizard.progress.f1
- sql13.swb.addreplicawizard.progress.f1
- sql13.swb.newagwizard.progress.f1
ms.assetid: bd3b0306-8384-4120-a1c9-03825f0ae26a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 147af9a2eecfe58cfc329fd8ce22b0452e21c59e
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53210485"
---
# <a name="progress-page-always-on-availability-group-wizards"></a>Page Progression (Assistants de groupe de disponibilité Always On)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Utilisez cette boîte de dialogue pour afficher la progression d'un Assistant [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] que vous exécutez dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. La barre de progression indique la progression relative des étapes que l'Assistant effectue.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Plus de détails**  
 Cliquez sur la flèche bas pour afficher une grille de progression qui répertorie toutes les étapes effectuées, dans l'ordre, suivies de l'opération en cours actuelle. Cette grille comporte les colonnes suivantes :  
  
 **Nom**  
 Affiche une expression qui décrit une étape spécifique.  
  
 **État**  
 Indique le résultat des étapes terminées et le pourcentage d'exécution de l'étape active, comme suit :  
  
|Résultats|Description|  
|------------|-----------------|  
|**Erreur**|Indique que l'opération pour cette étape a rencontré une erreur. Cliquez sur le lien pour afficher une boîte de dialogue de message qui décrit l'erreur.|  
|**En cours (** *pourcentage-effectué* **)**|Indique que l'opération a maintenant lieu et estime le pourcentage de réalisation de cette étape.|  
|**Réussi**|Indique que l'opération pour cette étape s'est terminée avec succès.|  
  
 **Moins de détails**  
 Cliquez pour masquer la grille de progression.  
  
 **Annuler**  
 Cliquez pour ignorer les opérations restantes, puis quittez l'Assistant.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter une base de données au groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
-   [Utiliser l’Assistant Basculer le groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
