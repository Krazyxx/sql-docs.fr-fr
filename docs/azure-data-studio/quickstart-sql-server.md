---
title: 'Démarrage rapide : Se connecter et interroger SQL Server'
titleSuffix: Azure Data Studio
description: Ce démarrage rapide montre comment utiliser Azure Data Studio pour vous connecter à SQL Server et exécuter une requête
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: f62d315991910fa89513425e5e41700e4effd059
ms.sourcegitcommit: 553ecea0427e4d2118ea1ee810f4a73275b40741
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65620381"
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>Démarrage rapide : Se connecter et interroger à l’aide de SQL Server [!INCLUDE[name-sos](../includes/name-sos-short.md)]
Ce démarrage rapide montre comment utiliser [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour vous connecter à SQL Server, puis utiliser les instructions Transact-SQL (T-SQL) pour créer le *TutorialDB* utilisé dans [!INCLUDE[name-sos](../includes/name-sos-short.md)] didacticiels.

## <a name="prerequisites"></a>Configuration requise

Pour effectuer ce démarrage rapide, vous devez [!INCLUDE[name-sos](../includes/name-sos-short.md)]et l’accès à un serveur SQL Server.

- [Installer [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Si vous n’avez pas accès à un serveur SQL, sélectionnez votre plateforme parmi les liens suivants (pensez à mémoriser votre compte de connexion SQL et le mot de passe !) :
- [Windows : Téléchargez SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads)
- [macOS : Téléchargez SQL Server 2017 sur Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)
- [Linux - téléchargement SQL Server 2017 Developer Edition](https://docs.microsoft.com/sql/linux/sql-server-linux-overview#install) -vous ne devez suivre les étapes jusqu'à *créer et interroger des données*.


## <a name="connect-to-a-sql-server"></a>Se connecter à un serveur SQL Server

   
1. Démarrer **[!INCLUDE[name-sos](../includes/name-sos-short.md)]**.
1. La première fois que vous exécutez [!INCLUDE[name-sos](../includes/name-sos-short.md)] le **Bienvenue** page doit s’ouvrir. Si vous ne voyez pas le **Bienvenue** page, sélectionnez **aide** > **Bienvenue**. Sélectionnez **nouvelle connexion** pour ouvrir le **connexion** volet :
   
   ![Nouvelle icône de connexion](media/quickstart-sql-server/new-connection-icon.png)

1. Cet article utilise *connexion SQL*, mais *l’authentification Windows* est pris en charge. Renseignez les champs comme suit :
 
    - **Nom du serveur :** localhost
    - **Type d’authentification :** Connexion SQL  
    - **Nom d’utilisateur :** Nom d’utilisateur pour le serveur SQL Server  
    - **Mot de passe :** Mot de passe pour le serveur SQL Server  
    - **Nom de la base de données :** laissez ce champ vide 
    - **Groupe de serveurs :** \<Default\>  

   ![Nouvel écran de connexion](media/quickstart-sql-server/new-connection-screen.png)



## <a name="create-a-database"></a>création d'une base de données ;

Les étapes suivantes créent une base de données nommée **TutorialDB**:

1. Cliquez avec le bouton droit sur votre serveur, **localhost**, puis sélectionnez **nouvelle requête.**
1. Collez l’extrait de code suivant dans la fenêtre de requête : 

   ```sql
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
      CREATE DATABASE [TutorialDB];
   GO
   IF SERVERPROPERTY('ProductVersion') > '12'
       ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON;
   GO
   ```
1. Pour exécuter la requête, cliquez sur **exécuter** .

Une fois la requête terminée, le nouveau **TutorialDB** apparaît dans la liste des bases de données. Si vous ne le voyez pas, cliquez sur le **bases de données** nœud et sélectionnez **Actualiser**.


## <a name="create-a-table"></a>Créer une table

L’éditeur de requête est toujours connecté à la *master* base de données, mais nous voulons créer une table dans le *TutorialDB* base de données. 

1. Modifier le contexte de connexion au **TutorialDB**:

   ![Changer de contexte](media/quickstart-sql-server/change-context.png)



1. Collez l’extrait de code suivant dans la fenêtre de requête et cliquez sur **exécuter**:

   > [!NOTE]
   > Vous pouvez l’ajouter à ou remplacer la requête précédente dans l’éditeur. Notez qu’un clic sur **exécuter** exécute uniquement la requête sélectionnée. Si rien n’est sélectionné, un clic sur **exécuter** exécute toutes les requêtes dans l’éditeur.

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
      DROP TABLE dbo.Customers;
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
       CustomerId  int NOT NULL PRIMARY KEY, -- primary key column
       Name        nvarchar(50) NOT NULL,
       Location    nvarchar(50) NOT NULL,
       Email       nvarchar(50) NOT NULL
   );
   GO
   ```

Une fois la requête terminée, le nouveau **clients** table apparaît dans la liste des tables. Vous devrez peut-être avec le bouton droit le **TutorialDB > Tables** nœud et sélectionnez **Actualiser**.

## <a name="insert-rows"></a>Insérer des lignes

- Collez l’extrait de code suivant dans la fenêtre de requête et cliquez sur **exécuter**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId], [Name], [Location], [Email])
   VALUES
      ( 1, N'Orlando', N'Australia', N''),
      ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
      ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
      ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
   GO
   ```



## <a name="view-the-data-returned-by-a-query"></a>Afficher les données retournées par une requête
1. Collez l’extrait de code suivant dans la fenêtre de requête et cliquez sur **exécuter**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Les résultats de la requête sont affichés :

   ![Sélectionnez les résultats](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous avez correctement connecté à SQL Server et exécutez une requête, essayez le [didacticiel de l’éditeur de Code](tutorial-sql-editor.md).


