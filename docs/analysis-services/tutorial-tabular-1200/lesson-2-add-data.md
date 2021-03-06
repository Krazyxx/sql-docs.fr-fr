---
title: 'Leçon 2 : Ajouter des données | Microsoft Docs'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6e5a4d0ec80da5c29d513e74df1becca2d5cbb84
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65404871"
---
# <a name="lesson-2-add-data"></a>Leçon 2 : Ajouter des données
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

Dans cette leçon, vous utiliserez l’Assistant Importation de Table dans SSDT pour se connecter à la base de données SQL AdventureWorksDW, sélectionner des données, afficher un aperçu et filtrer les données et puis importer les données dans votre espace de travail du modèle.  
  
À l’aide de l’Assistant Importation de Table, vous pouvez importer des données à partir de diverses sources relationnelles : Access, SQL, Oracle, Sybase, Informix, DB2, Teradata et bien plus encore. Les étapes d'importation de données à partir des différentes sources relationnelles sont très semblables à celles qui suivent. Données peuvent également être sélectionnées à l’aide d’une procédure stockée. Pour en savoir plus sur l’importation de données et les différents types de sources de données que vous pouvez importer à partir de, consultez [des Sources de données](../tabular-models/data-sources-supported-ssas-tabular.md).  
  
Durée estimée pour effectuer cette leçon : **20 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 1 : Créez un projet de modèle tabulaire](lesson-1-create-a-new-tabular-model-project.md).  
  
## <a name="create-a-connection"></a>Créer une connexion  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2014-database"></a>Pour créer une connexion à une la base de données AdventureWorksDW2014  
  
1.  Dans l’Explorateur de modèles tabulaires, cliquez sur **des Sources de données** > **importer à partir de la Source de données**.  
  
    Cette action lance l’Assistant d’importation de Table, qui vous guide à travers la configuration d’une connexion à une source de données. Si vous ne voyez pas l’Explorateur de modèles tabulaires, double-cliquez sur **Model.bim** dans **l’Explorateur de solutions** pour ouvrir le modèle dans le concepteur. 
    
    ![as-tabular-lesson2-tme](media/as-tabular-lesson2-tme.png) 

    Remarque : Si vous créez votre modèle au niveau de compatibilité 1400, vous verrez la nouvelle expérience d’obtenir des données au lieu de l’Assistant Importation de Table. Les boîtes de dialogue seront affiche un peu différentes de la procédure ci-dessous, mais vous serez toujours en mesure de suivre la procédure. 
  
2.  Dans l’Assistant Importation de Table, sous **bases de données relationnelles**, cliquez sur **Microsoft SQL Server** > **suivant**.  
  
3.  Dans la page de **Connexion à une base de données Microsoft SQL Server** , dans **Nom convivial de la connexion**, tapez **Base de données Adventure Works depuis SQL**.  
  
4.  Dans **nom du serveur**, tapez le nom du serveur où vous avez installé la base de données AdventureWorksDW.  
  
5.  Dans le **nom de la base de données** champ, sélectionnez **AdventureWorksDW**, puis cliquez sur **suivant**.  
  
    ![as-tabular-lesson2-tiw-name](media/as-tabular-lesson2-tiw-name.png)
  
6.  Dans la page **Informations d'emprunt d'identité** , vous devez spécifier les informations d'identification qu'Analysis Services utilisera pour se connecter à la source de données lors de l'importation et du traitement des données. Vérifiez que l'option **Nom d'utilisateur et mot de passe Windows spécifiques** est sélectionnée, puis, dans **Nom d'utilisateur** et **Mot de passe**, entrez vos informations d'identification de connexion Windows, puis cliquez sur **Suivant**.  
  
    > [!NOTE]  
    > L'utilisation d'un compte d'utilisateur et d'un mot de passe Windows est la méthode la plus sûre pour se connecter à une source de données. Pour plus d’informations, consultez [l’emprunt d’identité](../tabular-models/impersonation-ssas-tabular.md).  
  
7.  Dans la page **Choisir comment importer les données** , vérifiez que l'option **Sélectionner les données à importer dans une liste de tables et de vues** est sélectionnée. Vous souhaitez choisir dans une liste de tables et de vues et vous devez donc cliquer sur **Suivant** pour afficher la liste de toutes les tables sources dans la base de données source.  
  
8.  Dans le **sélectionner des Tables et vues** , sélectionnez la case à cocher pour les tables suivantes : **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**,  **DimProductSubcategory**, et **FactInternetSales**.  
  
    **NE CLIQUEZ PAS** sur **Terminer**.  
  
## <a name="FilterData"></a>Filter the table data  
La table DimCustomer que vous importez à partir de la base de données exemple contient un sous-ensemble des données à partir de la base de données SQL Server Adventure Works d’origine. Vous allez filtrer d’autres colonnes de la table DimCustomer qui ne sont pas nécessaires lors de l’importation dans votre modèle. Dans la mesure du possible, vous souhaitez filtrer les données qui ne sont pas utilisées afin d’économiser l’espace mémoire utilisé par le modèle.  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a>Pour filtrer les données de table avant l'importation  
  
1.  Sélectionnez la ligne de la **DimCustomer** table, puis cliquez sur **aperçu et filtrer**. La fenêtre **Aperçu de la table sélectionnée** s'affiche en présentant toutes les colonnes de la table source DimCustomer.  
  
2.  Désactivez la case à cocher en haut des colonnes suivantes : **SpanishEducation**, **FrenchEducation**, **SpanishOccupation**, **FrenchOccupation**. 

    ![as-tabular-lesson2-tiw-clear](media/as-tabular-lesson2-tiw-clear.png)
  
    Étant donné que les valeurs de ces colonnes ne sont pas appropriées à l'analyse des ventes sur Internet, il est inutile de les importer. Éliminer les colonnes inutiles rendra votre modèle plus petits et plus efficace.  
  
3.  Vérifiez que toutes les autres colonnes sont cochées, puis cliquez sur **OK**.  
  
    Remarquez que les mots **filtres appliqués** s’affichent maintenant dans le **détails du filtre** colonne dans le **DimCustomer** de lignes ; si vous cliquez sur ce lien vous verrez une description textuelle de la vous venez d’appliquer des filtres.  
    
    ![as-tabular-lesson2-applied-filters](media/as-tabular-lesson2-applied-filters.png)
    
  
4.  Filtrez les autres tables en désactivant les cases à cocher des colonnes suivantes dans chaque table :  
    
    **DimDate**
    
      |colonne|  
      |--------|  
      |**DateKey**|  
      |**SpanishDayNameOfWeek**|  
      |**FrenchDayNameOfWeek**|  
      |**SpanishMonthName**|  
      |**FrenchMonthName**|  
  
    **DimGeography**
  
      |colonne|  
      |-------------|  
      |**SpanishCountryRegionName**|  
      |**FrenchCountryRegionName**|  
      |**IpAddressLocator**|  
  
    **DimProduct**
  
      |colonne|  
      |-----------|  
      |**SpanishProductName**|  
      |**FrenchProductName**|  
      |**FrenchDescription**|  
      |**ChineseDescription**|  
      |**ArabicDescription**|  
      |**HebrewDescription**|  
      |**ThaiDescription**|  
      |**GermanDescription**|  
      |**JapaneseDescription**|  
      |**TurkishDescription**|  
  
    **DimProductCategory**
  
      |colonne|  
      |--------------------|  
      |**SpanishProductCategoryName**|  
      |**FrenchProductCategoryName**|  
  
    **DimProductSubcategory**
  
      |colonne|  
      |-----------------------|  
      |**SpanishProductSubcategoryName**|  
      |**FrenchProductSubcategoryName**|  
  
    **FactInternetSales**
  
      |colonne|  
      |------------------|  
      |**OrderDateKey**|  
      |**DueDateKey**|  
      |**ShipDateKey**|   
  
## <a name="Import"></a>Import the selected tables and column data  
Maintenant que vous avez prévisualisé et filtré les données inutiles, vous pouvez importer le reste des données souhaitées. L'Assistant importe les données de la table avec toutes les relations entre les tables. Les nouvelles tables et les colonnes sont créées dans le modèle et les données filtrées ne seront pas importées.  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a>Pour importer les tables sélectionnées et les données de colonne  
  
1.  Vérifiez vos sélections. Si tout semble OK, cliquez sur **Terminer**.  
  
    Pendant l'importation des données, l'Assistant affiche le nombre de lignes qui ont été extraites. Lorsque toutes les données ont été importées, un message de réussite s'affiche.  
    
    ![en tant que-tabulaire-lesson2-réussite](media/as-tabular-lesson2-success.png) 
  
    > [!TIP]  
    > Pour afficher les relations qui ont été créées automatiquement entre les tables importées, sur la ligne **Préparation des données** , cliquez sur **Détails**. 
  
2.  Cliquez sur **Fermer**.  
  
    L’Assistant se ferme et le Générateur de modèles affiche maintenant vos tables importées. 
  
## <a name="save-your-model-project"></a>Enregistrer votre projet de modèle  
Il est important de sauvegarder fréquemment votre projet de modèle.  
  
#### <a name="to-save-the-model-project"></a>Pour enregistrer le projet de modèle  
  
-   Click **Fichier** > **Enregistrer tout**.  
  
## <a name="whats-next"></a>Quelle est l’étape suivante ?
Accédez à la leçon suivante : [Leçon 3 : Marquer en tant que Table de dates](lesson-3-mark-as-date-table.md).

  
  
