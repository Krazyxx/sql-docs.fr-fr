---
title: SQLFreeStmt | Microsoft Docs
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 32b1f1185dad9b173c12f3acb232c2426d5db411
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63014452"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  En règle générale   
      **SQLFreeStmt** n'est pas recommandé dans ODBC 3.0 et les versions ultérieures. Toutefois si l’application doit réutiliser l’instruction vous devez toujours utiliser **SQLFreeStmt** avec la **SQL_RESET_PARAMS** et **SQL_UNBIND** options). Vous pouvez également utiliser [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md), et [ SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) à remplacent ou dupliquent la fonction de **SQLFreeStmt** doit utiliser à la place.  
  
 En règle générale, il est plus efficace de réutiliser des instructions que to déposez-les et allouer de nouveaux. Toutefois dans certaines situations, telles que la réutilisation des instructions, SQLFreeStmt toujours doit être utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLFreeStmt, fonction](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
