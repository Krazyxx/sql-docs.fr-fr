---
title: Tester les autorisations d’un utilisateur (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 38d4b1e7f9bd3e76c00bb4228e53e09416ed8557
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488089"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>Tester les autorisations d’un utilisateur (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez créer un utilisateur de test et vous connecter à l'application Web pour tester les autorisations. Lorsqu'un utilisateur tente d'accéder à l'URL [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , les informations d'identification de l'utilisateur sont authentifiées. Dans Internet Explorer, les paramètres de sécurité déterminent si cette opération se produit automatiquement ou si l'utilisateur doit entrer un nom d'utilisateur et un mot de passe. Pour modifier ces paramètres, procédez comme suit :  
  
### <a name="to-test-a-users-security"></a>Pour tester la sécurité d’un utilisateur  
  
1.  Dans Internet Explorer 7 et version ultérieure, cliquez sur **Outils**, sur **Options Internet**, puis sur l'onglet **Sécurité** .  
  
2.  Cliquez sur **Intranet local** , puis sur le bouton **Personnaliser le niveau** .  
  
3.  Dans la section **Authentification utilisateur** , choisissez **Demander le nom d'utilisateur et le mot de passe**.  
  
4.  La prochaine fois que vous ouvrez la fenêtre de navigateur, vous serez invité à fournir un nom d'utilisateur et un mot de passe.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  
