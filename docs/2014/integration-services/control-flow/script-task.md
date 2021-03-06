---
title: Script, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.f1
helpviewer_keywords:
- scripts [Integration Services], tasks
- Script task [Integration Services], about Script task
- Script task [Integration Services]
ms.assetid: f6cce7df-4bd6-4b75-9f89-6c37b4bb5558
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7c710065bf0a87b5ec3850010344f2ef5114022e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830560"
---
# <a name="script-task"></a>Tâche de script
  La tâche de script fournit du code permettant d’exécuter des fonctions qui ne sont pas disponibles dans les tâches et transformations intégrées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . La tâche de script peut également combiner des fonctions dans un même script au lieu d'utiliser plusieurs tâches et transformations. Utilisez la tâche de script pour le travail devant être effectué une fois dans un package (ou une fois par objet énuméré), et non une fois par ligne de données.  
  
 Vous pouvez utiliser la tâche de script aux fins suivantes :  
  
-   Accéder aux données à l'aide d'autres technologies non prises en charge par les types de connexion intégrés. Par exemple, un script peut utiliser des interfaces ADSI (Active Directory Service Interfaces) pour accéder aux noms d'utilisateur et les extraire d'Active Directory.  
  
-   Créer un compteur de performances spécifique au package. Par exemple, un script peut créer un compteur de performances mis à jour pendant l'exécution d'une tâche complexe ou peu performante.  
  
-   Déterminez si les fichiers spécifiés sont vides ou combien de lignes ils contiennent, puis en fonction de ces informations, affectez le flux de contrôle dans un package. Par exemple, si un fichier ne contient aucune ligne, la valeur 0 d'une variable et une contrainte de précédence qui évalue la valeur empêchent une tâche de système de fichiers de copier le fichier.  
  
 Si vous devez utiliser le script afin d'effectuer le même travail pour chaque ligne de données d'un ensemble, vous devriez utiliser le composant Script à la place de la tâche de script. Par exemple, si vous souhaitez évaluer un montant de frais de port raisonnable et ignorer les lignes de données présentant des montants extrêmement élevés ou bas, il convient d'utiliser un composant Script. Pour plus d’informations, voir [Script Component](../data-flow/transformations/script-component.md).  
  
 Si plusieurs packages utilisent un script, envisagez l'écriture d'une tâche personnalisée plutôt que de recourir à la tâche de script. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
 Si vous choisissez la tâche de script pour votre package, vous devez développer le script utilisé par la tâche et configurer cette dernière.  
  
## <a name="writing-and-running-the-script-that-the-task-uses"></a>Écriture et exécution du script utilisé par la tâche  
 La tâche de script utilise [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) en tant qu’environnement d’écriture des scripts et que moteur d’exécution de ces derniers.  
  
 VSTA fournit l’ensemble des fonctionnalités standard de l’environnement [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , telles que l’éditeur [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] à code de couleur, IntelliSense et **l’Explorateur d’objets**. VSTA utilise également le même débogueur que les autres outils de développement [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Les points d'arrêt dans le script fonctionnent de façon transparente avec ceux des tâches et des conteneurs [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . VSTA prend en charge les langages de programmation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Vous ne pouvez lancer un script que si VSTA est installé sur l'ordinateur où le package est exécuté. Lorsque le package s'exécute, la tâche charge le moteur de script puis exécute le script. Vous pouvez accéder aux assemblys .NET externes dans les scripts en ajoutant des références aux assemblys du projet.  
  
> [!NOTE]  
>  Contrairement aux versions antérieures pour lesquelles il était possible d’indiquer si les scripts étaient précompilés, tous les scripts de [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] et des versions ultérieures sont précompilés. Lorsqu'un script est précompilé, le moteur de langage n'est pas chargé au moment de l'exécution et le package s'exécute plus rapidement. Toutefois, les fichiers binaires précompilés occupent un espace disque important.  
  
## <a name="configuring-the-script-task"></a>Configuration de la tâche de script  
 Vous pouvez configurer la tâche de script comme suit :  
  
-   Fournissez le script personnalisé que la tâche exécute.  
  
-   Spécifiez la méthode dans le projet VSTA utilisée au moment de l’exécution de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] comme point d’entrée du code de tâche de script.  
  
-   Spécifiez le langage de script  
  
-   Éventuellement, fournissez les listes des variables en lecture seule et en lecture/écriture à utiliser dans le script.  
  
 Vous pouvez définir ces propriétés via le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programme.  
  
### <a name="configuring-the-script-task-in-the-designer"></a>Configuration de la tâche de script dans le concepteur  
 Le tableau suivant décrit l'événement `ScriptTaskLogEntry` pouvant être consigné pour la tâche de script. Le `ScriptTaskLogEntry` événement est sélectionné pour la journalisation le **détails** onglet de la **configurer les journaux SSIS** boîte de dialogue. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|Indique les résultats de l'implémentation de la journalisation dans le script. La tâche écrit une entrée de journal pour chaque appel de la méthode `Log` de l'objet `Dts`. La tâche écrit ces entrées lorsque le code est exécuté. Pour plus d’informations, consultez [Journalisation dans la tâche de script](../extending-packages-scripting/task/logging-in-the-script-task.md).|  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez les rubriques suivantes :  
  
-   [Éditeur de tâche de script &#40;page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur de tâche de script &#40;page Script&#41;](../script-task-editor-script-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d’informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="configuring-the-script-task-programmatically"></a>Configuration par programme de la tâche de script  
 Pour plus d’informations sur la définition par programmation de ces propriétés, consultez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask>  
  
## <a name="related-content"></a>Contenu associé  
  
-   Article technique [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625)(Procédure d’envoi d’e-mail avec notification de remise en C#) sur shareourideas.com  
  
  
