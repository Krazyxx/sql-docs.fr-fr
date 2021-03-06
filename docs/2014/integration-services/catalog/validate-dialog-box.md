---
title: Boîte de dialogue Valider | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.isprojectvalidate.f1
- sql13.ssis.ssms.ispackagevalidate.f1
ms.assetid: 134e14ce-4f8d-4a20-889a-918014c841d8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8380b3ff1502088e0131b182149e90e31d2be42c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62771648"
---
# <a name="validate-dialog-box"></a>Boîte de dialogue Valider
  Utilisez la boîte de dialogue **Valider** pour examiner les problèmes usuels d'un projet ou package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 En cas de problème, un message s'affiche en haut de la boîte de dialogue. Sinon, le terme Prêt s'affiche en haut.  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir la boîte de dialogue Valider](#open_dialog)  
  
-   [Définir les options sur la page Général](#general)  
  
##  <a name="open_dialog"></a> Ouvrir la boîte de dialogue Valider  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous au serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Vous vous connectez à l’instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge la base de données SSISDB.  
  
2.  Dans l'Explorateur d'objets, développez l'arborescence pour afficher le nœud **Integration Services Catalogues** .  
  
3.  Développez le nœud **SSISDB** .  
  
4.  Développez le dossier qui contient le projet ou package à valider.  
  
5.  Cliquez avec le bouton droit sur le projet ou le package, puis cliquez sur **Valider**.  
  
##  <a name="general"></a> Définir les options sur la page Général  
 **Environnement**  
 Sélectionnez l'environnement à utiliser pour valider le projet ou le package.  
  
 **Runtime 32 bits**  
 Sélectionnez cette option afin d'utiliser un runtime 32 bits pour exécuter un package.  
  
 L'onglet **Paramètres** indique les valeurs de paramètres que vous utilisez pour valider le projet ou le package. Voici les options de l'onglet Paramètres.  
  
 **Conteneur**  
 Indique l'objet qui contient le paramètre.  
  
 **Paramètre**  
 Indique le nom des paramètres.  
  
 **Valeur**  
 Indique la valeur du paramètre.  
  
 L'onglet **Gestionnaires de connexions** indique les valeurs de propriétés du gestionnaire de connexions que vous utilisez pour valider le projet ou le package.  
  
 Voici les options de l'onglet **Gestionnaires de connexions** .  
  
 **Conteneur**  
 Indique l'objet qui contient le gestionnaire de connexions.  
  
 **Nom**  
 Indique le nom du gestionnaire de connexions.  
  
 **Nom de la propriété**  
 Indique le nom de la propriété du gestionnaire de connexions.  
  
 **Valeur**  
 Indique la valeur affectée à la propriété du gestionnaire de connexions.  
  
  
