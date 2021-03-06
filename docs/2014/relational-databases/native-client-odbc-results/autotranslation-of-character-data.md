---
title: Traduction automatique de données de type caractère | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5182ab1a72caac4181e50df2199f3e0457d3aaac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200214"
---
# <a name="autotranslation-of-character-data"></a>Traduction automatique de données caractères
  Les données de caractères, tels que ANSI caractères variables déclarées avec SQL_C_CHAR ou les données stockées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de la **char**, **varchar**, ou **texte** pouvez des types de données, représentent uniquement un nombre limité de caractères. Les données caractères stockées à l'aide d'un octet par caractère ne peuvent représenter que 256 caractères. Les valeurs stockées dans les variables SQL_C_CHAR sont interprétées à l'aide de la page de codes ANSI (ACP) de l'ordinateur client. Les valeurs stockées à l’aide de **char**, **varchar**, ou **texte** des types de données sur le serveur sont évaluées à l’aide de la page de codes ANSI du serveur.  
  
 Si le serveur et le client ont la même page de codes ANSI, ils peuvent sans peine interpréter les valeurs stockées dans SQL_C_CHAR, **char**, **varchar**, ou **texte** objets. Si le serveur et le client ont des pages de codes ANSI différentes, alors que les données SQL_C_CHAR du client peuvent être interprétées comme un caractère différent sur le serveur s’il est utilisé dans **char**, **varchar**, ou **texte** colonnes, variables ou paramètres. Par exemple, un octet de caractère contenant la valeur 0xA5 est interprété comme le caractère ?? sur un ordinateur à l’aide de code page 437 et est interprété comme l’yen signer ( ?) sur un ordinateur exécutant la page de codes 1252.  
  
 Les données Unicode sont stockées à l'aide de deux octets par caractère. Tous les caractères étendus étant couverts par la spécification Unicode, tous les caractères Unicode sont interprétés de la même façon par tous les ordinateurs.  
  
 La fonctionnalité AutoTranslate du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client tente de réduire les problèmes en déplaçant les données caractères entre un client et un serveur qui ont des pages de codes différentes. AutoTranslate peut être définie dans la chaîne de connexion de [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md), dans la chaîne de configuration de [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md), ou lors de la configuration des sources de données pour la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC Native Client pilote à l’aide de l’administrateur ODBC.  
  
 Lors de la fonctionnalité AutoTranslate est définie sur « non », sans conversions sont effectuées sur les données déplacées entre les variables SQL_C_CHAR sur le client et **char**, **varchar**, ou **texte** colonnes, variables, ou des paramètres dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données. Les modèles binaires peuvent être interprétés différemment sur les ordinateurs client et serveur si les données contiennent des caractères étendus et que les deux ordinateurs ont des pages de codes différentes. Les données seront interprétées de la même façon si les deux ordinateurs ont la même page de codes.  
  
 Lors de la fonctionnalité AutoTranslate est définie sur « Oui », le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client utilise Unicode pour convertir les données déplacées entre les variables SQL_C_CHAR sur le client et **char**, **varchar**, ou **texte** colonnes, variables ou paramètres dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données :  
  
-   Lorsque les données sont envoyées à partir d’une variable SQL_C_CHAR sur le client pour un **char**, **varchar**, ou **texte** colonne, variable ou un paramètre dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la base de données ODBC pilote convertit tout d’abord de SQL_C_CHAR en Unicode à l’aide de la page de codes ANSI du client, puis d’Unicode au caractère à l’aide de la page de codes ANSI du serveur.  
  
-   Lorsque les données sont envoyées à partir d’un **char**, **varchar**, ou **texte** colonne, variable ou un paramètre dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données à une variable SQL_C_CHAR sur le client, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Pilote ODBC Native Client convertit d’abord à partir de caractères Unicode à l’aide de la page de codes ANSI du serveur, puis d’Unicode en SQL_C_CHAR à l’aide de la page de codes ANSI du client.  
  
 Étant donné que toutes ces conversions sont effectuées par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’exécution de pilote ODBC Native Client sur le client, la page de codes ANSI du serveur doit être une des pages de codes installées sur l’ordinateur client.  
  
 Le fait d'effectuer les conversions de caractères via Unicode garantit une conversion correcte de tous les caractères qui existent dans les deux pages de codes. Si, toutefois, un caractère existe dans une page de codes mais pas dans une autre, le caractère ne peut pas être représenté dans la page de codes cible. Par exemple, la page de codes 1252 a le symbole de marque déposée ( ?), contrairement à la page de codes 437.  
  
 Le paramètre AutoTranslate n'a aucun effet sur ces conversions :  
  
-   Déplacement de données entre les variables caractères clientes SQL_C_CHAR et Unicode **nchar**, **nvarchar**, ou **ntext** colonnes, variables ou paramètres [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données.  
  
-   Déplacement de données entre les variables Unicode clientes SQL_C_WCHAR et caractère **char**, **varchar**, ou **texte** colonnes, variables ou paramètres [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données.  
  
 Les données doivent toujours être converties lorsqu'elles sont déplacées du type caractère vers le type Unicode.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des résultats &#40;ODBC&#41;](processing-results-odbc.md)   
 [Prise en charge d'Unicode et du classement](../collations/collation-and-unicode-support.md)  
  
  
