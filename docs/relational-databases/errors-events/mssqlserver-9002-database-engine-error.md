---
title: MSSQLSERVER_9002 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 757dabfc59775ac407dd5d1ceece2d067d32eacd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47761597"
---
# <a name="mssqlserver9002"></a>MSSQLSERVER_9002
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9002|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOG_IS_FULL|  
|Texte du message|Le journal des transactions de la base de données '%.*ls' est plein. Pour savoir pourquoi il est impossible de réutiliser de l'espace dans le journal, consultez la colonne log_reuse_wait_desc dans sys.databases.|  
  
## <a name="explanation"></a>Explication  
Le journal de la base de données est saturé. La colonne **log_reuse_wait_desc** dans **sys.databases** explique pourquoi il est impossible de réutiliser l’espace dans le journal.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Utilisez **sys.databases** pour comprendre pourquoi le journal est plein, puis corrigez la condition. Pour plus d’informations, consultez « Résolution des problèmes en cas de journal des transactions saturé (erreur 9002) » dans la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a> Voir aussi  
[Résoudre les problèmes liés à un journal des transactions saturé &#40;erreur SQL Server 9002&#41;](~/relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
[sys.databases &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
