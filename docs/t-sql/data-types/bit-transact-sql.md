---
title: bit (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- bit_TSQL
- bit
dev_langs:
- TSQL
helpviewer_keywords:
- bit data type
ms.assetid: 40adfd08-a31c-49cb-a172-386bcaa6edee
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4e5cbc79ec84b4349ad5a906b30f008a1f5b5490
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56009520"
---
# <a name="bit-transact-sql"></a>bit (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Données de type entier qui peuvent prendre la valeur 1, 0 ou NULL.  
  
## <a name="remarks"></a>Notes   
Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] optimise le stockage des colonnes de **bit**. Si une table contient 8 colonnes de **bits** ou moins, celles-ci sont stockées comme 1 octet. S’il y a entre 9 et 16 colonnes de **bit**, elles sont stockées sous la forme de 2 octets, etc.
  
Les valeurs de chaîne TRUE et FALSE peuvent être converties en valeurs de **bit** : TRUE est convertie en 1 et FALSE est convertie en 0.
  
Lors d'une conversion en bit, toute valeur différente de zéro est changée en 1.
  
## <a name="see-also"></a>Voir aussi
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Conversion de type de données &#40;moteur de base de données&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  
