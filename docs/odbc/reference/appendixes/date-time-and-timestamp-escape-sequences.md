---
title: Date, Time et Timestamp de séquences d’échappement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC]
- escape sequences [ODBC], about escape sequences
- ODBC escape sequences [ODBC], about escape sequences
- ODBC escape sequences [ODBC]
ms.assetid: 67b7dee0-e5b1-4469-a626-0c7767852b80
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6bd73a1bd7a9f41b20300e4abf47688a6c78794
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241016"
---
# <a name="date-time-and-timestamp-escape-sequences"></a>Date, heure et horodatage, séquences d’échappement
ODBC définit des séquences d’échappement pour les littéraux de date, heure et timestamp. La syntaxe de ces séquences d’échappement est comme suit :  
  
```  
  
{d 'value'}  
{t 'value'}  
{ts 'value'}  
```  
  
 Dans la notation BNF, la syntaxe est la suivante :  
  
```  
  
      ODBC-date-time-escape ::=  
     ODBC-date-escape  
     | ODBC-time-escape  
     | ODBC-timestamp-escapeODBC-date-escape ::=  
     ODBC-esc-initiator d 'date-value' ODBC-esc-terminatorODBC-time-escape ::=  
     ODBC-esc-initiator t 'time-value' ODBC-esc-terminatorODBC-timestamp-escape ::=  
     ODBC-esc-initiator ts 'timestamp-value' ODBC-esc-terminatorODBC-esc-initiator ::= {  
ODBC-esc-terminator ::= }  
date-value ::=   
     years-value date-separator months-value date-separator days-valuetime-value ::=   
     hours-value time-separator minutes-value time-separatorseconds-valuetimestamp-value ::= date-value timestamp-separator time-valuedate-separator ::= -  
time-separator ::= :  
timestamp-separator ::=  
     (The blank character)years-value ::= digit digit digit digitmonths-value ::= digit digitdays-value ::= digit digithours-value ::= digit digitminutes-value ::= digit digitseconds-value ::= digit digit[.digit...]  
```  
  
## <a name="remarks"></a>Notes  
 Les séquences d’échappement des littéraux de date, time et timestamp sont pris en charge si les types de données date, time et timestamp sont pris en charge par la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer si ces types de données sont pris en charge.
