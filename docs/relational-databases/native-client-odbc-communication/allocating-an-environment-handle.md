---
title: Allouer un Handle d’environnement | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4cee5d6711f18cc7ce21e162794858fbde7c893e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013901"
---
# <a name="allocating-an-environment-handle"></a>Allocation d'un handle d'environnement
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Avant qu'une application puisse appeler toute fonction ODBC, elle doit initialiser l'environnement ODBC et allouer un handle d'environnement. Il s'agit du handle de contexte global et de l'espace réservé pour les autres handles dans ODBC. Pour cela, vous devez appeler **SQLAllocHandle** avec la *HandleType* paramètre défini à SQL_HANDLE_ENV et *InputHandle* défini à SQL_NULL_HANDLE.  
  
 Après avoir alloué le handle d'environnement, l'application doit définir des attributs d'environnement afin d'indiquer la version des appels de fonction ODBC qu'elle utilisera. Pour utiliser le ODBC 3. *x* appeler des fonctions, [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) avec la *attribut* paramètre défini à SQL_ATTR_ODBC_VERSION et *ValuePtr* SQL_OV_ la valeur ODBC3.  
  
## <a name="see-also"></a>Voir aussi  
 [Communication avec SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
