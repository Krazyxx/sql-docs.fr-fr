---
title: Boîte de dialogue Source (Analysis Services - données multidimensionnelles) de partition | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionsourcedialog.f1
ms.assetid: c414dabe-9bad-49b7-9a3c-dfca87fef92b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f88f307f9cbace833a83603e0f24382b7e82e62f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743565"
---
# <a name="partition-source-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Source de partition (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Source de partition** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir la source des données de table de faits d'une partition. Pour afficher la boîte de dialogue **Source de partition** :  
  
-   cliquez sur le bouton **...** dans une cellule de la grille **Partitions** d'un groupe de mesures sélectionné dans le volet **Groupes de mesures** de l'onglet **Partitions** dans le Concepteur de cube ;  
  
-   cliquez sur le bouton **...** de la valeur de la propriété **Source** ou d'un objet **Partition** dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="options"></a>Options  
  
|Option|Définition|  
|------------|----------------|  
|**Type de liaison**|Sélectionnez le type de liaison à utiliser pour la source de la partition spécifiée. Les options suivantes sont disponibles :<br /><br /> **Liaison de table**: Sélectionnez cette option pour afficher le volet **Détails de la liaison de table** et indiquez que la partition est liée au contenu d’une table d’une source de données ou d’une vue de source de données. Pour plus d’informations sur le volet **Détails de la liaison de table**, consultez [Détails de la liaison de table &#40;boîte de dialogue Source de partition&#41; &#40;Analysis Services – Données multidimensionnelles&#41;](table-binding-partition-source-dialog-analysis-services-multidimensional-data.md).<br /><br /> **Détail**: Sélectionnez cette option pour afficher le volet **Détails de la liaison de requête** et indiquez que la partition est liée au contenu d’une requête exécutée sur une source de données. Pour plus d’informations sur le volet **Détails de la liaison de requête**, consultez [Détails de la liaison de requête &#40;boîte de dialogue Source de partition&#41; &#40;Analysis Services – Données multidimensionnelles&#41;](query-binding-partition-source-dialog-analysis-services-multidimensional-data.md).|  
|**Detail**|Affiche la boîte de dialogue **Détails de la liaison de table** ou **Détails de la liaison de requête** en fonction de la valeur de l'option **Type de liaison** .|  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
