---
title: Administrateur d’E/S SQL Server XTP | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 4f849d6c282fda16709b556131e44dd1ce9cd5ce
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380190"
---
# <a name="sql-server-xtp-io-governor"></a>Administrateur d’E/S SQL Server XTP
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’objet de performances Administrateur d’E/S SQL Server XTP contient des compteurs liés à l’Administrateur de taux d’E/S OLTP en mémoire.

Ce tableau décrit les compteurs **Administrateur d’E/S SQL Server XTP** .

|Compteur|Description|  
|-------------|-----------------|  
|**Attentes de crédits insuffisants/s**|Nombre d’attentes en raison de crédits insuffisants dans les objets de taux (par seconde).|
|**E/S émises/s**|Nombre d’E/S émises par seconde par les threads de vidage.|
|**Blocs de journal/s**|Nombre de blocs de journal traités par le contrôleur par seconde.|
|**Emplacements de crédit manqués**|Nombre d’emplacements de crédit manqués en raison de l’attente de crédits à partir de l’objet de taux.|
|**Taux des attentes d’objets périmés/s**|Nombre d’attentes en raison d’objets périmés (par seconde).|
|**Proportion totale d’objets publiés**|Nombre total de proportions d’objets publiés.|
 

## <a name="see-also"></a> Voir aussi  
[SQL Server XTP &#40;OLTP en mémoire&#41;, compteurs de performances](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
