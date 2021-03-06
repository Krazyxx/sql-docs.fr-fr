---
title: Boîte de dialogue Assembly de base de données (Analysis Services - données multidimensionnelles) Enregistrer | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidevstudio.assembly.registerassembly.f1
ms.assetid: 0c07cc87-fc94-456f-b878-7b23e39772b9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aad57083bdcd8337e9320e81a662bef12888011e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62748513"
---
# <a name="register-database-assembly-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Enregistrer l'assembly de base de données (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Enregistrer l'assembly de serveur** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour définir les propriétés d'une référence d'assembly dans une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Vous pouvez afficher la boîte de dialogue **Enregistrer l’assembly de serveur** en cliquant avec le bouton droit sur le dossier Assemblys d’une instance ou d’une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans **l’Explorateur d’objets** , puis en sélectionnant **Nouvel assembly**.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Type**|Sélectionnez le type de la référence d'assembly. Les valeurs suivantes sont disponibles :<br /><br /> **Assembly .NET.**: <br />                      La référence de l'assembly fait référence à un assembly [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework.<br /><br /> **DLL COM**: <br />                      La référence de l'assembly fait référence à une bibliothèque COM.<br /><br /> <br /><br /> **\*\* Note de sécurité \* \***  assemblys COM peuvent présenter un risque de sécurité. En raison de ce risque et d'autres considérations, les assemblys COM ont été déconseillés dans [!INCLUDE[ssASversion10](../includes/ssasversion10-md.md)]. Les assemblys COM peuvent ne pas être pris en charge dans les versions ultérieures.|  
|**Nom de fichier**|Tapez le chemin d'accès complet et le nom de fichier de l'assembly .NET ou de la bibliothèque COM.|  
|**...**|Cliquez sur ce bouton pour afficher la boîte de dialogue **Ouvrir** et sélectionner le chemin d'accès complet ainsi que le nom de fichier de l'assembly .NET ou de la bibliothèque COM.|  
|**Nom de l’assembly**|Tapez dans cette zone le nom de la référence de l'assembly.<br /><br /> Remarque : Modification de cette valeur ne modifie pas le nom de l’assembly référencé par la référence d’assembly, mais au lieu de cela modifie le nom utilisé le par le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance ou la base de données lorsque vous faites référence à la référence d’assembly.|  
|**Inclure les informations de débogage**|Sélectionnez cette option pour inclure les informations de débogage, le cas échéant, pour l'assembly .NET ou la bibliothèque COM.|  
|**Créer un horodateur**|Affiche la date et l'heure de création de la référence de l'assembly.|  
|**Dernière mise à jour du schéma**|Affiche la date et l'heure de la dernière mise à jour de la référence de l'assembly.|  
|**Source**|Affiche la source de la référence de l'assembly. Cette propriété contient généralement le chemin d'accès et le nom complets de l'assembly référencé par la référence de l'assembly.|  
|**Sécurisé**|Sélectionnez cette option pour utiliser ce paramètre d'autorisation pour la référence d'assembly. Si cette option est sélectionnée, seul un calcul interne et un accès local aux données sont autorisés à l'assembly. Le code exécuté par un assembly avec cette option ne peut pas accéder aux ressources système externes, tels que les fichiers, le réseau, les variables d'environnement ou le registre.<br /><br /> **\*\* Note de sécurité \* \***  cette option est le paramètre d’autorisation recommandé pour les assemblys qui effectuent des calculs et les données des tâches de gestion sans accès aux ressources en dehors de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Cette option représente le plus restrictif des paramètres d'autorisation.|  
|**Accès externe**|Sélectionnez cette option pour utiliser ce paramètre d'autorisation pour la référence d'assembly. Si cette option est sélectionnée, seul un calcul interne et un accès local aux données sont autorisés à l'assembly. Le code exécuté par un assembly avec ce paramètre d'autorisation peut accéder aux ressources système externes, tels que les fichiers, les réseaux, les variables d'environnement et le registre.<br /><br /> **\*\* Note de sécurité \* \***  cette option est recommandée pour les assemblys qui accèdent aux ressources en dehors de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Les assemblys utilisant cette option par défaut sont exécutées à l'aide des informations d'identification de sécurité du compte de service. Il est possible pour le code dans cet assembly peut explicitement emprunter l’identité de l’appelant [!INCLUDE[msCoName](../includes/msconame-md.md)] contexte de sécurité de l’authentification Windows. Étant donné que la valeur par défaut doit s'exécuter en tant que compte de service, l'autorisation d'exécuter les assemblys avec cette option ne devrait être donnée qu'aux rôles habilités à s'exécuter en tant que compte de service. Cette option représente un paramètre d'autorisation moins restrictif que la valeur **Sûr**. Ceci dit, elle est plus restrictive que la valeur **Illimité**.|  
|**Non restreint**|Sélectionnez cette option pour utiliser ce paramètre d'autorisation pour la référence d'assembly. Si cette option est sélectionnée, l'assembly dispose d'un accès illimité aux ressources, qu'elles soient internes ou externes. Le code exécuté à partir d'un assembly avec cette option peut appeler un code non managé.<br /><br /> **\*\* Note de sécurité \* \***  cette option n’est pas recommandée, sauf si l’assembly requiert un accès illimité. D'un point de vue de sécurité, cette option est identique à l' **accès externe**. Cependant, les assemblys utilisant l'option **Accès externe** fournissent diverses protections de fiabilité et de robustesse qui ne sont pas comprises dans les assemblys utilisant cette option. Si vous indiquez cette option, le code au sein de l'assembly peut effectuer des opérations illégales à l'encontre de l'espace de traitement. C'est ainsi que la robustesse et l'évolutivité de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]risquent d'être compromises. Cette option représente le plus restrictif des paramètres d'autorisation et doit être utilisée avec précaution.|  
|**Utiliser un nom d'utilisateur et un mot de passe spécifiques**|Sélectionnez cette option pour que l'objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] exploite les informations d'identification de sécurité d'un compte d'utilisateur spécifié.|  
|**Nom d'utilisateur**|Tapez le domaine et le nom du compte d'utilisateur que doit utiliser l'objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sélectionné. Le domaine et le nom de compte d'utilisateur utilisent le format suivant :<br /><br /> *\<Nom de domaine >* **\\**  *\<nom de compte d’utilisateur >*<br /><br /> Remarque : Cette option est activée si **Utiliser un nom d'utilisateur et un mot de passe spécifiques** est sélectionné.|  
|**Mot de passe**|Tapez le domaine et le nom du compte d'utilisateur que doit utiliser l'objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sélectionné.|  
|**Utiliser le compte de service**|Sélectionnez cette option pour que l'objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise les informations d'identification de sécurité associées au service [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui gère l'objet.|  
|**Utiliser les informations d'identification de l'utilisateur actuel**|Sélectionnez cette option pour que l'objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] exploite les informations d'identification de sécurité de l'utilisateur actuel.|  
|**Default**|Sélectionnez cette option pour utiliser le compte d'utilisateur par défaut pour [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La sélection de cette option revient à sélectionner l'option **Utiliser les informations d'identification de l'utilisateur actuel** .|  
|**Description**|Tapez dans cette zone la description de la référence d'assembly.|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Gestion des assemblys de modèles multidimensionnels](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
