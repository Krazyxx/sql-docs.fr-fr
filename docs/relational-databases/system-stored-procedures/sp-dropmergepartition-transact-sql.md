---
title: sp_dropmergepartition (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergepartition_TSQL
- sp_dropmergepartition
helpviewer_keywords:
- sp_dropmergepartition
ms.assetid: 1be511c1-79ff-4947-9379-78d83b7b8945
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74837390afe358d4f9a12d4f98ea9d2e4166e146
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536091"
---
# <a name="spdropmergepartition-transact-sql"></a>sp_dropmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Supprime une partition d'un filtre de lignes paramétré d'une publication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication. Elle supprime également le travail d'instantané correspondant et les fichiers d'instantané de la partition.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication] = 'publication'` Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @suser_sname = ] 'suser_sname'` Est la valeur de la [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) fonction sur l’abonné est utilisée pour définir la partition. *SUSER_SNAME* est **sysname**, sans valeur par défaut.  
  
`[ @host_name = ] 'host_name'` Est la valeur de la [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) fonction sur l’abonné est utilisée pour définir la partition. *HOST_NAME* est **sysname**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropmergepublication** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_dropmergepublication**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les partitions d’une publication de fusion avec des filtres paramétrables](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
  
