---
title: Mot clé réservé de suivant de deux-points Remove | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- reserved keywords
ms.assetid: 4f23f7e4-7b4d-4e19-86c9-7527bb8b107d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6f68a641caf21e6cc1dfdefbcb31ff78a1fd8aa6
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583032"
---
# <a name="remove-colon-following-reserved-keyword"></a>Supprimer le signe deux-points qui suit le mot clé réservé
  Le Conseiller de mise à niveau a détecté un script dans lequel un signe deux-points (:) suit un mot clé réservé. Dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette syntaxe est ignorée et les instructions s'y exécutent correctement. Cette syntaxe provoque l'échec de l'instruction lorsque le mode de compatibilité de la base de données est défini à 100 ou supérieur.  
  
 Les bases de données utilisateur conservent leur mode de compatibilité.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Avant de définir le mode de compatibilité de la base de données à 100 ou ultérieur, modifiez vos scripts en supprimant les signes deux-points qui suivent des mots clés réservé. Pour plus d'informations, consultez « sp_dbcmptlevel » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
