---
title: Affecter des autorisations d’objet de modèle (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4daf79842158cabf8dc42f5f544a6bb0f3d8b62b
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65478633"
---
# <a name="assign-model-object-permissions-master-data-services"></a>Affecter des autorisations d'objet de modèle (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], affectez les autorisations aux objets de modèle lorsque vous devez donner à un utilisateur ou un groupe l'accès aux données dans la zone fonctionnelle **Explorateur** de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], ou lorsque vous devez faire d'un utilisateur ou d'un groupe un administrateur.  
  
> [!NOTE]  
>  Lorsque vous affectez une autorisation à un modèle, l'autorisation à tous les autres modèles est refusée implicitement. Si vous n'affectez pas d'autorisations d'objet de modèle, l'utilisateur ou le groupe ne peut accéder à aucune donnée dans l' **Explorateur**.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Autorisations d'accès** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-assign-model-object-permissions"></a>Pour affecter des autorisations d'objet de modèle  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Autorisations d'accès**.  
  
2.  Dans la page **Utilisateurs** ou **Groupes** , sélectionnez la ligne de l'utilisateur ou du groupe à modifier.  
  
3.  Cliquez sur **Modifier l'utilisateur sélectionné**.  
  
4.  Cliquez sur l'onglet **Modèles** .  
  
5.  Dans la liste **Modèle** , sélectionnez éventuellement un modèle.  
  
6.  Cliquez sur **Modifier**.  
  
7.  Développez l'arborescence, puis cliquez sur l'objet de modèle auquel vous souhaitez affecter des autorisations.  
  
8.  Dans le menu, sélectionnez une combinaison d’autorisations (lecture, création, mise à jour et suppression, ou refus).  
  
9. Au niveau du modèle de niveau supérieur, sélectionnez **Admin** pour créer un administrateur de modèles utilisateur.  
  
10. Cliquez sur **Enregistrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   (Facultatif) [Affecter des autorisations de membre de hiérarchie &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer des autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/delete-model-object-permissions-master-data-services.md)   
 [Autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Créer un administrateur de modèle &#40;Master Data Services&#41;](../master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
