---
title: Communication avec SQL Server (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5bf07f4e83cb58966b384a4bf0f523b7a1dd3881
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63032884"
---
# <a name="communicating-with-sql-server-odbc"></a>Communication avec SQL Server (ODBC)
  Pour une application ODBC communiquer avec une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], elle doit allouer d’environnement et de connexion gère et se connecter à la source de données. Après avoir établi une connexion, l'application peut envoyer des requêtes au serveur et traiter tous les jeux de résultats. Lorsque l'application a terminé d'utiliser la source de données, elle se déconnecte de la source de données et libère le handle de connexion. Lorsque l'application a libéré tous ses handles de connexion, elle libère le handle d'environnement.  
  
 Une application peut se connecter à un nombre quelconque de sources de données. L'application peut utiliser une combinaison de pilotes et de sources de données, le même pilote et une combinaison de sources de données, voire le même pilote et plusieurs connexions à la même source de données.  
  
 Vous pouvez télécharger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC Native Client exemples à partir de la [téléchargements SQL Server](https://go.microsoft.com/fwlink/?LinkId=62796) page sur MSDN.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Allocation d’un descripteur d’environnement](allocating-an-environment-handle.md)  
  
-   [Allocation d’un descripteur de connexion](allocating-a-connection-handle.md)  
  
-   [Sources de données ODBC SQL Server Native Client](../../integration-services/connection-manager/data-sources.md)  
  
-   [Connexion à une Source de données &#40;ODBC&#41;](connecting-to-a-data-source-odbc.md)  
  
-   [Déconnexion d’une source de données](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)  
  
  
