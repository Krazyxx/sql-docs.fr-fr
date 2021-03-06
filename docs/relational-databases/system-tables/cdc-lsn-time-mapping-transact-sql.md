---
title: cdc.lsn_time_mapping (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.lsn_time_mapping
- cdc.lsn_time_mapping_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.lsn_time_mapping
ms.assetid: 1cb7aedc-48a4-486e-9b91-d30c4bd4084e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3118a814d18013a4360dd9afdcd1e09dcc483545
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62471110"
---
# <a name="cdclsntimemapping-transact-sql"></a>cdc.lsn_time_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque transaction qui a des lignes dans une table de modifications. Cette table est utilisée pour le mappage entre les valeurs de validation du numéro séquentiel dans le journal et l'heure de validation de la transaction. Des entrées pour lesquelles il n'existe pas d'entrées de tables de modifications peuvent également être enregistrées. Cela permet à la table d'enregistrer l'exécution du traitement du numéro séquentiel dans le journal à des moments où l'activité de changement est faible ou nulle.  
  
 Nous vous recommandons de ne pas interroger les tables système directement. À la place, exécutez le [sys.fn_cdc_map_lsn_to_time &#40;Transact-SQL&#41; ](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md) et [sys.fn_cdc_map_time_to_lsn &#40;Transact-SQL&#41; ](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md) fonctions système.  
    
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**start_lsn**|**binary(10)**|Numéro séquentiel dans le journal de la transaction validée.|  
|**tran_begin_time**|**datetime**|Heure de début de la transaction associée au numéro séquentiel dans le journal.|  
|**tran_end_time**|**datetime**|Heure de fin de la transaction|  
|**tran_id**|**varbinary(10)**|ID de la transaction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Journal des transactions &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [cdc.&#60;capture_instance&#62;_CT &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
  
  
