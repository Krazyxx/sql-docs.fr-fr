---
title: Prise en charge de Type de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9a3d63f0bf1923905c5281655aff2af294b8284
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241324"
---
# <a name="data-type-support"></a>Prise en charge du type de données
Pilotes ODBC doivent prendre en charge au moins une des SQL_CHAR et SQL_VARCHAR. Prise en charge pour les autres types de données est déterminée par le niveau de conformité de la source du pilote ou de données SQL-92. Une application doit appeler **SQLGetTypeInfo** pour déterminer les types de données pris en charge par le pilote.  
  
 Pour plus d’informations sur les types de données, consultez [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).
