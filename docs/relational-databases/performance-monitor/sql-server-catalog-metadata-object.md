---
title: SQL Server, objet Catalog Metadata | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: c7e3e4632141040f791b6b83640c5261017726c6
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380787"
---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, objet Catalog Metadata
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
L’objet de performance **SQLServer:Catalog Metadata** fournit des compteurs pour les métadonnées de catalogue pour SQL Server.

Le tableau suivant décrit les objets de performance **Métadonnées de catalogue** SQL Server.


|**Compteurs de métadonnées de catalogue SQLServer**|Description|  
|-------------|-----------------|  
|**Nombre d’entrées de cache**|Nombre d’entrées dans le cache de métadonnées de catalogue.|
|**Nombre d’entrées de cache épinglées**|Nombre d’entrées épinglées du cache de métadonnées de catalogue.|
|**Taux d'accès au cache**|Rapport entre les accès au cache de métadonnées de catalogue et les recherches.|
|**Base du taux d’accès au cache**|À usage interne uniquement|

Il existe une instance du compteur pour chaque base de données.

## <a name="see-also"></a> Voir aussi  
[Analyser l'utilisation des ressources (Moniteur système)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
