---
title: nchar et nvarchar (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nvarchar data type
- nchar data type
ms.assetid: 81ee5637-ee31-4c4d-96d0-56c26a742354
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ee44e6c7a4ff8befc21b461feab44a07a8658a2f
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51696727"
---
# <a name="nchar-and-nvarchar-transact-sql"></a>nchar et nvarchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Les types de données de caractères qui sont soit de longueur fixe, **nchar**, soit de longueur variable, **nvarchar**. À partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], quand un classement prenant en charge les [caractères supplémentaires (SC)](../../relational-databases/collations/collation-and-unicode-support.md#Supplementary_Characters) est utilisé, ces types de données stockent la plage complète des données caractères [Unicode](../../relational-databases/collations/collation-and-unicode-support.md#Unicode_Defn) et utilisent le codage de caractères [UTF-16 ](https://www.wikipedia.org/wiki/UTF-16). Si un classement autre que SC est spécifié, ces types de données stockent uniquement le sous-ensemble de données caractères pris en charge par le codage de caractères [UCS-2](https://www.wikipedia.org/wiki/Universal_Coded_Character_Set#Encoding_forms).
  
## <a name="arguments"></a>Arguments  
**nchar** [ ( n ) ]  
Données de type chaîne de longueur fixe. *n* définit la longueur de chaîne en paires d’octets et doit être une valeur comprise entre 1 et 4 000. La taille de stockage est le double de *n* octets. Pour l'encodage [UCS-2](https://www.wikipedia.org/wiki/UTF-16#U+0000_to_U+D7FF_and_U+E000_to_U+FFFF), la taille de stockage est deux fois *n* octets et le nombre de caractères pouvant être stockés est également *n*. Pour l'encodage UTF-16, la taille de stockage est toujours deux fois *n* octets, mais le nombre de caractères pouvant être stockés peut être inférieur à *n*, car les caractères supplémentaires utilisent deux paires d'octets (également appelées [paires de remplacement](https://www.wikipedia.org/wiki/UTF-16#U+010000_to_U+10FFFF)). Les synonymes ISO de **nchar** sont **national char** et **national character**.
  
**nvarchar** [ ( n | **max** ) ]  
Données de type chaîne de longueur variable. *n* définit la longueur de chaîne en paires d’octets et peut être une valeur comprise entre 1 et 4 000. **max** indique que la taille de stockage maximale est de 2^30-1 caractères (2 Go). La taille de stockage est deux fois *n* octets + 2 octets. Pour l'encodage [UCS-2](https://www.wikipedia.org/wiki/UTF-16#U+0000_to_U+D7FF_and_U+E000_to_U+FFFF), la taille de stockage est deux fois *n* octets + 2 octests et le nombre de caractères pouvant être stockés est également *n*. Pour l'encodage UTF-16, la taille de stockage est toujours deux fois *n* octets + 2 octets, mais le nombre de caractères pouvant être stockés peut être inférieur à *n*, car les caractères supplémentaires utilisent deux paires d'octets (également appelées [paires de remplacement](https://www.wikipedia.org/wiki/UTF-16#U+010000_to_U+10FFFF)). Les synonymes ISO de **nvarchar** sont **national char varying** et **national character varying**.
  
## <a name="remarks"></a>Notes   
Quand la valeur de *n* n’est spécifiée ni dans une définition de données ni dans une instruction de déclaration de variable, la longueur par défaut est 1. Quand la valeur de *n* n’est pas précisée avec la fonction CAST, la longueur par défaut est 30.

Si vous utilisez **nchar** ou **nvarchar**, nous vous recommandons de procéder comme suit :
- Utilisez **nchar** quand les tailles des entrées de données de la colonne sont cohérentes.  
- Utilisez **nvarchar** quand les tailles des entrées de données de la colonne varient considérablement.  
- Utilisez **nvarchar(max)** quand les tailles des entrées de données de la colonne varient considérablement et que la longueur de chaîne peut dépasser 4 000 paires d’octets.  
  
**sysname** est un type de données défini par l’utilisateur fourni par le système qui présente la même fonctionnalité que **nvarchar(128)**, à la différence qu’il n’accepte pas la valeur Null. **sysname** est utilisé pour faire référence aux noms des objets de base de données.
  
Les objets qui utilisent **nchar** ou **nvarchar** reçoivent le classement par défaut de la base de données, sauf si un classement spécifique est affecté à l’aide de la clause COLLATE.
  
SET ANSI_PADDING a toujours la valeur ON pour **nchar** et **nvarchar**. SET ANSI_PADDING OFF ne s’applique pas aux types de données **nchar** ni **nvarchar**.
  
Préfixer une constante de chaîne de caractères Unicode avec la lettre N pour signaler une entrée UCS-2 ou UTF-16, selon qu'un classement SC est utilisé ou non. Sans le préfixe N, la chaîne est convertie en page de codes par défaut de la base de données et ne reconnaîtra peut-être pas certains caractères. En commençant par [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)], lorsqu’un classement prenant en charge UTF-8 est utilisé, la page de codes par défaut est capable de stocker le jeu de caractères UNICODE UTF-8. 
 
> [!NOTE]  
> Lorsque vous préfixez une constante de chaîne avec la lettre N, la conversion implicite donnera une chaîne UCS-2 ou UTF-16 si la constante à convertir ne dépasse pas la longueur maximale pour le type de données de chaîne nvarchar (4 000). Sinon, la conversion implicite génère un nvarchar(max) de valeur élevée.
  
> [!WARNING]  
> Chaque colonne **varchar(max)** ou **nvarchar(max)** non Null demande 24 octets d’allocation fixe supplémentaire calculée par rapport à la limite de 8 060 octets par ligne pendant une opération de tri. Ces octets supplémentaires peuvent produire une limite implicite du nombre de colonnes **varchar(max)** ou **nvarchar(max)** non Null dans une table. Aucune erreur spéciale n'est fournie quand la table est créée (mis à part l’avertissement habituel indiquant que la taille maximale de ligne dépasse la taille maximale autorisée de 8 060 octets) ou quand les données sont insérées. Cette grande taille de ligne peut provoquer des erreurs (comme l’erreur 512) que les utilisateurs peuvent ne pas anticiper au cours d’opérations normales.  Deux exemples d’opérations sont la mise à jour d’une clé d’index cluster ou le tri de l’intégralité du jeu de colonnes.
  
## <a name="converting-character-data"></a>Conversion des données de type caractère  
Pour plus d’informations sur la conversion de données caractères, consultez [char et varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md).
  
## <a name="see-also"></a>Voir aussi
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)  
[SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)    
[Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)     
[Jeux de caractères codés sur un octet et multioctets](/cpp/c-runtime-library/single-byte-and-multibyte-character-sets)  
  
