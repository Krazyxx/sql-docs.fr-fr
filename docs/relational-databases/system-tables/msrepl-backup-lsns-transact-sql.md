---
title: MSrepl_backup_lsns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_backup_lsns_TSQL
- MSrepl_backup_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_backup_Isns system table
ms.assetid: de06c349-82a8-48c6-b602-b5d6938514f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b35c095b2c00b4293062086b9a79f92b1fb4e77b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52757911"
---
# <a name="msreplbackuplsns-transact-sql"></a>MSrepl_backup_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSrepl_backup_lsns** table contient des numéros de séquence de journaux de transaction (LSN) pour prendre en charge l’option 'sync with backup' de la base de données de Distribution. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**Int**|Identificateur de la base de données du serveur de publication.|  
|**valid_xact_id**|**varbinary(16)**|ID de la transaction à envoyer au serveur de publication pour marquer le point de troncature du journal. Utilisé uniquement si la base de données de Distribution est en mode de « sync with backup ». Contient l'ID de la dernière transaction répliquée dans la base de données de distribution qui a été sauvegardée. L'ID est envoyé au serveur de publication pour que le lecteur de journal marque le point de troncature du journal.|  
|**valid_xact_seqno**|**varbinary(16)**|Numéro de séquence de la transaction à envoyer au serveur de publication pour marquer le point de troncature du journal. Utilisé seulement si la base de données de distribution est en mode 'sync with backup'. Il s'agit du numéro séquentiel dans le journal de la dernière transaction de réplication dans la base de données de distribution qui a été sauvegardée. L'ID est envoyé au serveur de publication pour que le lecteur de journal marque le point de troncature du journal.|  
|**next_xact_id**|**varbinary(16)**|Numéro séquentiel dans le journal temporaire utilisé par les opérations de sauvegarde.|  
|**nextx_xact_seqno**|**varbinary(16)**|Numéro séquentiel dans le journal temporaire utilisé par les opérations de sauvegarde.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
