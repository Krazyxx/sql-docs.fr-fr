---
title: Définir des seuils d’avertissement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.setwarningthreshold.f1
ms.assetid: 17f93147-e7d9-4092-b4c2-c11b38051171
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9f1c7c05a02c67fda968ea26bd114d16b0b73925
ms.sourcegitcommit: 8d288ca178e30549d793c40510c4e1988130afb0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805156"
---
# <a name="set-warning-thresholds"></a>Définir les seuils d'avertissement
  Utilisez cette boîte de dialogue pour activer et configurer un ou plusieurs seuils d'avertissement pour la base de données sélectionnée dans l'arborescence de navigation de la boîte de dialogue **Moniteur de mise en miroir de bases de données** .  
  
 La boîte de dialogue tente d'établir une connexion avec les deux instances de serveurs. Ces connexions sont établies de façon asynchrone. La boîte de dialogue affiche l'état de la connexion de chaque partenaire. Si le partenaire n'est pas connecté, vous pouvez cliquer sur **Se connecter**.  
  
 **Pour utiliser SQL Server Management Studio pour contrôler la mise en miroir de base de données**  
  
-   [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a>Options  
 *Instance de serveur et état de la connexion*  
 Nom d’une instance de serveur partenaire au format _SYSTÈME_**\\**_NOM_INSTANCE_. Pour une instance de serveur par défaut, seul le nom du système s'affiche.  
  
 Ce champ indique également si le moniteur est actuellement connecté à cette instance de serveur. Les états de connexion possibles sont les suivants :  
  
-   **Non connecté à**  *nom_instance_serveur*  
  
-   **Tentative de connexion à**  *nom_instance_serveur*  
  
-   **Connecté à**  *nom_instance_serveur*  
  
    > [!NOTE]  
    >  Si vous n’êtes pas membre du rôle de serveur fixe **sysadmin** , l’état est **Connecté à** *nom_instance_serveur* **(Autorisations limitées)**.  
  
 Le nom de chaque instance de serveur partenaire est affiché dans un champ d' *instance de serveur et d'état de la connexion* distinct. Le premier champ affiche le serveur principal au démarrage du moniteur.  
  
 **Se connecter**/**Annuler**  
 Un bouton **Se connecter**/**Annuler** est associé à chaque champ d’ *instance de serveur et état de la connexion* . L'état de ce bouton dépend de l'état de la connexion :  
  
-   Si aucune connexion à l'instance de serveur n'est établie, l'intitulé du bouton est **Se connecter**. Cliquez sur le bouton pour vous connecter à l'instance de serveur.  
  
-   Lorsqu'une tentative de connexion est en cours, l'intitulé du bouton est **Annuler**. Cliquez sur le bouton pour annuler la tentative de connexion.  
  
-   Si le serveur est connecté, le bouton est grisé et son intitulé est **Connecté**.  
  
 **Seuils**  
 La grille **Seuils** affiche les paramètres d’avertissement pour les deux instances de serveurs.  
  
> [!NOTE]  
>  Si une instance de serveur n'est pas connectée, ses colonnes affichent des cellules vides sur un fond gris. Lorsque la connexion s'ouvre, la grille affiche automatiquement le contenu à partir de l'instance.  
  
 Cette grille comporte les colonnes suivantes :  
  
 **Avertissements**  
 Répertorie les avertissements pris en charge :  
  
|Warning|Description|  
|-------------|-----------------|  
|**Avertir si le journal non envoyé dépasse le seuil**|Ce seuil indique la taille en kilo-octets (Ko) du journal non envoyé dans la file d'attente d'envoi sur le principal.|  
|**Avertir si le journal non restauré dépasse le seuil**|Ce seuil indique la taille (en Ko) de la file d'attente de restauration sur l'instance du serveur miroir.|  
|**Avertir si la durée de vie de la plus ancienne transaction non envoyée dépasse le seuil**|Ce seuil indique la durée exprimée en minutes des transactions qui n'ont pas encore été envoyées depuis la file d'attente d'envoi vers l'instance de serveur miroir. Cette valeur permet de mesurer la perte de données potentielle en termes de temps.|  
|**Avertir si le temps de traitement de validation de miroir dépasse le seuil**|Ce seuil indique le délai en millisecondes par transaction (utile uniquement en mode haute sécurité). Ce délai correspond au temps de traitement pendant lequel l'instance de serveur principal attend que l'instance de serveur miroir écrive l'enregistrement du journal de transaction dans la file d'attente de restauration par progression.|  
  
 **Activé sur «**   *\<instance_serveur>*   **»**  
 Une case à cocher vide indique que l'avertissement est actuellement désactivé sur l'instance de serveur. Pour activer l'avertissement, activez la case à cocher.  
  
 **Seuil sur «**   *\<instance_serveur>*   **»**  
 Lorsqu'un avertissement est activé, définissez le seuil dans la partie gauche de cette colonne. Un événement se produit si le seuil spécifié est atteint lors de la mise à jour de la table d'état. Si vous désactivez un seuil après avoir configuré une valeur, cette valeur reste dans le champ et sera utilisée lorsque vous activerez de nouveau l'avertissement.  
  
 Lorsqu'un avertissement n'est pas activé, ce champ est inactif.  
  
 **OK**  
 Quand vous cliquez sur **OK** , cette boîte de dialogue se ferme et les valeurs actuellement spécifiées pour les seuils d’avertissement s’affichent dans la grille **Seuils** de la page à onglets **Avertissements**.  
  
## <a name="remarks"></a>Notes  
 Un seuil est applicable à un seul partenaire à la fois, mais nous vous recommandons de définir un seuil pour un événement donné sur les deux partenaires, afin de vous assurer que l'avertissement persiste lors du basculement de la base de données. Le seuil approprié pour chaque partenaire dépend des capacités de performance du système du partenaire.  
  
 Un événement est écrit dans le journal des événements pour une performance uniquement si sa valeur est identique ou supérieure au seuil au moment de la mise à jour de la table d'état. Si une valeur maximale atteint momentanément le seuil entre des mises à jour d'état, cette valeur est ignorée.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
