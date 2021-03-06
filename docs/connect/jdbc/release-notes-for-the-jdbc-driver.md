---
title: Notes de publication pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 04/16/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5e75f732fc44ee339cb3d9d47518627f264cb8cc
ms.sourcegitcommit: e2d65828faed6f4dfe625749a3b759af9caa7d91
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59671335"
---
# <a name="release-notes-for-the-microsoft-jdbc-driver"></a>Notes de publication pour le pilote JDBC Microsoft

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet article répertorie les versions du _pilote JDBC Microsoft pour SQL Server_. Pour chaque version publiée, les modifications sont nommées et décrites.

## <a name="722"></a>7.2.2

### <a name="compliance"></a>Conformité

16 avril 2019

| Modification de conformité | Détails |
| :---------------- | :------ |
| Téléchargez les dernières mises à jour du pilote JDBC 7.2. | &bull; &nbsp; [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=2063159)<br/>&bull; &nbsp; [GitHub, 7.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v7.2.2)<br/>&bull; &nbsp; [Maven Central](https://search.maven.org/search?q=g:com.microsoft.sqlserver) |
| Entièrement conforme à la spécification de l’API JDBC 4.2. | Les fichiers JAR dans le package 7.2 sont nommés en fonction de la compatibilité des versions de Java.<br/><br/>Par exemple, le fichier mssql-jdbc-7.2.2.jre11.jar du package 7.2 doit être utilisé avec Java 11. |
| Compatible avec JDK (Java Development Kit) version 11.0 en plus de JDK 1.8. | Le pilote JDBC Microsoft 7.2 pour SQL Server est désormais compatible avec JDK (Java Development Kit) version 11.0 en plus de JDK 1.8. |
| &nbsp; | &nbsp; |

> [!NOTE]
> Un problème relatif à l’analyse des instructions SQL a été détecté dans le pilote JDBC 7.2 Release To Web (RTW) publié le 31 janvier 2019. La modification a été annulée et de nouveaux fichiers JAR (version 7.2.1) ont été publiés le 11 février 2019.
>
> Une autre mise à jour a été effectuée sur le pilote pour résoudre les problèmes liés au fait que les identifiants ActivityID ne sont pas nettoyés correctement. Les nouveaux fichiers JAR (version 7.2.2) ont été publiés le 16 avril 2019.
> 
> Nous vous recommandons de mettre à jour vos projets pour utiliser la version 7.2.2 des fichiers JAR. Pour plus d’informations, voir les notes de version pour [GitHub, 7.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v7.2.1) et [GitHub, 7.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v7.2.2).

### <a name="active-directory-managed-service-identity-msi-authentication"></a>Authentification Azure Active Directory _Managed Service Identity_ (MSI).

| Changement MSI | Détails |
| :--------- | :------ |
| Prend en charge le mode d’authentification Active Directory Managed Service Identity (MSI). | Ce mode d’authentification est applicable aux ressources Azure avec prise en charge de la fonctionnalité « Identité » activée.<br/><br/>Les deux types d’identités de système managé (MSI) sont pris en charge par le pilote pour acquérir **accessToken** afin d’établir une connexion sécurisée. |
| Plus de détails et un exemple d’application pour utiliser ce mode d’authentification. | Consultez [Connexion avec l’authentification Azure Active Directory](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md). |
| &nbsp; | &nbsp; |

### <a name="introduces-open-service-gateway-initiative-osgi-support"></a>Introduit la prise en charge d’_Open Service Gateway Initiative_ (OSGi)

| Modification de l’OSGi | Détails |
| :---------- | :------ |
| Implémentation **DataSourceFactory** ajoutée. | &bull; &nbsp; `org.osgi.service.jdbc.DataSourceFactory`)<br/>&bull; &nbsp; `com.microsoft.sqlserver.jdbc.osgi.SQLServerDataSourceFactory`) |
| Implémentation **Activateur** ajoutée. | &bull; &nbsp; `org.osgi.framework.BundleActivator`)<br/>&bull; &nbsp; `com.microsoft.sqlserver.jdbc.osgi.Activator`) |
| &nbsp; | &nbsp; |

### <a name="introduces-sqlservererror-apis"></a>Introduit les API _SQLServerError_

| Modification de l’API d’erreur | Détails |
| :--------------- | :------ |
| Introduction de l’API SQLServerError. | API getter pour récupérer des détails supplémentaires sur l’erreur générée à partir du serveur.<br/><br/>&bull; &nbsp; `SQLServerException.getSQLServerError()`)<br/>&bull; &nbsp; `SQLServerError`) |
| Détails supplémentaires. | Consultez [Gestion des erreurs](../../connect/jdbc/handling-errors.md). |
| &nbsp; | &nbsp; |

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-163"></a>Mise à jour de la _bibliothèque d’authentification Microsoft Azure Active Directory (ADAL4J) pour Java_, version 1.6.3

| Modification d’ADAL4J | Détails |
| :------------ | :------ |
| Mise à jour de la dépendance Maven sur ADAL4J vers la version 1.6.3. | &nbsp; |
| Introduit _exécution du Client Java pour AutoRest_ comme une dépendance Maven, version 1.6.5). | &nbsp; |
| Détails supplémentaires. | Consultez [Dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="updated-microsoft-azure-key-vault-sdk-for-java-version-120"></a>Mise à jour du _kit de développement logiciel (SDK) Microsoft Azure Key Vault pour Java_, version 1.2.0

| Modification du SDK Key Vault | Détails |
| :------------------- | :------ |
| Mise à jour de la dépendance Maven sur le _kit de développement logiciel (SDK) Microsoft Azure Key Vault pour Java_ vers la version 1.2.0. | &nbsp; |
| Présente _Microsoft Azure SDK pour Key Vault WebKey_ en tant que dépendance Maven, version 1.2.0. | &nbsp; |
| Détails supplémentaires. | Consultez [Dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus

| Problèmes connus | Détails |
| :----------- | :------ |
| Requêtes paramétrables, dans certains cas. | v7.2.1, une mise à jour de la version 7.2.0, a été publiée en février 2019 pour résoudre ce problème. |
| Nettoyage d’ActivityId. | v7.2.2, une mise à jour de la version 7.2.1, a été publiée en avril 2019 pour résoudre ce problème. |
| &nbsp; | &nbsp; |

## <a name="70"></a>7.0

Le pilote JDBC 7.0 Microsoft pour SQL Server est parfaitement conforme à la spécification de l’API JDBC 4.2. Les fichiers JAR dans le package 7.0 sont nommés en fonction de la compatibilité avec les versions de Java. Par exemple, le fichier mssql-jdbc-7.0.0.jre10.jar du package 7.0 doit être utilisé avec Java 10.

### <a name="support-for-jdk-10"></a>Prise en charge de JDK 10

Le pilote JDBC Microsoft 7.0 pour SQL Server est désormais compatible avec JDK (Java Development Kit) version 10.0 en plus de JDK 1.8. Cette mise à jour expose également le `Automatic-Module-Name` du pilote en tant que `com.microsoft.sqlserver.jdbc` via son fichier MANIFESTE.

### <a name="support-for-spatial-datatypes"></a>Prise en charge des types de données spatiaux

Le pilote JDBC 7.0 Microsoft pour SQL Server prend désormais en charge les types de données spatiales Géographie et Géométrie de SQL Server. Pour plus d’informations sur les API des types de données spatiales et la façon de les utiliser, consultez [Utilisation des types de données spatiales](../../connect/jdbc/use-spatial-datatypes.md).

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>Implémentation des API java.sql.Connection beginRequest() et endRequest() introduites dans JDBC 4.3

Le pilote JDBC 7.0 Microsoft pour SQL Server implémente maintenant les API `beginRequest()` et `endRequest()` à partir de la classe `java.sql.Connection`. Ces API ont été introduites avec les spécifications JDBC 4.3 et JDK 9. Pour plus d’informations sur l’implémentation du pilote de ces API, consultez [Conformité de JDBC 4.3 pour le pilote JDBC](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="support-for-sql-data-discovery-and-classification"></a>Prise en charge de la découverte et de la classification des données SQL

Le pilote JDBC 7.0 Microsoft pour SQL Server fournit un support pour la détection et la classification de données SQL avec une base de données cible prenant en charge cette fonctionnalité. Le pilote expose désormais des API `SQLServerResultSet.getSensitivityClassification()` pour extraire ces informations à partir de `ResultSet` récupéré.

Pour plus d’informations sur la façon d’utiliser cette fonctionnalité avec le pilote JDBC, consultez l’exemple dans [Détection et classification de données SQL](../../connect/jdbc/data-discovery-classification-sample.md).

### <a name="added-connection-property-usebulkcopyforbatchinsert"></a>Ajout d’une propriété de connexion : useBulkCopyForBatchInsert

Le pilote JDBC 7.0 Microsoft pour SQL Server introduit une nouvelle propriété de connexion, `useBulkCopyForBatchInsert`. Cette propriété est prise en charge uniquement pour Azure SQL Data Warehouse.

Elle est désactivée par défaut. Vous pouvez l’activer pour augmenter les performances des applications de l’utilisateur lorsque vous transmettez de grandes quantités de données à Azure SQL Data Warehouse. L’activation de cette propriété modifie le comportement des opérations d’insertion de lots pour passer à des opérations de copie en bloc avec des données fournies par l’utilisateur. Pour plus d’informations sur cette propriété et ses limitations, consultez [Utilisation de l’API de copie en bloc pour les opérations d’insertion de lots](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md).

### <a name="added-connection-property-cancelquerytimeout"></a>Ajout d’une propriété de connexion : cancelQueryTimeout

Le pilote JDBC 7.0 Microsoft pour SQL Server introduit une nouvelle propriété de connexion, `cancelQueryTimeout`, pour annuler `queryTimeout` sur les objets `java.sql.Connection` et `java.sql.Statement`.

### <a name="added-azure-key-vault-provider-constructors"></a>Ajout de constructeurs Azure Key Vault Provider

Le pilote JDBC 7.0 Microsoft pour SQL Server réintroduit un constructeur précédemment supprimé pour `SQLServerColumnEncryptionAzureKeyVaultProvider`. Il permettait l’authentification avec une méthode personnalisée implémentée via `SQLServerKeyVaultAuthenticationCallback` pour récupérer un jeton d’accès.

Les nouveaux constructeurs ont la définition suivante :

```java
/* This constructor is added to provide backward compatibility with 6.0
* version of the driver. It is marked deprecated for removal in the next
* stable release.
*/
@Deprecated
public SQLServerColumnEncryptionAzureKeyVaultProvider(
        SQLServerKeyVaultAuthenticationCallback authenticationCallback,
        ExecutorService executorService) throws SQLServerException;

/*New constructor to replace the above constructor*/
public SQLServerColumnEncryptionAzureKeyVaultProvider(
            SQLServerKeyVaultAuthenticationCallback authenticationCallback) throws SQLServerException;
```

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-160"></a>Mise à jour de la « bibliothèque d’authentification Microsoft Azure Active Directory (ADAL4J) pour Java » : version 1.6.0

Le pilote JDBC 7.0 Microsoft pour SQL Server a mis à jour sa dépendance Maven sur la « bibliothèque d'authentification Active Directory Microsoft Azure (ADAL4J) pour Java » vers la version 1.6.0. Pour plus d’informations sur les dépendances, consultez [Dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="64"></a>6.4

Le pilote JDBC 6.4 Microsoft pour SQL Server est parfaitement conforme aux spécifications JDBC 4.1. et 4.2. Les fichiers JAR dans le package 6.4 sont nommés en fonction de la compatibilité avec les versions de Java. Par exemple, le fichier mssql-jdbc-6.4.0.jre8.jar du package 6.4 doit être utilisé avec Java 8.

### <a name="support-for-jdk-9"></a>Prise en charge de JDK 9

Le pilote prend en charge JDK 9.0 en plus de JDK 8.0 et 7.0.

### <a name="jdbc-43-compliance"></a>Conformité avec JDBC 4.3

Le pilote prend en charge la spécification de l’API Java Database Connectivity 4.3, en plus des versions 4.1 et 4.2. Les méthodes de l’API JDBC 4.3 sont ajoutés, mais pas encore implémentés. Pour plus d’informations, consultez [Conformité à JDBC 4.3 pour le pilote JDBC](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="added-connection-property-sslprotocol"></a>Ajout d’une propriété de connexion : sslProtocol

Une nouvelle propriété de connexion permet aux utilisateurs de spécifier le mot clé du protocole TLS. Les valeurs possibles sont : « TLS », « TLSv1 », « TLSv1.1 » et « TLSv1.2 ». Pour plus d’informations, consultez [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol).

### <a name="deprecated-connection-property-fipsprovider"></a>Propriété de connexion dépréciée : fipsProvider

La propriété de connexion `fipsProvider` est supprimée de la liste des propriétés de connexion acceptées. Pour plus d’informations, consultez la [demande de tirage (pull request) GitHub](https://github.com/Microsoft/mssql-jdbc/pull/460).

### <a name="added-connection-properties-for-specifying-a-custom-trustmanager"></a>Ajout de propriétés de connexion pour spécifier un TrustManager personnalisé

Le pilote prend désormais en charge la spécification d’un TrustManager personnalisé grâce à l’ajout des propriétés de connexion `trustManagerClass` et `trustManagerConstructorArg`. Vous pouvez spécifier dynamiquement un ensemble de certificats approuvés sur une base par connexion sans modifier les paramètres globaux de l’environnement de machine virtuelle (JVM) Java.

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters"></a>Ajout d’une prise en charge pour datetime/smallDatetime dans les paramètres table

Le pilote prend désormais en charge les types de données `datetime` et `smallDatetime` lorsque vous utilisez des paramètres table (TVP).

### <a name="added-support-for-the-sqlvariant-datatype"></a>Ajout d’une prise en charge pour le type de données sql_variant

Le pilote JDBC prend désormais en charge les types de données `sql_variant` à utiliser avec SQL Server. Le type de données `sql_variant` est également pris en charge avec des fonctionnalités telles que les paramètres table et de copie en bloc, avec les limitations suivantes :

* **Pour les valeurs de date** : 

  Lorsque vous utilisez un paramètre de table (TVP) pour remplir une table qui contient des valeurs `datetime`, `smalldatetime` ou `date` stockées dans une colonne `sql_variant`, l’appel de la méthode `getDateTime()`, `getSmallDateTime()` ou `getDate()` ne fonctionne pas sur le jeu de résultats et lève l’exception suivante :

  `java java.lang.String cannot be cast to java.sql.Timestamp`
    
  Pour contourner ce problème, utilisez la méthode `getString()` ou `getObject()` à la place.

* **Utilisation d’un paramètre table (TVP) avec sql_variant pour les valeurs null** :
  
  Si vous utilisez un TVP pour remplir une table et envoyez une valeur NULL au type de colonne `sql_variant`, vous rencontrez une exception. L’insertion d’une valeur NULL avec le type de colonne `sql_variant` dans un TVP n’est actuellement pas prise en charge.

### <a name="implemented-prepared-statement-metadata-caching"></a>Implémentation de la mise en cache des métadonnées de l’instruction préparée

Le pilote JDBC a implémenté la mise en cache des métadonnées de l’instruction préparée pour améliorer les performances. Le pilote prend désormais en charge la mise en cache des métadonnées de l’instruction préparée dans le pilote avec les propriétés de connexion `disableStatementPooling` et `statementPoolingCacheSize`. Cette fonctionnalité est désactivée par défaut. Pour plus d’informations, consultez [Mise en cache des métadonnées de l’instruction préparée pour le pilote JDBC](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md).

### <a name="added-support-for-azure-ad-integrated-authentication-on-linuxmac"></a>Ajout de la prise en charge de l’authentification intégrée Azure AD sur Linux/Mac

Le pilote JDBC prend maintenant en charge l’authentification intégrée Azure Active Directory (Azure AD) sur tous les systèmes d’exploitation pris en charge (Windows, Linux et Mac) avec Kerberos. Sur les systèmes d’exploitation Windows, les utilisateurs peuvent également s’authentifier avec sqljdbc_auth.dll.

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-140"></a>Mise à jour de la « bibliothèque d’authentification Microsoft Azure Active Directory (ADAL4J) pour Java » : version 1.4.0

Le pilote JDBC a mis à jour sa dépendance Maven sur la « bibliothèque d'authentification Active Directory Microsoft Azure (ADAL4J) pour Java » vers la version 1.4.0. Pour plus d’informations sur les dépendances, consultez [Dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="62"></a>6.2

Le pilote JDBC 6.2 Microsoft pour SQL Server est parfaitement conforme aux spécifications JDBC 4.1. et 4.2. Les fichiers JAR dans le package 6.2 sont nommés en fonction de la compatibilité avec les versions de Java. Par exemple, l’utilisation du fichier mssql-jdbc-6.2.2.jre8.jar du package 6.2 est recommandée avec Java 8.

> [!NOTE]  
> Un problème lié à l’amélioration de la mise en cache de métadonnées a été trouvé dans JDBC 6.2 RTW, publié le 29 juin 2017. L’amélioration a été annulée et de nouveaux fichiers JAR (version 6.2.1) ont été publiés le 17 juillet 2017. 
>
> Une autre amélioration mis à niveau la version de bibliothèque dépendante d’Azure Key Vault à 1.0.0 et de nouveaux fichiers JAR (version 6.2.2) ont été publiés sur le 19 octobre 2017.
>
> Téléchargez les dernières mises à jour du pilote JDBC 6.2 à partir du [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=852460), de [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2) et de [Maven Central](https://search.maven.org/search?q=g:com.microsoft.sqlserver). Mettez à jour vos projets pour utiliser la version 6.2.2 des fichiers JAR. Pour plus d’informations, consultez les notes de publication pour [6.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) et [6.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2).

### <a name="azure-ad-support-for-linux"></a>Prise en charge d’Azure AD pour Linux

Connectez vos applications Linux à Azure SQL Database à l’aide de l’authentification Azure AD via les méthodes avec nom d’utilisateur/mot de passe et jeton d’accès.

### <a name="fips-enabled-jvms"></a>JVM compatible FIPS

Le pilote JDBC peut désormais être utilisé sur des machines virtuelles Java exécutées en mode de conformité avec les normes FIPS (Federal Information Processing Standard) 140 afin de respecter les normes fédérales sur la conformité.

### <a name="kerberos-authentication-improvements"></a>Améliorations apportées à l’authentification Kerberos

Le pilote JDBC prend désormais en charge ce qui suit :

- Méthode par principal/mot de passe pour les applications où la configuration de Kerberos ne peut pas être modifiée ou ne peut pas récupérer un jeton ou un fichier Keytab nouveau. Cette méthode peut être utilisée pour l’authentification auprès d’une instance SQL Server autorisant uniquement l’authentification Kerberos.
- Authentification interdomaine qui utilise l’authentification intégrée Kerberos sans définir explicitement le SPN du serveur. Le pilote calcule maintenant automatiquement le domaine, même s’il n’y en a pas.
- Délégation contrainte Kerberos par acceptation d’informations d'identification d’utilisateurs impersonnés en tant qu’objet d’informations d’identification GSS via la source de données. Ces informations d’identification avec emprunt d’identité sont ensuite utilisées pour établir une connexion Kerberos.

### <a name="added-timeouts"></a>Ajout de délais d’expiration

Le pilote JDBC prend désormais en charge les délais d’expiration configurables suivants. Vous pouvez les modifier selon les besoins de votre application.

- Délai d’expiration de requête pour contrôler le nombre de secondes à attendre avant un délai d’expiration lorsque vous exécutez une requête.
- Délai d’expiration de socket pour spécifier le nombre de millisecondes à attendre avant un délai d’expiration d’un socket lu ou accepté.

## <a name="61"></a>6.1

Le pilote JDBC 6.1 Microsoft pour SQL Server est parfaitement conforme aux spécifications JDBC 4.1. et 4.2. Il s’agit de la version open source initiale du pilote JDBC. Il contient les fichiers mssql-jdbc-6.1.0.jre8.jar et mssql-jdbc-6.1.0.jre7.jar, qui indiquent la compatibilité avec une version de Java.

## <a name="60"></a>6.0

Le pilote JDBC 6.0 Microsoft pour SQL Server est parfaitement conforme aux spécifications JDBC 4.1. et 4.2. Les fichiers JAR dans le package 6.0 sont nommés en fonction de leur conformité avec la version de l’API JDBC. Par exemple, le fichier sqljdbc42.jar du package 6.0 est compatible avec l’API JDBC 4.2. De même, le fichier sqljdbc41.jar est conforme à l’API JDBC 4.1.

Pour vous assurer d’avoir le bon fichier sqljdbc42.jar ou sqljdbc41.jar, exécutez les lignes de code suivantes. Si la sortie est « Version du pilote : 6.0.7507.100 », c’est que vous disposez du package du pilote JDBC 6.0.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Always Encrypted

Le pilote prend en charge la fonctionnalité Always Encrypted dans SQL Server 2016. Cette fonctionnalité garantit que les données sensibles ne soient jamais affichées comme texte en clair dans une instance de SQL Server. Always Encrypted chiffre les données de l’application de manière transparente, de sorte que SQL Server manipule uniquement les données chiffrées, et non des valeurs en texte clair. Même si l’instance SQL Server ou l’ordinateur hôte est compromis, la personne malveillante ne pourra récupérer qu’un texte chiffré des données sensibles. Pour plus d’informations, voir [Utiliser Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).

### <a name="internationalized-domain-names"></a>Noms de domaine internationaux

Le pilote prend en charge les noms de domaine internationaux (IDN) pour les noms des serveurs. Pour plus d’informations, consultez « Utilisation des noms de domaines internationaux » dans l’article [Fonctionnalités internationales du pilote JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md).

### <a name="parameterized-queries"></a>Requêtes paramétrables

Le pilote prend maintenant en charge la récupération des métadonnées de paramètres avec des instructions préparées pour les requêtes complexes, comme les sous-requêtes et/ou les jointures. Notez que cette amélioration est disponible uniquement quand vous utilisez SQL Server 2012 et des versions plus récentes.

### <a name="azure-active-directory"></a>Azure Active Directory

L’authentification Azure AD est un mécanisme de connexion à Azure SQL Database v12 à l’aide d’identités dans Azure AD. Utilisez l’authentification Azure AD pour gérer de manière centralisée les identités des utilisateurs de base de données et comme alternative à l’authentification SQL Server. 

Vous pouvez utiliser le pilote JDBC 6.0 pour spécifier vos informations d’identification Azure AD dans la chaîne de connexion JDBC afin de vous connecter à Azure SQL Database. Pour plus d’informations, consultez la propriété d’authentification dans l’article [Définition des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).

### <a name="table-valued-parameters"></a>Paramètres table

Les paramètres table (TVP) fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données. Vous pouvez utiliser des TVP pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique. Les lignes de données entrantes sont stockées dans une variable de table que vous pouvez ensuite utiliser à l’aide de Transact-SQL. Pour plus d’informations, consultez [Utilisation de paramètres table](../../connect/jdbc/using-table-valued-parameters.md).

### <a name="always-on-availability-groups"></a>Groupes de disponibilité Always On

Le pilote prend désormais en charge les connexions transparentes aux groupes de disponibilité Always On. Le pilote détecte rapidement la topologie Always On actuelle de votre infrastructure serveur et se connecte au serveur actif de manière transparente.

## <a name="42"></a>4.2

Le pilote JDBC 4.2 Microsoft pour SQL Server est parfaitement conforme aux spécifications JDBC 4.1. et 4.2. Les fichiers JAR dans le package 4.2 sont nommés en fonction de leur conformité avec la version de l’API JDBC. Par exemple, le fichier sqljdbc42.jar du package 4.2 est compatible avec l’API JDBC 4.2. De même, le fichier sqljdbc41.jar est conforme à l’API JDBC 4.1.

Pour être certain d’avoir le bon fichier sqljdbc42.jar ou sqljdbc41.jar, exécutez les lignes de code suivantes. Si la sortie est « Version du pilote : 4.2.6420.100 », c’est que vous disposez du package du pilote JDBC 4.2.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>Prise en charge de JDK 8

Le pilote prend en charge JDK 8.0 en plus de JDK 7.0, 6.0 et 5.0.

### <a name="jdbc-41-and-42-compliance"></a>Compatible avec JDBC 4.1 et 4.2

Le pilote prend en charge les spécifications de l’API Java Database Connectivity 4.1 et 4.2, en plus de la version 4.0. Pour plus d’informations, consultez [compatibilité avec JDBC 4.1 pour le pilote JDBC](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) et [Compatibilité avec JDBC 4.2 pour le pilote JDBC](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).

### <a name="bulk-copy"></a>Copie en bloc

Vous utilisez la fonctionnalité de copie en bloc pour copier rapidement de grandes quantités de données dans des tables ou des vues de bases de données SQL Server. Pour plus d’informations, consultez [Utilisation de la copie en bloc avec le pilote JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

### <a name="xa-transaction-rollback-option"></a>Option de restauration des transactions XA

Le pilote dispose de nouvelles options de délai d’attente pour la restauration automatique existante de transactions non préparées. Pour plus d’informations, consultez [Présentation des transactions XA](../../connect/jdbc/understanding-xa-transactions.md).

### <a name="new-kerberos-principal-connection-property"></a>Nouvelle propriété de connexion principale Kerberos

Le pilote utilise une nouvelle propriété de connexion pour faciliter la flexibilité avec les connexions Kerberos. Pour plus d’informations, consultez [Utilisation de l’authentification intégrée Kerberos pour se connecter à SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).

## <a name="41"></a>4.1

### <a name="support-for-jdk-7"></a>Prise en charge de JDK 7

Le pilote prend en charge JDK 7.0 en plus de JDK 6.0 et 5.0.

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Itanium non pris en charge pour les applications JDBC Driver 6.4, 6.0, 4.2 et 4.1

L’exécution d’applications Microsoft JDBC Driver 6.4, 6.0, 4.2 et 4.1 pour SQL Server n’est pas prise en charge sur un ordinateur Itanium.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)
