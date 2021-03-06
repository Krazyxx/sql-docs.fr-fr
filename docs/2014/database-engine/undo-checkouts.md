---
title: Annuler des extractions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2057c78f953645c9b1a5915b9912ab99263cb005
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62773395"
---
# <a name="undo-checkouts"></a>Annuler des extractions
  Vous pouvez utiliser la **annuler l’extraction** commande pour annuler une extraction existante. Cette opération s'avère particulièrement utile lorsque vous avez modifié et enregistré un fichier et que vous devez par la suite annuler vos modifications.  
  
 Selon les options que vous définissez dans le **annuler les Options d’extraction avancées** boîte de dialogue, l’environnement Studio laisse la copie de l’élément de travail sur votre disque local ou le remplace par la dernière version de contrôle de code source. Si un utilisateur a modifié l'élément en dehors du contexte du système de contrôle de code source, la version extraite peut ne pas être la toute dernière.  
  
### <a name="to-undo-a-checkout"></a>Pour annuler une extraction  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet.  
  
2.  Sur le **fichier** menu, pointez sur **contrôle de code Source**, puis cliquez sur **annuler l’extraction**.  
  
3.  Dans le **annuler l’extraction** boîte de dialogue, sélectionnez les options appropriées, puis cliquez sur le **annuler l’extraction** bouton.  
  
     **Colonnes**  
     Identifiez les colonnes à afficher et l'ordre dans lequel elles s'affichent.  
  
     **Affichage en 2D**  
     Permet d'afficher les éléments sous forme de liste en 2D sous leur connexion de contrôle de code source.  
  
     **Nom**  
     Indique les noms des éléments pour lesquels annuler l'extraction. Les cases à cocher en regard des éléments affichés sont activées. Si vous ne voulez pas annuler l'extraction d'un élément, désactivez sa case à cocher.  
  
     **Options**  
     Affiche les options d'annulation d'extraction spécifiques au plug-in de contrôle de code source lorsque vous cliquez sur la flèche à droite du bouton.  
  
     **Sort**  
     Permet d'ordonner les colonnes d'affichage.  
  
     **Vue d’arborescence**  
     Permet d'afficher la hiérarchie des dossiers et des éléments pour les éléments dont vous annulez l'extraction.  
  
     **Annuler l’extraction**  
     Permet d'annuler l'extraction, en supprimant toutes les modifications apportées au fichier extrait.  
  
## <a name="see-also"></a>Voir aussi  
 [Extraire des fichiers](../../2014/database-engine/check-out-files.md)   
 [Gérer les extractions](../../2014/database-engine/manage-checkouts.md)  
  
  
