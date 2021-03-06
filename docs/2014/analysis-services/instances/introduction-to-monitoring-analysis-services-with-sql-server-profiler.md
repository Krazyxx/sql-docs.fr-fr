---
title: Introduction à la surveillance d’Analysis Services avec SQL Server Profiler | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 568ec549-5ddc-493a-b9f8-3bdc548b562e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e5d21e0b5a187fa7b55e104df9b633adc180070c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62730258"
---
# <a name="introduction-to-monitoring-analysis-services-with-sql-server-profiler"></a>Introduction à la surveillance d’Analysis Services à l’aide de SQL Server Profiler
  Vous pouvez utiliser [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour surveiller les événements générés par une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]vous permet d'effectuer les opérations suivantes :  
  
-   Surveiller les performances d'une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   Déboguer des instructions MDX (Multidimensional Expressions).  
  
-   Identifier les instructions MDX qui s'exécutent lentement.  
  
-   Tester les instructions MDX dans la phase de développement d'un projet en exécutant les instructions pas à pas pour vérifier que le code fonctionne comme prévu.  
  
-   Réparer les problèmes de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en capturant des événements sur un système de production et en relisant ces événements capturés sur un système de test. Cette approche est utile à des fins de test et de mise au point, et permet aux utilisateurs de continuer à utiliser le système de production sans perturbation.  
  
-   Réaliser l'audit et l'examen de l'activité intervenue sur une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Un administrateur de la sécurité peut examiner tous les événements audités. Ceci inclut le succès ou l'échec d'une tentative de connexion et le succès ou l'échec d'autorisations lors de l'accès à des instructions et des objets.  
  
-   Afficher des données sur les événements capturés ou capturer et enregistrer des données sur chaque événement dans un fichier ou une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en vue d'une future analyse ou relecture. Lorsque vous relisez des données, vous pouvez réexécuter les événements enregistrés comme ils se sont produits à l'origine, soit en temps réel, soit en pas à pas.  
  
## <a name="using-sql-server-profiler"></a>Utilisation de SQL Server Profiler  
 Pour créer ou relire des traces à l'aide de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , vous devez être membre du rôle de serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Si vous êtes membre du rôle de serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous pouvez démarrer [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] à partir du groupe de programmes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le menu **Démarrer** .  
  
 Lorsque vous utilisez [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], gardez présentes à l'esprit les considérations suivantes :  
  
-   Les définitions de trace sont stockées avec la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'aide de l'instruction CREATE.  
  
-   Plusieurs traces peuvent s'exécuter simultanément.  
  
-   Plusieurs connexions peuvent recevoir des événements de la même trace.  
  
-   Une trace peut continuer lorsque [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s'arrête et redémarre.  
  
    > [!NOTE]  
    >  Les mots de passe ne sont pas révélés dans les événements de trace, mais sont remplacés par \* \* \* \* \* \* dans l’événement.  
  
 Pour optimiser les performances, utilisez [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour ne surveiller que les événements qui vous intéressent le plus. En effet, le fait de surveiller un trop grand nombre d'événements augmente les servitudes logicielles et peut considérablement accroître la taille du fichier ou de la table de trace, surtout si la surveillance se prolonge sur une période importante. En outre, utilisez le filtrage pour limiter la quantité de données recueillies et éviter que les traces ne deviennent trop volumineuses.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de trace Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)   
 [Créer des traces de SQL Server Profiler pour la relecture &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md)  
  
  
