---
title: ALTER EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL LIBRARY
author: dphansen
ms.author: davidph
manager: cgronlund
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 33270c8ccc490a400db45b6525d8c6002d974f3a
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583172"
---
# <a name="alter-external-library-transact-sql"></a>ALTER EXTERNAL LIBRARY (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Modifie le contenu d’une bibliothèque de package externe existante.

> [!NOTE]
> Dans SQL Server 2017, le langage R et la plateforme Windows sont pris en charge. R, Python et Java sur les plateformes Windows et Linux sont pris en charge dans SQL Server 2019 CTP 2.4. 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
## <a name="syntax-for-sql-server-2019"></a>Syntaxe pour SQL Server 2019

```text
ALTER EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ]
SET <file_spec>
WITH ( LANGUAGE = <language> )
[ ; ]

<file_spec> ::=
{
    (CONTENT = { <client_library_specifier> | <library_bits> | NONE}
    [, PLATFORM = <platform> )
}

<client_library_specifier> :: =
{
      '[\\computer_name\]share_name\[path\]manifest_file_name'
    | '[local_path\]manifest_file_name'
    | '<relative_path_in_external_data_source>'
}

<library_bits> :: =
{ 
      varbinary_literal 
    | varbinary_expression 
}

<platform> :: = 
{
      WINDOWS
    | LINUX
}

<language> :: = 
{
      'R'
    | 'Python'
    | 'Java'
}
```
::: moniker-end
::: moniker range=">=sql-server-2017 <=sql-server-2017||=sqlallproducts-allversions"
## <a name="syntax-for-sql-server-2017"></a>Syntaxe pour SQL Server 2017

```text
ALTER EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ]
SET <file_spec>
WITH ( LANGUAGE = 'R' )
[ ; ]

<file_spec> ::=
{
    (CONTENT = { <client_library_specifier> | <library_bits> | NONE}
    [, PLATFORM = WINDOWS )
}

<client_library_specifier> :: =
{
      '[\\computer_name\]share_name\[path\]manifest_file_name'
    | '[local_path\]manifest_file_name'
    | '<relative_path_in_external_data_source>'
}

<library_bits> :: =
{ 
      varbinary_literal 
    | varbinary_expression 
}
```
::: moniker-end

### <a name="arguments"></a>Arguments

**library_name**

Spécifie le nom d’une bibliothèque de package existante. Les bibliothèques sont limitées à l’utilisateur. Les noms de bibliothèques doivent être uniques dans le contexte d’un utilisateur ou d’un propriétaire donné.

Le nom de la bibliothèque ne peut pas être assigné arbitrairement. Autrement dit, vous devez utiliser le nom que le runtime appelant attend quand il charge le package.

**owner_name**

Spécifie le nom de l’utilisateur ou du rôle propriétaire de la bibliothèque externe.

**file_spec**

Spécifie le contenu du package pour une plateforme spécifique. Un seul artefact de fichier par plateforme est pris en charge.

Le fichier peut être spécifié sous la forme d’un chemin local ou d’un chemin réseau. Si l’option de source de données est spécifiée, le nom de fichier peut être un chemin relatif au conteneur référencé dans `EXTERNAL DATA SOURCE`.

Si vous le souhaitez, vous pouvez spécifier une plateforme de système d’exploitation pour le fichier. Un seul artefact de fichier ou contenu est autorisé pour chaque plateforme de système d’exploitation pour un langage ou un runtime spécifique.

**library_bits**

Spécifie le contenu du package en tant que littéral hexadécimal, similaire aux assemblys. 

Cette option est utile si vous avez l’autorisation nécessaire pour modifier une bibliothèque, mais que l’accès aux fichiers sur le serveur est restreint et que vous ne pouvez pas enregistrer le contenu à un emplacement accessible au serveur.

Au lieu de cela, vous pouvez passer le contenu du package en tant que variable au format binaire.

::: moniker range=">=sql-server-2017 <=sql-server-2017||=sqlallproducts-allversions"
**PLATFORM = WINDOWS**

Spécifie la plateforme pour le contenu de la bibliothèque. Cette valeur est nécessaire lors de la modification d’une bibliothèque existante pour ajouter une autre plateforme. Dans SQL Server 2017, Windows est la seule plateforme prise en charge.

::: moniker-end
::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
**PLATFORM**

Spécifie la plateforme pour le contenu de la bibliothèque. Cette valeur est nécessaire lors de la modification d’une bibliothèque existante pour ajouter une autre plateforme. Dans SQL Server 2019, les plateformes Windows et Linux sont prises en charge.

**language**

Spécifie le langage du package. La valeur peut être **R**, **Python** ou **Java**.
::: moniker-end

## <a name="remarks"></a>Notes 

::: moniker range=">=sql-server-2017 <=sql-server-2017||=sqlallproducts-allversions"
Pour le langage R, les packages doivent être préparés sous la forme de fichiers d’archives compressés avec l’extension .ZIP pour Windows. Dans SQL Server 2017, seule la plateforme Windows est pris en charge.  
::: moniker-end

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Pour le langage R, lors de l’utilisation d’un fichier, les packages doivent être préparés sous la forme de fichiers d’archive compressés avec l’extension .ZIP. 

Pour le langage Python, le package contenu dans un fichier .whl ou .zip doit être préparé sous la forme d’un fichier d’archive compressé. Si le package est déjà un fichier .zip, il doit être inclus dans un nouveau fichier .zip. Le chargement direct d’un package sous la forme de fichier .whl ou .zip n’est actuellement pas pris en charge.
::: moniker-end

L’instruction `ALTER EXTERNAL LIBRARY` charge uniquement les bits de la bibliothèque vers la base de données. La bibliothèque modifiée est installée quand un utilisateur exécute dans [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) du code qui appelle la bibliothèque.

## <a name="permissions"></a>Autorisations

Par défaut, l’utilisateur **dbo** ou n’importe quel membre du rôle **db_owner** a l’autorisation d’exécuter ALTER EXTERNAL LIBRARY. Par ailleurs, l’utilisateur qui a créé la bibliothèque externe peut la modifier.

## <a name="examples"></a>Exemples

Les exemples suivants modifient une bibliothèque externe nommée `customPackage`.

### <a name="a-replace-the-contents-of-a-library-using-a-file"></a>A. Remplacer le contenu d’une bibliothèque à l’aide d’un fichier

L’exemple suivant modifie une bibliothèque externe nommée `customPackage`, à l’aide d’un fichier compressé qui contient les bits mis à jour.

```sql
ALTER EXTERNAL LIBRARY customPackage 
SET 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```

Pour installer la bibliothèque mise à jour, exécutez la procédure stockée `sp_execute_external_script`.

```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'library(customPackage)'
;
```

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Pour le langage Python dans SQL Server 2019, l’exemple fonctionne également en remplaçant `'R'` par `'Python'`.
::: moniker-end
### <a name="b-alter-an-existing-library-using-a-byte-stream"></a>B. Modifier une bibliothèque existante à l’aide d’un flux d’octets

L’exemple suivant modifie la bibliothèque existante en passant les nouveaux bits sous forme de littéral hexadécimal.

```SQL
ALTER EXTERNAL LIBRARY customLibrary 
SET (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Pour le langage Python dans SQL Server 2019, l’exemple fonctionne également en remplaçant `'R'` par `'Python'`.
::: moniker-end

> [!NOTE]
> Cet exemple de code montre uniquement la syntaxe ; la valeur binaire de `CONTENT =` a été tronquée pour des raisons de clarté et ne crée pas une bibliothèque fonctionnelle. Son véritable contenu serait beaucoup plus long.

## <a name="see-also"></a>Voir aussi

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md) 
