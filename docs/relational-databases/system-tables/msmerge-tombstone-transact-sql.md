---
title: MSmerge_tombstone (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_tombstone_TSQL
- MSmerge_tombstone
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_tombstone system table
ms.assetid: 8b3fc7bf-729b-40f2-8a26-e7dfbe8ddb38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab57e69118edfe4a647d6baeedf5a10ee8460247
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026464"
---
# <a name="msmergetombstone-transact-sql"></a>MSmerge_tombstone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_tombstone** table contient des informations sur les lignes supprimées et permet des suppressions soient propagées aux autres abonnés. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**rowguid**|**uniqueidentifier**|Identificateur de ligne.|  
|**tablenick**|**Int**|Surnom de la table.|  
|**type**|**tinyint**|Type de suppression :<br /><br /> 1 = suppression de l'utilisateur<br /><br /> 5 = exclusion de la ligne de la partition filtrée<br /><br /> 6 = suppression par le système|  
|**lineage**|**varbinary(249)**|Indique la version de l'enregistrement objet de la suppression, ainsi que les mises à jour connues lors de la suppression. Permet d'obtenir la résolution cohérente d'un conflit lorsqu'un abonné modifie une ligne alors qu'un autre abonné est en train de la supprimer.|  
|**generation**|**Int**|Est affecté lors de la suppression d'une ligne. Si un abonné demande la génération N, seules les informations résiduelles de génération > = N sont envoyées.|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Identifie l'enregistrement logique auquel une ligne supprimée appartient.|  
|**logical_record_lineage**|**Varbinary(501)**|Paires nom de l'Abonné/numéro de version permettant de gérer un historique des suppressions pour l'enregistrement logique auquel cette ligne appartient.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
