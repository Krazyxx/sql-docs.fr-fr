---
title: À l’aide de jeux de résultats actifs multiples (MARS) | Microsoft Docs
description: Utilisation de MARS (Multiple Active Result Sets)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, MARS
- MSOLEDBSQL, MARS
- data access [OLE DB Driver for SQL Server], MARS
- Multiple Active Result Sets
- OLE DB Driver for SQL Server, MARS
- MARS [SQL Server]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: d8f59034d6826bd1af3f1c48c81674dfc039b85e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52545472"
---
# <a name="using-multiple-active-result-sets-mars"></a>Utilisation de MARS (Multiple Active Result Sets)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] a introduit la prise en charge de MARS (Multiple Active Result Sets) dans les applications accédant au [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les applications de base de données ne pouvaient pas gérer plusieurs instructions actives sur une connexion. Lors de l'utilisation de jeux de résultats [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par défaut, l'application devait traiter ou annuler tous les jeux de résultats d'un lot avant de pouvoir exécuter tout autre lot sur cette connexion. Un nouvel attribut de connexion a été introduit dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] de manière à ce que les applications puissent gérer plus d'une demande en attente par connexion et, plus spécifiquement, pour qu'elles puissent avoir plus d'un jeu de résultats par défaut actif par connexion.  
  
 MARS simplifie la conception d'applications grâce aux nouvelles fonctionnalités suivantes :  
  
-   Les applications peuvent avoir plusieurs jeux de résultats par défaut ouverts et entrelacer leur lecture.  
  
-   Les applications peuvent exécuter d'autres instructions (par exemple, INSERT, UPDATE, DELETE et des appels de procédure stockée) pendant que les jeux de résultats par défaut sont ouverts.  
  
 Voici quelques recommandations pour les applications utilisant MARS :  
  
-   Les jeux de résultats par défaut doivent être utilisés pour des jeux de résultats à courte durée de vie ou des jeux de résultats de petites taille générés par des instructions SQL uniques (SELECT, DML avec OUTPUT, RECEIVE, READ TEXT, etc.).  
  
-   Des curseurs côté serveur doivent être utilisés pour des jeux de résultats à plus longue durée de vie ou des jeux de résultats de grande taille générés par des instructions SQL uniques.  
  
-   Lisez systématiquement les résultats dans leur intégralité afin de savoir s'ils contiennent des demandes de procédure ou des traitements qui renvoient des résultats multiples.  
  
-   Si possible, utilisez des appels d'API pour modifier les propriétés de connexion et gérez les transactions plutôt que les instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
-   Dans MARS, l'emprunt d'identité à l'échelle de la session est interdit lorsque des traitements simultanés sont en cours d'exécution.  
  
> [!NOTE]  
>  Par défaut, la fonctionnalités MARS n'est pas activée. Pour utiliser MARS lors de la connexion à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec OLE DB Driver pour SQL Server, vous devez l’activer au sein d’une chaîne de connexion. Pour plus d’informations, consultez le pilote OLE DB pour les sections de SQL Server, plus loin dans cette rubrique.  
  
 OLE DB Driver pour SQL Server ne limite pas le nombre d’instructions actives sur une connexion.  
  
 Les applications conventionnelles n’ayant pas besoin d’avoir plusieurs traitements à instructions multiples ni plusieurs procédures stockées en cours d’exécution en même temps peuvent tirer parti de MARS sans avoir à comprendre comment ce dernier est implémenté. Toutefois, les applications ayant des exigences plus complexes doivent prendre ceci compte.  
  
 MARS permet l'exécution entrelacée de plusieurs demandes au sein d'une connexion unique. Autrement dit, il permet à un traitement de s'exécuter, et au sein de cette exécution, il permet à d'autres demandes de s'exécuter. Notez toutefois que MARS est défini en terme d'entrelacement et non en terme d'exécution parallèle.  
  
 L’infrastructure MARS permet l’exécution en mode entrelacé de plusieurs traitements, mais l’exécution ne peut être basculée qu’à des points bien définis. Par ailleurs, la plupart des instructions doivent s'exécuter atomiquement au sein d'un lot. Les instructions qui retournent des lignes au client, parfois appelées *points d’interruption*, sont autorisées à entrelacer l’exécution avant l’achèvement pendant que des lignes sont envoyées au client, par exemple :  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 Toute autre instruction exécutée dans le cadre d'une procédure stockée ou d'un traitement doit s'exécuter jusqu'à la fin pour que l'exécution puisse être basculée sur d'autres demandes MARS.  
  
 La manière exacte dont les lots entrelacent l'exécution dépend de plusieurs facteurs et il est difficile de prédire la séquence exacte dans laquelle les commandes de plusieurs traitements qui contiennent des points d'interruption seront exécutées. Soyez prudent afin d'éviter des effets secondaires non désirés liés à l'exécution entrelacée de traitements complexes de cet type.  
  
 Évitez des problèmes en utilisant des appels d'API plutôt que des instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour gérer l'état de la connexion (SET, USE) et les transactions (BEGIN TRAN, COMMIT, ROLLBACK) en n'incluant pas ces instructions dans des traitements à instructions multiples qui contiennent également des points d'interruption, et en sérialisant l'exécution de tels traitements par la consommation ou l'annulation de tous les résultats.  
  
> [!NOTE]  
>  Un traitement ou une procédure stockée qui démarre une transaction manuelle ou implicite lorsque MARS est activé doit terminer la transaction avant que le traitement ne quitte. S'il ne le fait pas, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restaure toutes les modifications apportées par la transaction lorsque le traitement se termine. Une telle transaction est gérée par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en tant que transaction dont l'étendue est définie par traitement. Il s'agit d'un nouveau type de transaction introduit dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] pour permettre aux procédures stockées valides existantes d'être utilisées lorsque MARS est activé. Pour plus d’informations sur les transactions délimitées au traitement, consultez [instructions Transaction &#40;Transact-SQL&#41;](../../../t-sql/statements/statements.md).  
  
 Pour obtenir un exemple d’utilisation de MARS à partir d’ADO, consultez [à l’aide d’ADO avec OLE DB Driver pour SQL Server](../../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
## <a name="in-memory-oltp"></a>OLTP en mémoire  
 OLTP en mémoire prend en charge de MARS, à l’aide de requêtes et des procédures stockées compilées en mode natif. MARS permet demandant les données à partir de plusieurs requêtes sans avoir besoin de récupérer complètement chaque jeu de résultats avant envoi d’une demande pour extraire les lignes à partir d’un nouveau jeu de résultats. Pour pouvoir lire à partir de plusieurs jeux de résultats ouverts, vous devez utiliser une connexion MARS est activé.  
  
 MARS est désactivée par défaut, vous devez l’activer explicitement en ajoutant `MultipleActiveResultSets=True` à une chaîne de connexion. L’exemple suivant montre comment se connecter à une instance de SQL Server et spécifier que MARS est activé :  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 MARS avec OLTP en mémoire est essentiellement identique à MARS dans le reste du moteur SQL. La liste suivante décrit les différences lors de l’utilisation de MARS dans des tables optimisées en mémoire et en mode natif des procédures stockées compilées.  
  
 **Tables optimisées en mémoire et MARS**  
  
 Voici les différences entre les tables sur disque et optimisées en mémoire quand à l’aide d’un MARS activé connexion :  
  
-   Deux instructions peuvent modifier des données dans le même objet cible, mais si les deux essaient de modifier le même enregistrement un conflit d’écriture-écriture entraîne la nouvelle opération échoue. Toutefois, si les deux opérations modifient des enregistrements différents, les opérations réussissent.  
  
-   Chaque instruction s’exécute en isolement d’instantané afin de nouvelles opérations ne peuvent pas voir les modifications apportées par les instructions existantes. Même si les instructions simultanées sont exécutées sous la même transaction le moteur SQL crée les transactions délimitées au traitement pour chaque instruction qui sont isolées les uns des autres. Toutefois, délimitées au traitement des transactions sont toujours liées afin de la restauration d’une seule transaction délimitées au traitement affecte les autres dans le même lot.  
  
-   Opérations DDL ne sont pas autorisées dans les transactions utilisateur afin qu’ils échouent immédiatement.  
  
 **MARS et procédures stockées compilées en mode natif**  
  
 Les procédures stockées compilées en mode natif peuvent s’exécuter dans les connexions MARS est activé et peuvent générer une autre instruction de l’exécution uniquement lorsqu’un point est rencontré. Un point de rendement nécessite une instruction SELECT, est la seule instruction dans une procédure stockée compilée en mode natif qui peut produire une autre instruction de l’exécution. Si une instruction SELECT n’est pas présente dans la procédure que ne génèrera pas, il sera exécutée entièrement avant que les autres instructions commencent.  
  
 **Transactions MARS et OLTP en mémoire**  
  
 Modifications apportées par les instructions et les blocs atomic sont entrelacés sont isolées les uns des autres. Par exemple, si une instruction ou bloc atomic apporte des modifications et génère ensuite une autre instruction de l’exécution, la nouvelle instruction ne verrez pas les modifications apportées par la première instruction. En outre, lors de la première instruction reprend l’exécution, il ne verrez pas toutes les modifications apportées par d’autres instructions. Instructions ne voient que les modifications qui sont terminées et validées avant le démarrage de l’instruction.  
  
 Une nouvelle transaction de l’utilisateur peut être démarrée dans la transaction utilisateur actuel à l’aide de l’instruction BEGIN TRANSACTION : cela est pris en charge uniquement en mode interop afin de l’instruction BEGIN TRANSACTION ne peut être appelée à partir d’une instruction T-SQL et non à partir d’un compilées en mode natif stocké dans procédure. Vous pouvez créer un enregistrement point dans une transaction à l’aide de SAVE TRANSACTION ou un appel API à la transaction. Save(save_point_name) restauration au point de sauvegarde. Cette fonctionnalité est également activée uniquement à partir d’instructions T-SQL et non à partir d’en mode natif des procédures stockées compilées.  
  
 **MARS et les index columnstore**  
  
 SQL Server (à partir de 2016) prend en charge MARS avec des index columnstore. SQL Server 2014 utilise MARS pour les connexions en lecture seule à des tables avec un index columnstore.    Toutefois, SQL Server 2014 ne prend pas en charge MARS pour les opérations de langage de manipulation de données (DML) simultanées sur une table avec un index columnstore. Quand ce cas se produit, SQL Server met fin aux connexions et annule les transactions.   SQL Server 2012 a des index columnstore en lecture seule et MARS ne s’applique pas à eux.  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver pour SQL Server  
 OLE DB Driver pour SQL Server prend en charge MARS via l’ajout de la propriété d’initialisation de la source de données SSPROP_INIT_MARSCONNECTION, implémentée dans le jeu de propriétés DBPROPSET_SQLSERVERDBINIT. De plus, un nouveau mot clé de chaîne de connexion, **MarsConn**, a été ajouté. Il accepte **true** ou **false** valeurs ; **false** est la valeur par défaut.  
  
 Le propriété de source de données DBPROP_MULTIPLECONNECTIONS a la valeur par défaut VARIANT_TRUE. Cela signifie que le fournisseur générera dynamiquement plusieurs connexions pour prendre en charge plusieurs objets command et rowset simultanés. Quand MARS est activé, OLE DB Driver pour SQL Server peut prendre en charge plusieurs objets command et rowset sur une connexion unique. MULTIPLE_CONNECTIONS est par conséquent défini par défaut sur VARIANT_FALSE.  
  
 Pour plus d’informations sur les améliorations apportées au jeu de propriétés DBPROPSET_SQLSERVERDBINIT, consultez [propriétés d’initialisation et d’autorisation](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
### <a name="ole-db-driver-for-sql-server-example"></a>Exemple OLE DB Driver pour SQL Server  
 Dans cet exemple, un objet source de données est créé à l’aide d’OLE DB Driver pour SQL Server et MARS est activé à l’aide du jeu de propriétés DBPROPSET_SQLSERVERDBINIT avant que l’objet session ne soit créé.  
  
```  
#include <msoledbsql.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL,  
   CLSCTX_INPROC_SERVER,  
   IID_IDBInitialize,   
    (void**)&pIDBInitialize);  
  
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void**)&pIDBProperties);  
  
// Set the MARS property.  
DBPROP rgPropMARS;  
  
// The following is necessary since MARS is off by default.  
rgPropMARS.dwPropertyID = SSPROP_INIT_MARSCONNECTION;  
rgPropMARS.dwOptions = DBPROPOPTIONS_REQUIRED;  
rgPropMARS.dwStatus = DBPROPSTATUS_OK;  
rgPropMARS.colid = DB_NULLID;  
V_VT(&(rgPropMARS.vValue)) = VT_BOOL;  
V_BOOL(&(rgPropMARS.vValue)) = VARIANT_TRUE;  
  
// Create the structure containing the properties.  
DBPROPSET PropSet;  
PropSet.rgProperties = &rgPropMARS;  
PropSet.cProperties = 1;  
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
  
// Get an IDBProperties pointer and set the initialization properties.  
pIDBProperties->SetProperties(1, &PropSet);  
pIDBProperties->Release();  
  
// Initialize the data source object.  
hr = pIDBInitialize->Initialize();  
  
//Create a session object from a data source object.  
IOpenRowset * pIOpenRowset = NULL;  
hr = IDBInitialize->QueryInterface(IID_IDBCreateSession, (void**)&pIDBCreateSession));  
hr = pIDBCreateSession->CreateSession(  
   NULL,             // pUnkOuter  
   IID_IOpenRowset,  // riid  
  &pIOpenRowset ));  // ppSession  
  
// Create a rowset with a firehose mode cursor.  
IRowset *pIRowset = NULL;  
DBPROP rgRowsetProperties[2];  
  
// To get a firehose mode cursor request a   
// forward only read only rowset.  
rgRowsetProperties[0].dwPropertyID = DBPROP_IRowsetLocate;  
rgRowsetProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[0].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[0].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[0].vValue));  
rgRowsetProperties[0].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[0].vValue.boolVal = VARIANT_FALSE;  
  
rgRowsetProperties[1].dwPropertyID = DBPROP_IRowsetChange;  
rgRowsetProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[1].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[1].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[1].vValue));  
rgRowsetProperties[1].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[1].vValue.boolVal = VARIANT_FALSE;  
  
DBPROPSET rgRowsetPropSet[1];  
rgRowsetPropSet[0].rgProperties = rgRowsetProperties  
rgRowsetPropSet[0].cProperties = 2  
rgRowsetPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
  
hr = pIOpenRowset->OpenRowset (NULL,  
   &TableID,  
   NULL,  
   IID_IRowset,  
   1,  
   rgRowsetPropSet  
   (IUnknown**)&pIRowset);  
```  

  
## <a name="see-also"></a> Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 
  
  
