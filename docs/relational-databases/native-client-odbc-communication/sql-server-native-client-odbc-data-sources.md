---
title: Sources de données SQL Server Native Client ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 318ff6f9abf54e4c8e15e623bde7d5007a747eef
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013861"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>Sources de données ODBC SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Un nom de source de données (DSN) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identifie une source de données ODBC qui contient toutes les informations nécessaires à une application ODBC pour se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un serveur spécifique. Il existe deux moyens de définir un nom de source de données ODBC :  
  
-   Sur un ordinateur client, ouvrez Outils d’administration dans le panneau de configuration, double-cliquez sur **Sources de données (ODBC)**. L'Administrateur de sources de données ODBC qui vous permet de créer un DSN s'ouvre.  
  
-   Dans une application ODBC, appelez [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md).  
  
 Une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient les éléments suivants :  
  
-   Nom de la source de données.  
  
-   Toutes les informations nécessaires pour se connecter à une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Base de données par défaut à utiliser dans une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (facultatif).  
  
-   Paramètres tels que les options ANSI à utiliser, le besoin ou non d'enregistrer des statistiques de performance, et ainsi de suite (facultatif).  
  
 Aucune application ODBC n'est requise pour se connecter via une source de données. En revanche, l'application doit fournir les mêmes informations de connectivité à une fonction de connexion ODBC que celles que trouverait le pilote dans un DSN.  
  
## <a name="see-also"></a>Voir aussi  
 [Communication avec SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
