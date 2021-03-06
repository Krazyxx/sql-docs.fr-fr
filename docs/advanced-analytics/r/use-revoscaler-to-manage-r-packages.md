---
title: Comment utiliser les fonctions RevoScaleR pour rechercher ou installer des packages R - Services de SQL Server Machine Learning
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7eed38e54b0c4e77af8f7b3ede0af2d98b9c58b2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642341"
---
# <a name="how-to-use-revoscaler-functions-to-find-or-install-r-packages-on-sql-server"></a>Comment utiliser les fonctions RevoScaleR pour rechercher ou installer des packages R sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR 9.0.1 et versions ultérieures inclut des fonctions de gestion des packages R un contexte de calcul de SQL Server. Ces fonctions peuvent être utilisées par les non-administrateurs à distance, pour installer des packages sur SQL Server sans accès direct au serveur.

SQL Server 2017 Machine Learning Services inclut déjà une version plus récente de RevoScaleR. Les clients de SQL Server 2016 R Services doivent faire un [mise à niveau du composant](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) pour obtenir des fonctions de gestion de package RevoScaleR. Pour obtenir des instructions sur la récupération du package version et contenu, consultez [obtenir des informations de package](determine-which-packages-are-installed-on-sql-server.md).

## <a name="revoscaler-functions-for-package-management"></a>Fonctions RevoScaleR pour la gestion des packages

Le tableau suivant décrit les fonctions utilisées pour la gestion et l’installation des packages R.

| Fonction | Description |
|----------|-------------|
| [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) | Déterminer le chemin d’accès de la bibliothèque de l’instance sur le serveur SQL distant. |
| [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) | Obtient le chemin d’accès pour un ou plusieurs packages sur le serveur SQL distant. |
| [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) | Appelez cette fonction à partir d’un client distant de R à installer des packages dans un contexte de calcul de SQL Server, à partir d’un référentiel spécifié, ou en lisant les packages compressés enregistrés localement. Cette fonction vérifie les dépendances et garantit que tous les packages associés peuvent être installés à SQL Server, tout comme l’installation des packages R dans le contexte de calcul local. Pour utiliser cette option, vous devez activer gestion des packages sur le serveur et la base de données. Les environnements client et le serveur doivent avoir la même version de RevoScaleR. |
| [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) | Obtient une liste des packages installés dans le contexte de calcul spécifié. |
| [rxSyncPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsyncpackages) | Copier des informations sur une bibliothèque de package entre le système de fichiers et de la base de données, pour le contexte de calcul spécifié. |
| [rxRemovePackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxremovepackages) | Supprime les packages à partir d’un contexte de calcul spécifiée. Il calcule des dépendances et garantit que les packages qui ne sont plus utilisés par d’autres packages sur SQL Server sont supprimés pour libérer des ressources. |

## <a name="prerequisites"></a>Prérequis

+ [Activer la gestion à distance des packages R sur SQL Server](r-package-how-to-enable-or-disable.md)

+ Versions de RevoScaleR doivent être le même sur des environnements client et serveur. Pour plus d’informations, consultez [obtenir des informations de package](determine-which-packages-are-installed-on-sql-server.md).

+ Autorisation de se connecter au serveur et une base de données et pour exécuter des commandes R. Vous devez être membre d’un rôle de base de données qui vous permet d’installer des packages sur l’instance spécifiée et la base de données.

+ Packages dans **étendue partagée** peuvent être installées par les utilisateurs appartenant à la `rpkgs-shared` rôle dans une base de données spécifiée. Tous les utilisateurs de ce rôle peuvent désinstaller des packages partagés.

+ Packages dans **étendue privée** peut être installé par tout utilisateur appartenant à la `rpkgs-private` rôle dans une base de données. Toutefois, les utilisateurs peuvent voir et désinstaller uniquement leurs propres packages.

+ Les propriétaires de base de données peuvent fonctionner avec des packages privés ou partagés.

## <a name="client-connections"></a>Connexions clientes

Une station de travail cliente peut être [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/install-on-windows) ou un [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) (scientifiques de données utilisent souvent l’édition gratuite pour les développeurs) sur le même réseau.

Lors de l’appel des fonctions de gestion de package à partir d’un client de R à distance, vous devez créer un objet de contexte de calcul tout d’abord, à l’aide de la [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) (fonction). Par la suite, pour chaque fonction de gestion de package que vous utilisez, transmettre le contexte de calcul en tant qu’argument.

Identité de l’utilisateur est généralement spécifiée lors de la définition du contexte de calcul. Si vous ne spécifiez pas un nom d’utilisateur et le mot de passe lorsque vous créez le contexte de calcul, l’identité de l’utilisateur qui exécute le code R est utilisée.

1. À partir d’une ligne de commande R, définissez une chaîne de connexion à l’instance et de la base de données.
2. Utilisez le [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) constructeur pour définir un contexte de calcul SQL Server, à l’aide de la chaîne de connexion.

    ```R
    sqlcc <- RxInSqlServer(connectionString = myConnString, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    ```
3. Créer une liste des packages que vous souhaitez installer et enregistrer la liste dans une variable de chaîne.

    ```R
    packageList <- c("e1071", "mice")
    ```

4. Appelez [rxInstallPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstallpackages) et de transmettre le contexte de calcul et de la variable de chaîne contenant les noms de package.

    ```R
    rxInstallPackages(pkgs = packageList, verbose = TRUE, computeContext = sqlcc)
    ```

    Si les packages dépendants sont nécessaires, elles sont également installés, en supposant qu’une connexion internet est disponible sur le client.
    
    Les packages sont installés à l’aide des informations d’identification de l’utilisateur qui effectue la connexion, dans l’étendue par défaut pour cet utilisateur.

## <a name="call-package-management-functions-in-stored-procedures"></a>Appeler des fonctions de gestion de package dans les procédures stockées

Cam exécuter des fonctions de gestion de package à l’intérieur de `sp_execute_external_script`. Lorsque vous procédez ainsi, la fonction est exécutée à l’aide du contexte de sécurité de l’appelant de la procédure stockée.

## <a name="examples"></a>Exemples

Cette section fournit des exemples montrant comment utiliser ces fonctions à partir d’un client distant lors de la connexion à une instance de SQL Server ou de la base de données en tant que le contexte de calcul.

Pour tous les exemples, vous devez fournir une chaîne de connexion, ou dans un contexte de calcul, ce qui nécessite une chaîne de connexion. Cet exemple fournit une méthode de création d’un contexte de calcul pour SQL Server :

```R
instance_name <- "computer-name/instance-name";
database_name <- "TestDB";
sqlWait= TRUE;
sqlConsoleOutput <- TRUE;
connString <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
sqlcc <- RxInSqlServer(connectionString = connString, wait = sqlWait, consoleOutput = sqlConsoleOutput, numTasks = 4);
```

Selon l’endroit où se trouve le serveur et le modèle de sécurité, vous devrez peut-être fournir une spécification de domaine et un sous-réseau dans la chaîne de connexion, ou utiliser une connexion SQL. Exemple :

```R
connStr <- "Driver=SQL Server;Server=myserver.financeweb.contoso.com;Database=Finance;Uid=RUser1;Pwd=RUserPassword"
```

### <a name="get-package-path-on-a-remote-sql-server-compute-context"></a>Obtenir le chemin d’accès du package sur un contexte de calcul de SQL Server à distance

Cet exemple obtient le chemin d’accès pour le **RevoScaleR** package sur le contexte de calcul `sqlcc`.

```R
sqlPackagePaths <- rxFindPackage(package = "RevoScaleR", computeContext = sqlcc)
print(sqlPackagePaths)
```

**Résultats**

« C:/Program Files/Microsoft SQL Server/MSSQL14. MSSQLSERVER/R_SERVICES/library/RevoScaleR »

> [!TIP]
> Si vous avez activé l’option Afficher la sortie de la console SQL, vous pouvez obtenir des messages d’état à partir de la fonction qui précède la `print` instruction. Une fois que vous avez terminé de tester votre code, définissez `consoleOutput` sur FALSE dans le constructeur du contexte de calcul pour éliminer les messages.

### <a name="get-locations-for-multiple-packages"></a>Obtenir les emplacements de plusieurs packages

L’exemple suivant obtient les chemins d’accès pour le **RevoScaleR** et **lattice** packages, sur le contexte de calcul `sqlcc`. Pour obtenir des informations sur plusieurs packages, passez un vecteur de chaînes contenant les noms de package.

```R
packagePaths <- rxFindPackage(package = c("RevoScaleR", "lattice"), computeContext = sqlcc)
print(packagePaths)
```

### <a name="get-package-versions-on-a-remote-compute-context"></a>Obtenir des versions de package sur un contexte de calcul à distance

Exécutez cette commande à partir d’une console R pour obtenir le numéro de build et les numéros de version des packages installés sur le contexte de calcul *sqlServer*.

```R
sqlPackages <- rxInstalledPackages(fields = c("Package", "Version", "Built"), computeContext = sqlServer)
```

**Résultats**

```text
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/RevoScaleR"

[2] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library/lattice"
```

### <a name="install-a-package-on-sql-server"></a>Installer un package sur SQL Server

Cet exemple installe le **prévision** package et ses dépendances dans le contexte de calcul.

  ```R
  pkgs <- c("forecast")
  rxInstallPackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="remove-a-package-from-sql-server"></a>Supprimer un package de SQL Server

Cet exemple supprime la **prévision** package et ses dépendances à partir du contexte de calcul.

  ```R
  pkgs <- c("forecast")
  rxRemovePackages(pkgs = pkgs, verbose = TRUE, scope = "private", computeContext = sqlcc)
  ```

### <a name="synchronize-packages-between-database-and-file-system"></a>Synchroniser des packages entre le système de fichiers et de la base de données

L’exemple suivant vérifie la base de données **TestDB**et détermine si tous les packages sont installés dans le système de fichiers. Si certains packages sont manquants, ils sont installés dans le système de fichiers.

```R
# Instantiate the compute context
connectionString <- "Driver=SQL Server;Server=myServer;Database=TestDB;Trusted_Connection=True;"
computeContext <- RxInSqlServer(connectionString = connectionString )

# Synchronize the packages in the file system for all scopes and users
rxSyncPackages(computeContext=computeContext, verbose=TRUE)
```

Fonctionnement de la synchronisation de package sur un par base de données et par utilisateur. Pour plus d’informations, consultez [synchronisation de package R pour SQL Server](../r/package-install-uninstall-and-sync.md).

### <a name="use-a-stored-procedure-to-list-packages-in-sql-server"></a>Utiliser une procédure stockée pour répertorier les packages dans SQL Server

Exécutez cette commande à partir de Management Studio ou un autre outil qui prend en charge T-SQL, pour obtenir la liste des packages installés sur l’instance actuelle, à l’aide de `rxInstalledPackages` dans une procédure stockée.

```sql
EXEC sp_execute_external_script 
  @language=N'R', 
  @script=N'
    myPackages <- rxInstalledPackages();
    OutputDataSet <- as.data.frame(myPackages);
    '
```

Le `rxSqlLibPaths` fonction peut être utilisée pour déterminer la bibliothèque active utilisée par SQL Server Machine Learning Services. Ce script peut retourner uniquement le chemin de bibliothèque pour le serveur actif. 

```sql
declare @instance_name nvarchar(100) = @@SERVERNAME, @database_name nvarchar(128) = db_name();
exec sp_execute_external_script 
  @language = N'R',
  @script = N'
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    .libPaths(rxSqlLibPaths(connStr));
    print(.libPaths());
  ', 
  @input_data_1 = N'', 
  @params = N'@instance_name nvarchar(100), @database_name nvarchar(128)',
  @instance_name = @instance_name, 
  @database_name = @database_name;
```

## <a name="see-also"></a>Voir aussi

+ [Activer la gestion de packages R à distance](r-package-how-to-enable-or-disable.md)
+ [Synchroniser des packages R](package-install-uninstall-and-sync.md)
+ [Conseils pour l’installation des packages R](packages-installed-in-user-libraries.md)
+ [Packages par défaut](installing-and-managing-r-packages.md)