---
title: sys.dm_pdw_nodes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a5df628a6b37c8d89843506c5b7f4c5050157158
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027391"
---
# <a name="sysdmpdwnodes-transact-sql"></a>sys.dm_pdw_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur tous les nœuds dans [!INCLUDE[ssAPS](../../includes/ssaps-md.md)]. Elle répertorie une ligne par nœud dans l’appliance.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**Int**|Id numérique unique associé au nœud.<br /><br /> Clé pour cette vue.|Unique sur l’appliance, quel que soit le type.|  
|Type|**nvarchar(32)**|Type du nœud.|'COMPUTE', 'CONTROL',  'MANAGEMENT'|  
|NAME|**nvarchar(32)**|Nom logique du nœud.|N’importe quelle chaîne de longueur appropriée.|  
|address|**nvarchar(32)**|Adresse IP de ce nœud.|Dans le format [0-255]. 0-255. 0-255. 0-255.|  
|is_passive|**Int**|Indique si la machine virtuelle en cours d’exécution du nœud est en cours d’exécution sur le serveur affecté ou qu’il a basculé vers le serveur de secours.|0 - machine virtuelle du nœud est en cours d’exécution sur le serveur d’origine.<br /><br /> 1 - machine virtuelle du nœud est en cours d’exécution sur le serveur de secours.|  
|région|**nvarchar(32)**|La région où le nœud est en cours d’exécution.|'PDW', 'HDINSIGHT'|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
