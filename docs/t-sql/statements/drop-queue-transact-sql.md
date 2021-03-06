---
title: DROP QUEUE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP QUEUE
- DROP_QUEUE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dropping queues
- queues [Service Broker], removing
- deleting queues
- DROP QUEUE statement
- removing queues
ms.assetid: fd866520-ca00-477d-b2e9-0110e9610ed4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 297ef4c06b88d02e3c1a28829c7223d49c8ecee6
ms.sourcegitcommit: e4794943ea6d2580174d42275185e58166984f8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65503715"
---
# <a name="drop-queue-transact-sql"></a>DROP QUEUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime une file d'attente existante.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP QUEUE <object>  
[ ; ]  
  
<object> ::=  
{ database_name.schema_name.queue_name | schema_name.queue_name | queue_name }
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Nom de la base de données qui contient la file d'attente à supprimer. Quand aucun argument *database_name* n’est fourni, la base de données active est utilisée par défaut.  
  
 *schema_name (object)*  
 Nom du schéma auquel appartient la file d'attente à supprimer. Quand aucun argument *schema_name* n’est fourni, le schéma par défaut de l’utilisateur actif est utilisé par défaut.  
  
 *queue_name*  
 Nom de la file d'attente à supprimer.  
  
## <a name="remarks"></a>Notes   
 Il est impossible de supprimer une file d'attente si un service y fait référence.  
  
## <a name="permissions"></a>Autorisations  
 L’autorisation de supprimer une file d’attente est accordée par défaut à son propriétaire, aux membres des rôles de base de données fixes **db_ddladmin** ou **db_owner** et aux membres du rôle serveur fixe **sysadmin**.  
  
## <a name="examples"></a>Exemples  
 Dans l’exemple ci-dessous, la file d’attente **ExpenseQueue** est supprimée de la base de données active.  
  
```  
DROP QUEUE ExpenseQueue ;  
  
```  
  
## <a name="see-also"></a> Voir aussi  
 [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md)   
 [ALTER QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-queue-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
