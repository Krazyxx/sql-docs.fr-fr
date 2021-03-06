---
title: Fonction SQL-92 CAST | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db5077b9df2673593b6eaec9622aafd1d2c77234
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270631"
---
# <a name="sql-92-cast-function"></a>CAST (SQL-92), fonction
Le **CAST** fonction définie dans SQL-92 est équivalente à la **convertir** fonction définie dans ODBC. La syntaxe des fonctions équivalentes est comme suit :  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 Le SQL-92 **CAST** fonction impose que les types de données peuvent être convertis pour les autres types de données. (Pour plus d’informations, consultez la spécification de SQL-92.) Le **CAST** fonction est prise en charge au niveau de la transition FIPS.  
  
 Une application peut déterminer la prise en charge pour le **CAST** fonctionnent comme suit :  
  
1.  Appelez **SQLGetInfo** avec le type d’information SQL_SQL_CONFORMANCE. Si la valeur de retour pour le type d’informations est SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE ou SQL_SC_SQL92_FULL, le **CAST** fonction est prise en charge.  
  
2.  Si la valeur de retour du type d’informations SQL_SQL_CONFORMANCE est SQL_SC_ENTRY_LEVEL ou 0, appelez **SQLGetInfo** avec le type d’information SQL_SQL92_VALUE_EXPRESSIONS. Si le bit SQL_SVE_CAST est défini, le **CAST** fonction est prise en charge.
