---
title: Charger en masse des données dans les tables d’une publication de fusion | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cc2ab453279e429f148f257f75f44f26c4e57287
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47781737"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication"></a>Charger en masse des données dans les tables d’une publication de fusion
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Lorsque les données sont chargées dans des tables à l'aide des [bcp Utility](../../tools/bcp-utility.md) ou de la commande [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) , par défaut, les déclencheurs de réplication de fusion qui conservent les données de suivi dans la table système [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) ne sont pas déclenchés. Vous avez le choix entre forcer les déclencheurs de réplication de fusion à se déclencher au chargement des données et insérer par programmation les métadonnées de réplication générées après l'opération de copie en bloc à l'aide de procédures stockées de réplication.  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a>Pour charger en masse les données dans les tables publiées par la réplication de fusion à l'aide de l'utilitaire bcp  
  
1.  Sur le serveur de publication ou sur l'Abonné, exécutez l' [bcp Utility](../../tools/bcp-utility.md) ou [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) pour insérer des données dans une table a publié à l'aide de la réplication de fusion.  
  
2.  Utilisez l'une des méthodes suivantes pour garantir que les métadonnées de réplication sont générées pour les données insérées.  
  
    -   Exécutez la copie en bloc à l'aide de l'option FIRE_TRIGGERS.  
  
    -   Dans la base de données dans laquelle les données ont été insérées, exécutez [sp_addtabletocontents &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql.md). Spécifiez le nom de la table dans laquelle les données ont été insérées pour **@table_name**.  
  
  
