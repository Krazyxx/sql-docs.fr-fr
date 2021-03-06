---
title: Définir l’Intelligence comptable (Assistant Dimension) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.accountintelligencetypemapping.f1
ms.assetid: cbcff072-3a7e-4e98-858f-1b4265461561
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 927442d1fe46fc42998643d4f7de47b438cbaa49
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62732454"
---
# <a name="define-account-intelligence-dimension-wizard"></a>Définir l'intelligence comptable (Assistant Dimension)
  Utilisez la page **Définir l'intelligence comptable** pour faire correspondre les types de comptes définis dans l'instance [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] avec ceux définis dans l'attribut de dimension associé à l'attribut **Type de compte** de la dimension.  
  
> [!NOTE]  
>  Cette page s’affiche uniquement si vous avez sélectionné **Dimension standard** dans la page **Sélectionner le type de la dimension** et si vous avez mappé un attribut de dimension au type d’attribut **Type de compte** dans la page **Spécifier le type de la dimension** .  
  
## <a name="options"></a>Options  
 **Types de comptes de Table source**  
 Affiche les valeurs contenues dans l’attribut de dimension affecté au type d’attribut du **Type de compte** dans la page **Spécifier la clé et le type de la dimension** .  
  
 **Types de comptes intégrés**  
 Sélectionnez le type de compte défini dans l'instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui correspond aux types de comptes de la table source.  
  
 Le tableau ci-dessous répertorie les types de comptes définis dans une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
|Value|Description|  
|-----------|-----------------|  
|**Actif**|Valeur des biens possédés à un moment donné.|  
|**Balance**|Comptage d'une grandeur à un moment donné.|  
|**Dépenses**|Valeur des dépenses engagées.|  
|**Flux**|Comptage incrémental de biens.|  
|**Revenu**|Valeur des biens reçus.|  
|**Dettes**|Valeur des biens dus à un moment donné.|  
|**Statistique**|Rapport calculé d'une grandeur, ou comptage d'une grandeur qu'il n'est pas possible d'agréger.|  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
