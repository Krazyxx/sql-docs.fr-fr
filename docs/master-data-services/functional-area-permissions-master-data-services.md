---
title: Autorisations de zone fonctionnelle (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- functional area permissions [Master Data Services], about functional area permissions
- functional area permissions [Master Data Services]
- permissions [Master Data Services], functional areas
ms.assetid: a80b87b3-b904-4cda-8582-0761c2617c57
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 87af739d7e1b2d45d226c32c7a2fd99fa0ae37bd
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65485894"
---
# <a name="functional-area-permissions-master-data-services"></a>Autorisations de zone fonctionnelle (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Vous pouvez affecter une autorisation à chacune des zones fonctionnelles de l’interface utilisateur du [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Les zones fonctionnelles sont les suivantes :  
  
-   **Explorateur**  
  
-   **Gestion des versions**  
  
-   **Gestion de l'intégration**  
  
-   **Administration de système**  
  
-   **Autorisations d'accès**  
  
-   **Super utilisateur**  
  
 Lorsque vous affectez une autorisation à une zone fonctionnelle, vous rendez une zone de l'interface utilisateur visible à l'utilisateur ou au groupe.  
  
 Dans la zone fonctionnelle **Explorateur** , les autorisations supplémentaires affectées aux objets de modèle et aux membres de hiérarchie déterminent les données auxquelles un utilisateur peut accéder. Dans toutes les autres zones fonctionnelles, un utilisateur doit être administrateur de modèle pour afficher un modèle et agir sur lui. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
> [!IMPORTANT]  
>  Un utilisateur avec l’autorisation fonctionnelle Super utilisateur a en réalité l’autorisation d’administrateur sur tous les modèles et a toutes les autres autorisations fonctionnelles.  
  
 Un utilisateur ou groupe doit avoir une autorisation sur au moins une zone fonctionnelle et un modèle sous l'onglet **Modèles** afin d'accéder à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Affecter des autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/assign-functional-area-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Autorisations des membres de la hiérarchie &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Mode de détermination des autorisations &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
