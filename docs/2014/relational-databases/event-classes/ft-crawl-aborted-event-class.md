---
title: FT:Crawl Aborted, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Crawl Aborted event class
ms.assetid: eead8ea6-5051-4689-ab30-4dfbfda01fb9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ba7914456e4ffcf19a52c6e7f7206a390147cc2f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62662422"
---
# <a name="ftcrawl-aborted-event-class"></a>FT:Crawl Aborted, classe d'événements
  La classe d’événements **FT:Crawl Aborted** indique qu’une exception s’est produite au cours d’une analyse de texte intégral. Cette erreur entraîne généralement l'arrêt de l'analyse de texte intégral. Pour plus de détails sur l'erreur, consultez le journal des événements [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ou le journal d'analyse.  
  
## <a name="ftcrawl-aborted-event-class-data-columns"></a>Colonnes de données de la classe d'événements FT:Crawl Aborted  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**Int**|ID de la base de données dans laquelle l'analyse de texte intégral est exécutée. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**Erreur**|**Int**|Numéro d'erreur d'un événement donné. Il s’agit généralement du numéro d’erreur stocké dans la table **sysmessages** .|31|Oui|  
|**EventClass**|**Int**|Type d’événement = 157.|27|Non|  
|**EventSequence**|**Int**|Séquence d'un événement donné au sein de la demande.|51|Non|  
|**IsSystem**|**Int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**ObjectID**|**Int**|ID attribué par le système à l'objet sur lequel l'analyse de texte intégral était exécutée lorsque l'échec a eu lieu.|22|Oui|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**Int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**État**|**Int**|Équivalent à un code d'état d'erreur.|30|Oui|  
|**TransactionID**|**bigint**|ID affecté par le système à la transaction.|4|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
