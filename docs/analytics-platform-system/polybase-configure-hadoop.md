---
title: Configurer PolyBase pour accéder à des données externes dans Hadoop | Microsoft Docs
description: Explique comment configurer PolyBase dans Parallel Data Warehouse pour se connecter à Hadoop externe.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 94c8d399f7b6ba36b48b4c5aa7f35bbd67ce6909
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62678641"
---
# <a name="configure-polybase-to-access-external-data-in-hadoop"></a>Configurer PolyBase pour accéder à des données externes dans Hadoop

L’article explique comment utiliser PolyBase sur une appliance APS pour interroger des données externes dans Hadoop.

## <a name="prerequisites"></a>Prérequis

PolyBase prend en charge deux fournisseurs Hadoop, HDP (Hortonworks Data Platform) et CDH (Cloudera Distributed Hadoop). Hadoop suit le modèle « majeure.mineure.version » pour ses nouvelles versions, et toutes les versions d’une version majeure ou mineure prise en charge sont prises en charge. Les fournisseurs Hadoop suivants sont pris en charge :
 - Hortonworks HDP 1.3 sur Linux/Windows Server  
 - Hortonworks HDP 2.1-2.6 sur Linux
 - Hortonworks HDP 2.1 - 2.3 sur Windows Server  
 - Cloudera CDH 4.3 sur Linux  
 - Cloudera CDH 5.1-5.5, 5.9-5.13 sur Linux

### <a name="configure-hadoop-connectivity"></a>Configurer la connectivité Hadoop

Tout d’abord, configurer des points d’accès pour utiliser votre fournisseur Hadoop spécifique.

1. Exécutez [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) avec 'hadoop connectivity' et définissez une valeur appropriée pour votre fournisseur. Pour trouver la valeur pour votre fournisseur, consultez [Configuration de la connectivité PolyBase](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md). 

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. Redémarrer la région de points d’accès à l’aide de la page État du Service sur [Appliance Configuration Manager](launch-the-configuration-manager.md).
  
## <a id="pushdown"></a>Activer le calcul pushdown  

Pour améliorer les performances des requêtes, activez le calcul pushdown sur votre cluster Hadoop :  
  
1. Ouvrez une connexion Bureau à distance au nœud de contrôle de PDW.

2. Recherchez le fichier **yarn-site.XML** sur le nœud de contrôle. En règle générale, le chemin d’accès est le suivant :  

   ```xml  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\  
   ```  

3. Sur l’ordinateur Hadoop, recherchez le fichier analogue dans le répertoire de configuration Hadoop. Dans le fichier, recherchez et copiez la valeur de la clé de configuration yarn.application.classpath.  
  
4. Sur le nœud de contrôle, dans le **fichier yarn.site.xml** trouver la **yarn.application.classpath** propriété. Collez la valeur de l’ordinateur Hadoop dans l’élément de valeur.  
  
5. Pour toutes les versions 5.X de CDH, vous devez ajouter les paramètres de configuration mapreduce.application.classpath, soit à la fin de votre fichier yarn.site.xml, soit dans le fichier mapred-site.xml. HortonWorks inclut ces configurations dans les configurations yarn.application.classpath. Consultez [Configuration PolyBase](../relational-databases/polybase/polybase-configuration.md) pour voir des exemples.

## <a name="configure-an-external-table"></a>Configurer une table externe

Pour interroger les données dans votre source de données Hadoop, vous devez définir une table externe à utiliser dans les requêtes Transact-SQL. Les étapes suivantes décrivent comment configurer la table externe.

1. Créez une clé principale sur la base de données. Il est nécessaire pour chiffrer le secret des informations d’identification.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

2. Créez des informations d’identification limitées à la base de données pour les clusters Hadoop sécurisés par Kerberos.

   ```sql
   -- IDENTITY: the Kerberos user name.  
   -- SECRET: the Kerberos password  
   CREATE DATABASE SCOPED CREDENTIAL HadoopUser1
   WITH IDENTITY = '<hadoop_user_name>', Secret = '<hadoop_password>';  
   ```

3. Créez une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../t-sql/statements/create-external-data-source-transact-sql.md).

   ```sql
   -- LOCATION (Required) : Hadoop Name Node IP address and port.  
   -- RESOURCE MANAGER LOCATION (Optional): Hadoop Resource Manager location to enable pushdown computation.  
   -- CREDENTIAL (Optional):  the database scoped credential, created above.  
   CREATE EXTERNAL DATA SOURCE MyHadoopCluster WITH (  
         TYPE = HADOOP,
         LOCATION ='hdfs://10.xxx.xx.xxx:xxxx',
         RESOURCE_MANAGER_LOCATION = '10.xxx.xx.xxx:xxxx',
         CREDENTIAL = HadoopUser1
   );  
   ```

4. Créez un format de fichier externe avec [CREATE EXTERNAL FILE FORMAT](../t-sql/statements/create-external-file-format-transact-sql.md).

   ```sql
   -- FORMAT TYPE: Type of format in Hadoop (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE)  
   ```

5. Créez une table externe pointant vers les données stockées dans Hadoop avec [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md). Dans cet exemple, les données externes contiennent des données provenant de capteurs sur des voitures.

   ```sql
   -- LOCATION: path to file or directory that contains the data (relative to HDFS root).  
   CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
         [SensorKey] int NOT NULL,
         [CustomerKey] int NOT NULL,
         [GeographyKey] int NULL,
         [Speed] float NOT NULL,
         [YearMeasured] int NOT NULL  
   )  
   WITH (LOCATION='/Demo/',
         DATA_SOURCE = MyHadoopCluster,  
         FILE_FORMAT = TextFileFormat  
   );  
   ```

6. Créez des statistiques sur une table externe.

   ```sql
   CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
   ```

## <a name="polybase-queries"></a>Requêtes PolyBase

PolyBase est approprié pour trois fonctions :  
  
- Requêtes ad hoc sur les tables externes.  
- Importation de données.  
- Exportation de données.  

Les requêtes suivantes fournissent un exemple avec des données fictives provenant de capteurs sur des voitures.

### <a name="ad-hoc-queries"></a>Requêtes ad hoc  

La requête ad hoc des jointures relationnelles à des données Hadoop. Il sélectionne les clients qui dépasser 35 mph, jointure de données structurées client stockée dans les points d’accès avec les données de capteur de véhicules stockées dans Hadoop.  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
OPTION (FORCE EXTERNALPUSHDOWN);   -- or OPTION (DISABLE EXTERNALPUSHDOWN)  
```  

### <a name="importing-data"></a>Importation de données  

La requête suivante importe des données externes dans APS. Cet exemple importe les données pour les pilotes rapides dans les points d’accès pour effectuer une analyse plus approfondie. Pour améliorer les performances, il tire parti de la technologie Columnstore de points d’accès.  

```sql
CREATE TABLE Fast_Customers
WITH
(CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH (CustomerKey))
AS
SELECT DISTINCT
      Insured_Customers.CustomerKey, Insured_Customers.FirstName, Insured_Customers.LastName,   
      Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
from Insured_Customers INNER JOIN   
(  
      SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
```  

### <a name="exporting-data"></a>Exportation de données  

La requête suivante exporte des données à partir de points d’accès vers Hadoop. Il peut être utilisé pour archiver des données relationnelles à Hadoop while toujours pouvoir interroger.

```sql
-- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] 
WITH (  
      LOCATION='/archive/customer/2009',  
      DATA_SOURCE = HadoopHDP2,  
      FILE_FORMAT = TextFileFormat
)  
AS
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```  

## <a name="view-polybase-objects-in-ssdt"></a>Afficher les objets PolyBase dans SSDT  

Dans SQL Server Data Tools, les tables externes sont affichées dans un dossier distinct **des Tables externes**. Les sources de données externes et les formats de fichiers externes figurent dans des sous-dossiers du dossier **Ressources externes**.  
  
![Objets PolyBase dans SSDT](media/polybase/external-tables-datasource.png)  

## <a name="next-steps"></a>Étapes suivantes

Pour les paramètres de sécurité Hadoop, consultez [configurer la sécurité de Hadoop](polybase-configure-hadoop-security.md).<br>
Pour plus d’informations sur PolyBase, consultez [Qu’est-ce que PolyBase ?](../relational-databases/polybase/polybase-guide.md). 
 
