---
title: Option status (outil d’administration Distributed Replay) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 09e8ad6b60dfc9afbb3fbed7ef450dc4fb1cc28a
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589203"
---
# <a name="status-option-distributed-replay-administration-tool"></a>Option status (outil d'administration Distributed Replay)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L’outil d’administration [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay (**DReplay.exe**) est un outil en ligne de commande qui permet de communiquer avec Distributed Replay Controller. Cette rubrique décrit l’option de ligne de commande **status** et la syntaxe correspondante.  
  
 L'option **status** interroge le contrôleur et affiche l'état en cours.  
  
 ![Icône de lien vers une rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône de lien vers une rubrique") Pour plus d’informations sur les conventions de syntaxe utilisées par l’outil d’administration, consultez [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dreplay status [-m controller] [-f status_interval]  
```  
  
#### <a name="parameters"></a>Paramètres  
 **-m** _controller_  
 Spécifie le nom de l'ordinateur du contrôleur. Vous pouvez utiliser «`localhost`» ou «`.`» pour désigner l'ordinateur local.  
  
 Si le paramètre **-m** n’est pas spécifié, l’ordinateur local est utilisé.  
  
 **-f** _status_interval_  
 Spécifie la fréquence (en secondes) à laquelle afficher l'état.  
  
 Si le paramètre **-f** n’est pas spécifié, l’intervalle par défaut est de 30 secondes.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, l'état en cours est affiché toutes les 60 secondes. La valeur `localhost` indique que le service contrôleur s'exécute sur le même ordinateur que l'outil d'administration.  
  
```  
dreplay status -m localhost -f 60  
```  
  
## <a name="permissions"></a>Permissions  
 Vous devez exécuter l'outil d'administration en tant qu'utilisateur interactif, comme un utilisateur local ou un compte d'utilisateur de domaine. Pour utiliser un compte d'utilisateur local, l'outil d'administration et le contrôleur doivent s'exécuter sur le même ordinateur.  
  
 Pour plus d’informations, voir [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## <a name="see-also"></a> Voir aussi  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)   
 [Débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)  
  
  
