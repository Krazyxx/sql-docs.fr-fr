---
title: Enregistrements d’état | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 986cd3c48104bfe822934eb415b854b8e976f242
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149118"
---
# <a name="status-records"></a>Enregistrements d’état
Les champs dans les enregistrements d’état contiennent des informations sur les erreurs spécifiques ou des avertissements retournés par la Gestionnaire de pilotes, pilotes ou source de données, y compris le SQLSTATE, une numéro d’erreur natif, un message de diagnostic, un numéro de colonne et un numéro de ligne. Enregistrements d’état peuvent être créés uniquement si la fonction retourne SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA ou SQL_STILL_EXECUTING. Pour obtenir une liste complète des champs dans les enregistrements d’état, consultez le [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) description de fonction.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Séquence d’enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [Codes SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Messages de diagnostic](../../../odbc/reference/develop-app/diagnostic-messages.md)
