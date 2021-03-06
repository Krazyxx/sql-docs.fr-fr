---
title: À l’aide de mots clés de chaîne de connexion avec SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [SQL Server Native Client], connection string keywords
- SQLNCLI, connection string keywords
- connection strings [SQL Server Native Client]
- SQL Server Native Client, connection string keywords
ms.assetid: 16008eec-eddf-4d10-ae99-29db26ed6372
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 26400946d2ea9e656a659bf9d3a761fa0e5e8f74
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65095899"
---
# <a name="using-connection-string-keywords-with-sql-server-native-client"></a>Utilisation de mots clés de chaîne de connexion avec SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Certaines API [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilisent des chaînes de connexion pour spécifier des attributs de connexion. Les chaînes de connexion sont des listes de mots clés et de valeurs associées ; chaque mot clé identifie un attribut de connexion particulier.  

> [!IMPORTANT]
> Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB (SQLNCLI) reste déconseillée et il n’est pas recommandé de l’utiliser pour les nouveaux travaux de développement. Au lieu de cela, utilisez la nouvelle [Microsoft OLE DB Driver pour SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) qui seront mises à jour avec les fonctionnalités de serveur les plus récentes.    
> Pour plus d’informations, consultez [à l’aide de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](../../../connect/oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).

> [!NOTE]
> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client autorise l'ambiguïté dans les chaînes de connexion afin de maintenir la compatibilité descendante (par exemple, certains mots clés peuvent être spécifiés plusieurs fois et des mots clés en conflit peuvent être autorisés avec la résolution en fonction de la position ou de la précédence). Lors de la modification d'applications, il est conseillé d'utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client pour éliminer toute dépendance vis-à-vis de l'ambiguïté de chaîne de connexion.  
  
 Les sections suivantes décrivent les mots clés qui peuvent être utilisés avec le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et ActiveX Data Objects (ADO) lors de l'utilisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client comme fournisseur de données.  
  
## <a name="odbc-driver-connection-string-keywords"></a>Mots-clés de chaîne de connexion de pilote ODBC  
 Les applications ODBC utilisent des chaînes de connexion comme paramètres le [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) et [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) fonctions.  
  
 Les chaînes de connexion utilisées par ODBC ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre accolades, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs d'attributs contiennent des signes non alphanumériques. Il est supposé que la première accolade fermante dans la valeur termine la valeur ; par conséquent, les valeurs ne peuvent pas contenir de caractères d'accolade fermante.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec une chaîne de connexion ODBC.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|**Addr**|Synonyme de « Address ».|  
|**Adresse**|Adresse réseau du serveur exécutant une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **Address** est généralement le nom réseau du serveur, mais il peut s’agir d’autres noms tels qu’un canal, une adresse IP ou un port TCP/IP et une adresse de socket.<br /><br /> Si vous spécifiez une adresse IP, assurez-vous que les protocoles TCP/IP ou de canaux nommés sont activés dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La valeur de **adresse** est prioritaire sur la valeur passée à **Server** dans les chaînes de connexion ODBC lors de l’utilisation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Notez également que `Address=;` se connecte au serveur spécifié dans le mot clé **Server**, tandis que `Address= ;, Address=.;`, `Address=localhost;` et `Address=(local);` entraîne tous l’établissement d’une connexion au serveur local.<br /><br /> La syntaxe complète du mot clé **Address** est la suivante :<br /><br /> [_protocol_**:**]*Address*[**,**_port &#124;\pipe\pipename_]<br /><br /> Le*protocole* peut avoir la valeur **tcp** (TCP/IP), **lpc** (mémoire partagée) ou **np** (canaux nommés). Pour plus d’informations sur les protocoles, consultez [configurer des protocoles clients](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Si ni *protocole* ni le **réseau** mot clé est spécifié, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise l’ordre des protocoles spécifié dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* est le port auquel se connecter, sur le serveur spécifié. Par défaut, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le port 1433.|  
|**AnsiNPW**|Lorsque la valeur « yes » est spécifiée, le pilote utilise les comportements ANSI pour gérer les comparaisons NULL, le remplissage des données caractères, les avertissements et la concaténation de NULL. Lorsque la valeur « no » est spécifiée, les comportements ANSI ne sont pas exposés. Pour plus d’informations sur les comportements ANSI NPW, consultez [effets des Options ISO](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|**APP**|Nom de l’application qui appelle [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) (facultatif). Si spécifié, cette valeur est stockée dans le **master.dbo.sysprocesses** colonne **nom_programme** et est retourné par [sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) et [APP_NAME](../../../t-sql/functions/app-name-transact-sql.md)fonctions.|  
|**ApplicationIntent**|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**. La valeur par défaut est **ReadWrite**.  Exemple :<br /><br /> `ApplicationIntent=ReadOnly`<br /><br /> Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prise en charge du Client natif de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [SQL Server Native Client prend en charge pour la haute disponibilité, récupération d’urgence](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|Nom du fichier primaire d'une base de données qui peut être attachée. Incluez le chemin d'accès complet et échappez tout caractère \ lors de l'utilisation d'une variable de chaîne de caractères C :<br /><br /> `AttachDBFileName=c:\\MyFolder\\MyDB.mdf`<br /><br /> Cette base de données est attachée et devient la base de données par défaut de la connexion. Pour utiliser **AttachDBFileName** vous devez également spécifier le nom de la base de données dans un le [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) paramètre de la base de données ou la connexion sql_copt_current_catalog. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas ; il utilise la base de données attachée comme valeur par défaut pour la connexion.|  
|**AutoTranslate**|Lorsque la valeur « yes » est spécifiée, les chaînes de caractères ANSI transmises entre le client et le serveur sont converties au format Unicode afin de réduire les problèmes lors de la correspondance des caractères étendus entre les pages de codes sur le client et le serveur.<br /><br /> Données SQL_C_CHAR clientes envoyées à un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **char**, **varchar**, ou **texte** colonne, paramètre ou variable est converties du format caractère Unicode à l’aide du client Page de codes ANSI (ACP), puis sont converties du Unicode pour des caractères à l’aide de la page de codes ANSI du serveur.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **char**, **varchar**, ou **texte** données envoyées à une variable SQL_C_CHAR cliente sont converties du format caractère Unicode à l’aide de la page de codes ANSI du serveur, puis sont converties du format Unicode à l’aide du client de caractères PAGE DE CODES ANSI.<br /><br /> Ces conversions sont effectuées sur le client par le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Cela requiert que la page de codes ANSI utilisée sur le serveur soit disponible sur le client.<br /><br /> Ces paramètres n'ont aucun effet sur les conversions effectuées pour les transferts suivants :<br /><br /> \* Les données de client Unicode SQL_C_WCHAR envoyées à **char**, **varchar**, ou **texte** sur le serveur.<br /><br /> &#42;**char**, **varchar**, ou **texte** les données de serveur envoyées à une variable Unicode SQL_C_WCHAR sur le client.<br /><br /> \* Les données de client ANSI SQL_C_CHAR envoyées au format Unicode **nchar**, **nvarchar**, ou **ntext** sur le serveur.<br /><br /> \* Unicode **nchar**, **nvarchar**, ou **ntext** les données de serveur envoyées à une variable ANSI SQL_C_CHAR sur le client.<br /><br /> Lorsque la valeur « no » est spécifiée, la conversion de caractère n'est pas effectuée.<br /><br /> Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client ne traduit pas les données SQL_C_CHAR clientes ANSI envoyées à **char**, **varchar**, ou **texte** variables, des paramètres ou les colonnes sur le serveur. Aucune traduction n’est effectuée sur **char**, **varchar**, ou **texte** données envoyées à partir du serveur aux variables SQL_C_CHAR sur le client.<br /><br /> Si le client et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisent des pages de codes ANSI différentes, les caractères étendus peuvent être mal interprétés.|  
|**Sauvegarde de la base de données**|Nom de la base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par défaut utilisée pour la connexion. Si **base de données** n’est pas spécifié, la base de données par défaut définie pour la connexion est utilisée. La base de données par défaut de la source de données ODBC remplace la base de données par défaut définie pour la connexion. La base de données doit être une base de données existante, sauf si **AttachDBFileName** est également spécifié. Si **AttachDBFileName** est également spécifié, le fichier primaire, il pointe vers est attaché et le nom de la base de données spécifié par **base de données**.|  
|**Driver**|Nom du pilote tel que retourné par [SQLDrivers](../../../relational-databases/native-client-odbc-api/sqldrivers.md). La valeur de mot clé pour le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est « {SQL Server Native Client 11.0} ». Le **Server** mot clé est requise si **pilote** est spécifié et **DriverCompletion** est définie sur SQL_DRIVER_NOPROMPT.<br /><br /> Pour plus d’informations sur les noms de pilote, consultez [à l’aide de l’en-tête SQL Server Native Client et les fichiers de la bibliothèque](../../../relational-databases/native-client/applications/using-the-sql-server-native-client-header-and-library-files.md).|  
|**DSN**|Nom d'une source de données utilisateur ou système ODBC existante. Ce mot clé remplace toutes les valeurs qui peuvent être spécifiés dans le **Server**, **réseau**, et **adresse** mots clés.|  
|**Encrypt**|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».|  
|**Fallback**|Ce mot clé est déconseillé et sa valeur est ignorée par le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**Failover_Partner**|Nom du partenaire de basculement à utiliser s'il est impossible d'établir une connexion au serveur principal.|  
|**FailoverPartnerSPN**|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le pilote.|  
|**FileDSN**|Nom d'une source de données de fichier ODBC existante.|  
|**Langage**|Nom de la langue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (facultatif). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut stocker des messages pour plusieurs langues dans **sysmessages**. Si vous vous connectez à un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec plusieurs langues, **langage** Spécifie le jeu de messages sont utilisés pour la connexion.|  
|**MARS_Connection**|Active ou désactive MARS (Multiple Active Result Set) sur la connexion. Les valeurs reconnues sont « yes » et « no ». La valeur par défaut est « no ».|  
|**MultiSubnetFailover**|Spécifiez toujours **multiSubnetFailover = Yes** lors de la connexion à l’écouteur de groupe de disponibilité d’un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] groupe de disponibilité ou un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance de Cluster de basculement. **multiSubnetFailover = Yes** configure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client pour fournir une détection plus rapide et une connexion au serveur (actuellement) actif. Les valeurs possibles sont **Yes** et **No**. La valeur par défaut est **No**. Exemple :<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prise en charge du Client natif de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [SQL Server Native Client prend en charge pour la haute disponibilité, récupération d’urgence](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**Net**|Synonyme de « Network ».|  
|**Network**|Les valeurs valides sont **dbnmpntw** (canaux nommés) et **dbmssocn** (TCP/IP).<br /><br /> C’est une erreur pour spécifier à la fois une valeur pour le **réseau** mot clé et un protocole de préfixe sur le **Server** mot clé.|  
|**PWD**|Mot de passe du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] spécifié dans le paramètre UID. **PWD** ne doivent pas être spécifié si la connexion a un mot de passe NULL ou lors de l’utilisation de l’authentification Windows (`Trusted_Connection = yes`).|  
|**QueryLog_On**|Lorsque la valeur « yes » est spécifiée, l'enregistrement des données de requêtes longues est activé sur la connexion. Lorsque la valeur « no » est spécifiée, les données de requêtes longues ne sont pas enregistrées dans le journal.|  
|**QueryLogFile**|Chemin d'accès complet et nom de fichier d'un fichier à utiliser pour l'enregistrement des données sur les requêtes longues.|  
|**QueryLogTime**|Chaîne de caractères numérique spécifiant le seuil d'enregistrement (en millisecondes) des requêtes longues. Toute requête qui n'obtient pas de réponse dans les délais spécifiées est écrite dans le fichier journal de requêtes longues.|  
|**QuotedId**|Lorsque la valeur « yes » est spécifiée, QUOTED_IDENTIFIERS est défini à ON pour la connexion, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise les règles ISO concernant l'utilisation de guillemets dans les instructions SQL. Lorsque la valeur « no » est spécifiée, QUOTED_IDENTIFIERS est défini à OFF pour la connexion. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise dans ce cas les règles [!INCLUDE[tsql](../../../includes/tsql-md.md)] héritées concernant l'utilisation de guillemets dans les instructions SQL. Pour plus d’informations, consultez [effets des Options ISO](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|**Regional**|Lorsque la valeur « yes » est spécifiée, le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise les paramètres du client pour convertir monnaie, date et heure en données caractères. La conversion est unidirectionnelle uniquement ; le pilote ne reconnaît pas les formats standard non-ODBC pour les chaînes de date ou les valeurs monétaires contenues par exemple dans un paramètre utilisé dans une instruction INSERT ou UPDATE. Lorsque la valeur « no » est spécifiée, le pilote utilise les chaînes standard ODBC pour représenter les données de monnaie, date et heure converties en données caractères.|  
|**SaveFile**|Nom d'un fichier source de données ODBC dans lequel les attributs de la connexion actuelle sont enregistrés si la connexion réussit.|  
|**Server**|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La valeur doit être le nom d'un serveur sur le réseau, une adresse IP ou le nom d'un alias du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Le **adresse** mot clé substitue le **Server** mot clé.<br /><br /> Vous pouvez vous connecter à l’instance par défaut sur le serveur local en spécifiant l’un des éléments suivants :<br /><br /> **Server=;**<br /><br /> **Server=.;**<br /><br /> **Server=(local);**<br /><br /> **Server=(local);**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(localdb)\\** _instancename_ **;**<br /><br /> Pour plus d’informations sur la prise en charge de la base de données locale, consultez [SQL Server Native Client prend en charge pour la base de données locale](../../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md).<br /><br /> Pour spécifier une instance nommée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ajouter **\\** _InstanceName_.<br /><br /> Si aucun serveur n'est spécifié, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Si vous spécifiez une adresse IP, assurez-vous que les protocoles TCP/IP ou de canaux nommés sont activés dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La syntaxe complète du mot clé **Server** est la suivante :<br /><br /> **Server=**[_protocol_**:**]*Server*[**,**_port_]<br /><br /> Le*protocole* peut avoir la valeur **tcp** (TCP/IP), **lpc** (mémoire partagée) ou **np** (canaux nommés).<br /><br /> Voici un exemple de spécification d'un canal nommé :<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Cette ligne spécifie le protocole de canal nommé, un canal nommé sur l'ordinateur local (`\\.\pipe`), le nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) et le nom par défaut du canal nommé (`sql/query`).<br /><br /> Si ni un *protocole* ni le **réseau** mot clé est spécifié, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise l’ordre des protocoles spécifié dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* est le port auquel se connecter, sur le serveur spécifié. Par défaut, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le port 1433.<br /><br /> Les espaces sont ignorés au début de la valeur passée à **Server** dans les chaînes de connexion ODBC lors de l’utilisation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**ServerSPN**|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le pilote.|  
|**StatsLog_On**|Lorsque la valeur « yes » est spécifiée, active la capture de données de performances du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Lorsque la valeur « no » est spécifiée, les données de performances du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ne sont pas disponibles sur la connexion.|  
|**StatsLogFile**|Chemin d'accès complet et nom de fichier d'un fichier utilisé pour enregistrer les statistiques de performances du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**Trusted_Connection**|Lorsque la valeur « yes » est spécifiée, fait en sorte que le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le mode d'authentification Windows pour la validation de connexion. Autrement, fait en sorte que le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise un nom d'utilisateur et un mot de passe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour la validation de connexion, et les mots clés UID et PWD doivent être spécifiés.|  
|**TrustServerCertificate**|Lorsqu’il est utilisé avec **Encrypt**, Active le chiffrement à l’aide d’un certificat de serveur auto-signé.|  
|**UID**|Compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] valide. Il n'est pas nécessaire de spécifier l'UID lors de l'utilisation de l'authentification Windows.|  
|**UseProcForPrepare**|Ce mot clé est déconseillé et sa valeur est ignorée par le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC du Client natif.|  
|**WSID**|ID de station de travail. En général, il s'agit du nom réseau de l'ordinateur sur lequel l'application réside (facultatif). Si spécifié, cette valeur est stockée dans le **master.dbo.sysprocesses** colonne **nom d’hôte** et est retourné par [sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) et [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md)(fonction).|  
  
> **REMARQUE :** Les paramètres de conversion régionaux s'appliquent aux types de données monétaire, numérique, date et heure. Le paramètre de conversion est applicable uniquement à la conversion sortante et est visible uniquement lorsque des valeurs de monnaie, numériques, de date ou d'heure sont converties en chaînes de caractères.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise les paramètres régionaux du Registre pour l'utilisateur actuel. Le pilote n’honore pas les paramètres régionaux du thread actuel si l’application définit après une connexion par, par exemple, l’appel **SetThreadLocale**.  
  
 La modification du comportement régional d'une source de données peut provoquer l'échec de l'application. Une application qui analyse des chaînes de date et s'attend à ce qu'elles apparaissent comme défini par ODBC pourrait être affectée de manière négative par la modification de cette valeur.  
  
## <a name="ole-db-provider-connection-string-keywords"></a>Mots clés de chaîne de connexion du fournisseur OLE DB  
 Il existe deux manières pour les applications OLE DB d'initialiser des objets source de données :  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 Dans le premier cas, une chaîne du fournisseur peut être utilisée pour initialiser des propriétés de connexion en définissant la propriété DBPROP_INIT_PROVIDERSTRING dans le jeu de propriétés DBPROPSET_DBINIT. Dans le deuxième cas, une chaîne d’initialisation peut être passée à la méthode **IDataInitialize::GetDataSource** pour initialiser des propriétés de connexion. Les deux méthodes initialisent les mêmes propriétés de connexion OLE DB, mais des jeux de mots clés différents sont utilisés. L’ensemble de mots clés utilisé par **IDataInitialize::GetDataSource** est au minimum la description des propriétés présentes dans le groupe de propriétés d’initialisation.  
  
 Lorsqu'un paramètre de chaîne du fournisseur qui a une propriété OLE DB correspondante définie à une certaine valeur par défaut ou explicitement définie avec une valeur, la valeur de la propriété OLE DB remplace le paramètre dans la chaîne du fournisseur.  
  
 Les propriétés booléennes définies dans les chaînes du fournisseur via des valeurs DBPROP_INIT_PROVIDERSTRING sont définies à l'aide des valeurs « yes » et « no ». Les propriétés booléennes définies dans les chaînes d’initialisation à l’aide de **IDataInitialize::GetDataSource** sont définies à l’aide des valeurs « true » et « false ».  
  
 Les applications qui utilisent **IDataInitialize::GetDataSource** peuvent également utiliser les mots clés utilisés par **IDBInitialize::Initialize**, mais uniquement pour les propriétés qui n’ont pas de valeur par défaut. Si une application utilise à la fois le mot clé **IDataInitialize::GetDataSource** et le mot clé **IDBInitialize::Initialize** dans la chaîne d’initialisation, le paramètre de mot clé **IDataInitialize::GetDataSource** est utilisé. Il est fortement recommandé que les applications n’utilisent pas de mots clés **IDBInitialize::Initialize** dans les chaînes de connexion **IDataInitialize:GetDataSource**, car ce comportement peut ne pas être conservé dans les versions ultérieures.  
  
> [!NOTE]  
>  Une chaîne de connexion passée via **IDataInitialize::GetDataSource** est convertie en propriétés et appliquée via **IDBProperties::SetProperties**. Si les services de composants ont trouvé la description de la propriété dans **IDBProperties::GetPropertyInfo**, cette propriété sera appliquée comme une propriété autonome. Sinon, elle sera appliquée par le biais de la propriété DBPROP_PROVIDERSTRING. Par exemple, si vous spécifiez la chaîne de connexion **Data Source = server1 ; Serveur = Serveur2**, **Source de données** est défini en tant que propriété, mais **Server** passera à une chaîne de fournisseur.  
  
 Si vous spécifiez plusieurs instances de la même propriété spécifique au fournisseur, la première valeur de la première propriété est utilisée.  
  
 Les chaînes de connexion utilisées par les applications OLE DB utilisant DBPROP_INIT_PROVIDERSTRING avec **IDBInitialize::Initialize** ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre accolades, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs d'attributs contiennent des signes non alphanumériques. Il est supposé que la première accolade fermante dans la valeur termine la valeur ; par conséquent, les valeurs ne peuvent pas contenir de caractères d'accolade fermante.  
  
 Un espace après le signe égal (=) d’un mot clé de chaîne de connexion sera interprété comme un littéral, même si la valeur est placée entre guillemets.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec DBPROP_INIT_PROVIDERSTRING.  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|Synonyme de « Address ».|  
|**Adresse**|SSPROP_INIT_NETWORKADDRESS|Adresse réseau d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description de la **adresse** ODBC mot clé, plus loin dans cette rubrique.|  
|**APP**|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**.<br /><br /> La valeur par défaut est **ReadWrite**. Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prise en charge du Client natif de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [SQL Server Native Client prend en charge pour la haute disponibilité, récupération d’urgence](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser **AttachDBFileName**, vous devez également spécifier le nom de la base de données avec le mot clé Database de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|**Traduire automatiquement**|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « yes » et « no ».|  
|**Sauvegarde de la base de données**|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données à utiliser. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données SQL Server 2000.|  
|**Encrypt**|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|**Langage**|SSPROPT_INIT_CURRENTLANGUAGE|Langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion si le serveur est [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».|  
|**Net**|SSPROP_INIT_NETWORKLIBRARY|Synonyme de « Network ».|  
|**Network**|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Synonyme de « Network ».|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « yes » et « no » comme valeurs. Lorsque « no » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes|  
|**PWD**|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description de la **Server** ODBC mot clé, dans cette rubrique.|  
|**ServerSPN**|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|**Délai d'expiration**|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Lorsque la valeur « yes » est spécifiée, fait en sorte que le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le mode d'authentification Windows pour la validation de connexion. Autrement, fait en sorte que le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise un nom d'utilisateur et un mot de passe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour la validation de connexion, et les mots clés UID et PWD doivent être spécifiés.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « yes » et « no » comme valeurs. La valeur par défaut est « no », ce qui signifie que le certificat de serveur sera validé.|  
|**UID**|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Ce mot clé est déconseillé et sa valeur est ignorée par le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**WSID**|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
 Les chaînes de connexion utilisées par les applications OLE DB utilisant **IDataInitialize::GetDataSource** ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 L'utilisation des propriétés doit être conforme à la syntaxe autorisée dans l'étendue.  Par exemple, **WSID** utilise des accolades (**{}**) caractères de guillemets et **nom de l’Application** utilise unique (**'**) ou Double (**»**) caractères. Seules les propriétés de chaîne peuvent être mises entre guillemets. Si vous tentez de placer entre guillemets un entier ou une propriété énumérée, une erreur indiquant que la chaîne de connexion n'est pas conforme à la spécification OLE DB sera générée.  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre guillemets simples ou doubles, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs contiennent des caractères non alphanumériques. Le caractère de guillemet utilisé peut également apparaître dans des valeurs, à condition d'être doublé.  
  
 Un espace après le signe égal (=) d’un mot clé de chaîne de connexion sera interprété comme un littéral, même si la valeur est placée entre guillemets.  
  
 Si une chaîne de connexion a plusieurs des propriétés répertoriées dans le tableau suivant, la valeur de la dernière propriété sera utilisée.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec **IDataInitialize::GetDataSource** :  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|**Application Name**|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|**Intention de l’application**|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**.<br /><br /> La valeur par défaut est **ReadWrite**. Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prise en charge du Client natif de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [SQL Server Native Client prend en charge pour la haute disponibilité, récupération d’urgence](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**Traduire automatiquement**|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « true » et « false ».|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|Nom de la langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Source de données**|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description de la **Server** ODBC mot clé, plus loin dans cette rubrique.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données à utiliser. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|**Catalogue initial**|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|**Nom de fichier initial**|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser **AttachDBFileName**, vous devez également spécifier le nom de la base de données avec le mot clé DATABASE de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|**Sécurité intégrée**|DBPROP_AUTH_INTEGRATED|Accepte la valeur « SSPI » pour l'authentification Windows.|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion. Les valeurs reconnues sont « true » et « false ». La valeur par défaut est « false ».|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Adresse réseau d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description de la **adresse** ODBC mot clé, plus loin dans cette rubrique.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|**Mot de passe**|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « true » et « false » comme valeurs. Lorsque « false » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes|  
|**Fournisseur**||Pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ce doit être « SQLNCLI11 ».|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|**Faire confiance au certificat de serveur**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « true » et « false » comme valeurs. La valeur par défaut est « false », ce qui signifie que le certificat de serveur sera validé.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».|  
|**ID d'utilisateur**|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Workstation ID**|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
 **Remarque** Dans la chaîne de connexion, la propriété « Ancien Mot de passe » définit SSPROP_AUTH_OLD_PASSWORD, qui correspond au mot de passe actuel (éventuellement périmé) qui n’est pas disponible via une propriété de chaîne de fournisseur.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Mots clés de chaîne de connexion ActiveX Data Objects (ADO)  
 Les applications ADO définissent la propriété **ConnectionString** des objets **ADODBConnection** ou fournissent une chaîne de connexion comme paramètre à la méthode **Open** des objets **ADODBConnection**.  
  
 Les applications ADO peuvent également utiliser les mots clés utilisés par la méthode OLE DB **IDBInitialize::Initialize**, mais uniquement pour les propriétés qui n’ont pas de valeur par défaut. Si une application utilise à la fois les mots clés ADO et les mots clés **IDBInitialize::Initialize** dans la chaîne d’initialisation, le paramètre de mot clé ADO est utilisé. Il est vivement recommandé que les applications utilisent uniquement des mots clés de chaîne de connexion ADO.  
  
 Les chaînes de connexion utilisées par ADO ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre guillemets doubles, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs contiennent des caractères non alphanumériques. Les valeurs d'attributs ne peuvent pas contenir de guillemets doubles.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec une chaîne de connexion ADO :  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|**Intention de l’application**|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**.<br /><br /> La valeur par défaut est **ReadWrite**. Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prise en charge du Client natif de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [SQL Server Native Client prend en charge pour la haute disponibilité, récupération d’urgence](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**Application Name**|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|**Traduire automatiquement**|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « true » et « false ».|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|Nom de la langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Source de données**|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description de la **Server** ODBC mot clé, dans cette rubrique.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données qui sera utilisé. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données SQL Server 2000.|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|**Catalogue initial**|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|**Nom de fichier initial**|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser **AttachDBFileName**, vous devez également spécifier le nom de la base de données avec le mot clé DATABASE de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|**Sécurité intégrée**|DBPROP_AUTH_INTEGRATED|Accepte la valeur « SSPI » pour l'authentification Windows.|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion si le serveur est [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure. Les valeurs reconnues sont « true » et « false ». La valeur par défaut est « false ».|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Adresse réseau d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description de la **adresse** ODBC mot clé, dans cette rubrique.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|**Mot de passe**|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « true » et « false » comme valeurs. Lorsque « false » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes.|  
|**Fournisseur**||Pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ce doit être « SQLNCLI11 ».|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide fait en sorte que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilise le nom principal de service par défaut généré par le fournisseur.|  
|**Faire confiance au certificat de serveur**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « true » et « false » comme valeurs. La valeur par défaut est « false », ce qui signifie que le certificat de serveur sera validé.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».|  
|**ID d'utilisateur**|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Workstation ID**|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
 **Remarque** Dans la chaîne de connexion, la propriété « Ancien Mot de passe » définit SSPROP_AUTH_OLD_PASSWORD, qui correspond au mot de passe actuel (éventuellement périmé) qui n’est pas disponible via une propriété de chaîne de fournisseur.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
