---
title: Enregistrer des résultats d’une trace dans une table (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4679576a8336d9a35299622b8513b9c8ae855287
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267780"
---
# <a name="save-trace-results-to-a-table-sql-server-profiler"></a>Enregistrer des résultats d'une trace dans une table (SQL Server Profiler)
  Cette rubrique explique comment enregistrer les résultats d'une trace dans une table de base de données à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-save-trace-results-to-a-table"></a>Pour enregistrer les résultats d'une trace dans une table  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion**est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et le suivi se lance. Pour désactiver ce paramètre, accédez au menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la zone **Nom de la trace** , entrez le nom de la trace, puis cliquez sur **Enregistrer dans la table**.  
  
3.  Dans la boîte de dialogue **Se connecter au serveur** , connectez-vous à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contiendra la table.  
  
4.  Dans la boîte de dialogue **Table de destination** , sélectionnez le nom d’une base de données dans la liste **Base de données**.  
  
5.  Dans la liste **Propriétaire** , sélectionnez le propriétaire de la trace.  
  
6.  Dans la liste **Table** , tapez ou sélectionnez le nom de la table dans laquelle seront enregistrés les résultats de la trace. Cliquez sur **OK.**  
  
7.  Dans la boîte de dialogue **Propriétés de la trace** , cochez la case **Définir le nombre de lignes maximal (en milliers)** pour définir le nombre maximal de lignes à enregistrer.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
