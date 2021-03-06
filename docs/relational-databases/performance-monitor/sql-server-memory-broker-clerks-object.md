---
title: SQL Server, objet Memory Broker Clerks | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: e2ae02cd83f99c43f844bdae8da8b7b9860a7769
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380820"
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQL Server, objet Memory Broker Clerks
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
L’objet de performance **SQLServer:Memory Broker Clerks** fournit des compteurs pour les statistiques relatives aux régisseurs de gestionnaire d’allocation de mémoire.

Le tableau suivant décrit les objets de performance **Memory Broker Clerks** SQL Server.

|**Compteurs du régisseur de gestionnaire d’allocation de mémoire SQL Server**|Description|  
|-------------|-----------------|  
|**Avantage interne**|Quantité interne de mémoire pour la sollicitation du nombre d’entrées, en millisecondes par page par milliseconde, multipliée par 10 milliards et tronquée en entier.|
|**Taille du régisseur de gestionnaire d’allocation de mémoire**|Taille du régisseur, en pages.|
|**Évictions périodiques (pages)**|Nombre de pages évincées du régisseur de gestionnaire d’allocation de mémoire par la dernière éviction périodique.|
|**Évictions de pression (pages/s)**|Nombre de pages par seconde évincées du régisseur de gestionnaire d’allocation de mémoire par sollicitation de la mémoire.|
|**Avantages de simulation**|Quantité de mémoire pour le régisseur, en millisecondes par page par milliseconde, multipliée par 10 milliards et tronquée en entier.|
|**Taille de simulation**|Taille actuelle de la simulation du régisseur, en pages.|

Il existe une instance du compteur pour le pool de mémoires tampons et le pool d’objets de banque de colonnes.

## <a name="see-also"></a> Voir aussi  
[Analyser l'utilisation des ressources (Moniteur système)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
