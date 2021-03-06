---
title: Masquer des éléments de légende dans le graphique (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 88c798ce1bd5f25b1a844894b8aa609a4c641e4c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63185595"
---
# <a name="hide-legend-items-on-the-chart-report-builder-and-ssrs"></a>Masquer des éléments de légende dans le graphique (Générateur de rapports et SSRS)
  Par défaut, toute série ajoutée à un graphique qui n'est pas à base de formes sera ajoutée en tant qu'élément à la légende. Pour les graphiques à secteurs, en anneau, en entonnoir et en pyramide, toute série ajoutée au graphique ajoutera des points de données individuels à la légende.  
  
 Vous pouvez masquer tout élément de la légende. Lorsque vous masquez un élément de légende, celui-ci continuera à figurer dans le graphique. Cela peut s'avérer utile dans les cas où vous ne souhaiteriez pas afficher plus d'informations sur une série ajoutée au graphique. Par exemple, si vous avez ajouté une série calculée comme une moyenne mobile au graphique, vous pouvez masquer cette entrée dans la légende de manière à afficher davantage d'informations sur la série d'origine uniquement.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-an-item-from-display-in-the-legend"></a>Pour masquer un élément dans la légende  
  
1.  Cliquez avec le bouton droit sur la série que vous souhaitez masquer et sélectionnez **Propriétés de la série**.  
  
2.  Cliquez sur **Légende**. Sélectionnez l'option **Ne pas afficher cette série dans une légende** .  
  
    > [!NOTE]  
    >  Vous ne pouvez pas masquer une série d'un groupe et pas des autres. Si vous avez ajouté un champ à la zone **Groupes de séries** , toutes les séries qui appartiennent à ce groupe seront masquées.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme de la légende sur un graphique &#40;Générateur de rapports et SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [Mise en forme des points de données sur un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Modifier le texte d’un élément de légende &#40;Générateur de rapports et SSRS&#41;](chart-legend-change-item-text-report-builder.md)   
 [Ajouter une moyenne mobile à un graphique &#40;Générateur de rapports et SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés de la légende, Général &#40;Générateur de rapports et SSRS&#41;](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
