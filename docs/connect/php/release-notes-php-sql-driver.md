---
title: Notes de publication des pilotes Microsoft pour PHP pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: v-dapugl, kenvh
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 48c4497dfa8974fe5fd59747d4b7023002d3f762
ms.sourcegitcommit: c60784d1099875a865fd37af2fb9b0414a8c9550
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58646416"
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Notes de publication de Microsoft Drivers for PHP for SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette page explique ce qui a été ajouté dans chaque version de la [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

<!--
Hello, We are standardizing the format of content inside our Release Notes (or What's New) articles.
Instead of bullets (or paragraphs), we have shifted to the 2-column format you see for H2 **What's New in Version 5.6**.
It is not necessary to reformat all the older H2 sections in this Release Notes file, but.....

Going forward, please be sure to use the 2-column format.

Also, all Release Notes .md file names now must begin with 'release-notes-*.md'.  And no filler words.
The 5.6 edition of this file is being renamed.....
FROM:  'release-notes-for-the-php-sql-driver.md'
TO  :  'release-notes-php-sql-driver.md'

For any questions, ask GeneMi or CraigG.
Thanks a lot.  2019-03-28  (DevO= 1467988)
-->

## <a name="whats-new-in-version-56"></a>Nouveautés de la version 5.6

| Nouvel élément | Détails |
| :------- | :------ |
| Prise en charge de PHP 7.3. | &nbsp; |
| Supprimé de la prise en charge de PHP 7.0. | &nbsp; |
| Prise en charge de Microsoft ODBC Driver 17.3 sur toutes les plateformes. | &nbsp; |
| Prise en charge de macOS Mojave. | Nécessite le pilote ODBC 17.3 ou version ultérieure. |
| Prise en charge pour Ubuntu 18.10 et Suse Linux 15. | Les deux nécessitent 17.3 du pilote ODBC ou version ultérieure. |
| Supprimer la prise en charge de Linux Ubuntu 17.10 et macOS El Capitan. | &nbsp; |
| Prise en charge pour le jeton d’accès Azure AD. | Dans Linux et macOS, nécessite le pilote ODBC 17.2 + et unixODBC 2.3.6+. |
| Prise en charge pour l’authentification auprès d’Azure AD à l’aide de MSI pour les ressources Azure. | Nécessite un pilote ODBC 17.3 +. |
| Nouvelles fonctionnalités d’extraction | &bull; &nbsp; Nouvel indicateur PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE pour pdo_sqlsrv retourner la date/heure en tant qu’objets.<br/><br/>&bull; &nbsp; Ajouter l’option de ReturnDatesAsStrings au niveau instruction pour sqlsrv.<br/><br/>&bull; &nbsp; Nouvelles options de niveaux de connexion et instruction pour les deux pilotes pour mettre en forme de valeurs décimales dans les résultats d’extraction. |
| Prise en charge pour une compilation statique des pilotes si les utilisateurs choisir de générer à partir de la source. | &nbsp; |
| Amélioration des performances par la mise en cache des métadonnées sur les extractions et accélérer les conversions de chaînes Unicode. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="whats-new-in-version-53"></a>Nouveautés de la version 5.3

- Prise en charge pour Microsoft ODBC Driver 17.2 sur toutes les plateformes
- Prise en charge de macOS High Sierra (nécessite la version 17 du pilote ODBC et versions ultérieures)
- Prise en charge pour Azure Key Vault Always Encrypted pour base fonctionnalités CRUD telles que la fonctionnalité Always Encrypted est disponible pour tous les prises en charge les plateformes Windows, Linux ou macOS [à l’aide du chiffrement intégral avec les pilotes PHP pour SQL Server](../../connect/php/using-always-encrypted-php-drivers.md)
- Prise en charge d’Ubuntu LTS de 18.04 (nécessite 17.2 du pilote ODBC)
- Prise en charge de la résilience des connexions dans Linux ou macOS ainsi (nécessite 17.2 du pilote ODBC)

## <a name="whats-new-in-version-52"></a>Nouveautés de la version 5.2

- Prise en charge de PHP 7.2.1 et jusqu'à sur Windows et 7.2.0 et sur d’autres plateformes
- Prise en charge pour Microsoft ODBC Driver 17
  - Version 17 est désormais la valeur par défaut sur toutes les plateformes
- Prise en charge Ubuntu 17.10, Debian 9 et Suse Enterprise Linux 12
- Prise en charge supprimée pour Ubuntu 15.10
- Prise en charge Always Encrypted avec les fonctionnalités CRUD sur Windows. Pour plus d’informations, consultez [à l’aide du chiffrement intégral avec les pilotes PHP pour SQL Server](../../connect/php/using-always-encrypted-php-drivers.md)
  - Prise en charge de Store de certificat Windows
  - Always Encrypted n’est possible que le pilote Microsoft ODBC 17 et versions ultérieures
- Prise en charge pour les paramètres régionaux non UTF8 sur Linux et macOS
  - Paramètres régionaux non-UTF-8 sur Linux et macOS sont uniquement pris en charge avec le pilote Microsoft ODBC 17 et versions ultérieures
- Prise en charge d’Azure SQL Data Warehouse
- Prise en charge pour Azure SQL Managed Instance (préversion privée étendue)

## <a name="whats-new-in-version-43"></a>Nouveautés de la version 4.3

- Prise en charge de PHP 7.1
- Prise en charge de macOS Sierra et macOS El Capitan
- Prise en charge pour Ubuntu 15.10 et Debian 8
- Prise en charge supprimée pour Ubuntu 15.04
- Prise en charge des groupes de disponibilité Always On via la résolution d’adresses IP réseau Transparent. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).
- Prise en charge pour le type de données sql_variant avec limitation.
- Prise en charge de la résilience des connexions inactive dans Windows. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).
- Regroupement de prise en charge de Linux et macOS de la connexion. Pour plus d’informations, consultez [Regroupement de connexions](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).
- Prise en charge pour l’authentification Azure Active Directory avec ActiveDirectoryPassword et SqlPassword. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).

## <a name="whats-new-in-version-40"></a>Nouveautés de la version 4.0

- Prise en charge de PHP 7.0  
- Prise en charge 64 bits
- Prise en charge pour Ubuntu 15.04, Ubuntu 16.04 et RedHat 7

## <a name="whats-new-in-version-32"></a>Nouveautés de la version 3.2

- Prise en charge de PHP 5.6   
- Inclut les dernières mises à jour pour les versions antérieures PHP 5.5 et 5.4   
- Nécessite Microsoft ODBC Driver 11 for SQL Server  

## <a name="whats-new-in-version-31"></a>Nouveautés de la version 3.1

- Prise en charge de PHP 5.5  
- Nécessite Microsoft ODBC Driver 11 for SQL Server. Les versions précédentes nécessitaient SQL Native Client.  

## <a name="whats-new-in-version-30"></a>Nouveautés de la version 3.0  

- Prise en charge de PHP 5.4.  PHP 5.2 n’est pas pris en charge dans la version 3 du [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
- Ajout de l’option de connexion AttachDBFileName. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).  
- Prise en charge de la Base de données locale, qui a été ajoutée dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Pour plus d’informations, consultez [prise en charge de la base de données locale](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).
- Ajout de l’option de connexion AttachDBFileName. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).  
- Prise en charge des fonctionnalités de récupération d’urgence/haute disponibilité. Pour plus d’informations, consultez [prise en charge pour la haute disponibilité, récupération d’urgence](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).
- Prise en charge des curseurs côté client (mise en cache d’un jeu de résultats en mémoire). Pour plus d’informations, consultez [Types de curseur &#40;pilote SQLSRV&#41;](../../connect/php/cursor-types-sqlsrv-driver.md) et [Types de curseur &#40;pilote PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- Ajout de l’attribut PDO::ATTR_EMULATE_PREPARES. Pour plus d’informations, consultez [PDO::prepare](../../connect/php/pdo-prepare.md).  

## <a name="whats-new-in-version-20"></a>Nouveautés de la version 2.0

Dans la version 2.0, la prise en charge du pilote PDO_SQLSRV a été ajoutée. Pour plus d’informations, consultez [Référence de pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md).  

## <a name="see-also"></a> Voir aussi

[Vue d’ensemble de Microsoft Drivers for PHP for SQL Server](../../connect/php/overview-of-the-php-sql-driver.md)
