---
title: Modifier les procédures stockées qui utilisent des propriétés de recherche en texte intégral obsolètes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- discontinued properties [Full-Text Search]
- stored procedures [Full-Text Search]
ms.assetid: 8d9392d9-a9ba-4378-84e4-59f516b67ddb
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1d6d7467da572d5d0552d400e2c05505c1bc0aaa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267562"
---
# <a name="modify-stored-procedures-that-use-discontinued-full-text-search-properties"></a>Modifier les procédures stockées qui utilisent des propriétés de recherche en texte intégral obsolètes
  Pour garantir le bon fonctionnement de vos procédures stockées, vous devez modifier les procédures existantes et supprimer les propriétés et les paramètres liées au texte intégral qui n'existent plus ou sont déconseillés.  
  
## <a name="component"></a>Composant  
 Recherche en texte intégral  
  
## <a name="description"></a>Description  
 Les propriétés et paramètres suivants associés à la recherche en texte intégral ont été supprimés.  
  
-   **DataTimeout**  
  
-   **ConnectTimeout**  
  
-   **Clean_up**  
  
-   **LogSize**  
  
 Les propriétés et paramètres suivants associés à la recherche en texte intégral ont été supprimés ou déconseillés.  
  
-   'Path' du catalogue de texte intégral. Le catalogue de texte intégral est un objet logique sans chemin d'accès de fichier spécifique dans le système.  
  
-   L'activation/désactivation de SP_FULLTEXT_DATABASE n'a plus aucun effet puisque les bases de données sont activées pour la recherche en texte intégral à tous moments et par défaut dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez vos procédures stockées de manière à supprimer ces propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
