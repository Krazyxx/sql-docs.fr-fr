---
title: Terminologie Visual FoxPro | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], glossary
- FoxPro ODBC driver [ODBC], glossary
ms.assetid: a379b3cb-0393-46e7-b03b-724a56d8f31c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8aeb7db6f844b5182165146905f6cc9de928726
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63287381"
---
# <a name="visual-foxpro-terminology"></a>Terminologie Visual FoxPro
**database**  
 Dans Visual FoxPro, un fichier de base de données possède une extension de .dbc et peut contenir un ou plusieurs **tables**.  
  
 **table de base de données**  
 Dans Visual FoxPro, une table qui est associé à une base de données. Contraste **table gratuit**.  
  
 **table gratuit**  
 Dans Visual FoxPro, une table qui n’est pas associée à une base de données.  
  
 Un fichier .dbf créé dans FoxPro version 2.x est une table gratuite, sauf si elle est convertie en une table Visual FoxPro et ajouté à une base de données Visual FoxPro. Contraste **table de base de données**.  
  
 **instruction SQL préliminaire**  
 Une instruction SQL qui n’a pas déjà été traitée par le **SQLPrepare** (fonction). Pour plus d’informations sur cette fonction avec le pilote ODBC Visual FoxPro, consultez [SQLPrepare (pilote de ODBC Visual FoxPro)](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md).  
  
 **table**  
 Dans Visual FoxPro, les enregistrements sont stockés dans une table. Chaque ligne d’une table représente un enregistrement, et les colonnes de la table représentent les champs de l’enregistrement. Chaque table Visual FoxPro est stockée dans son propre fichier portant une extension .dbf. Tables Visual FoxPro peuvent être associés à une base de données.  
  
 FoxPro version 2. *x* tables ne sont pas associés à une base de données.
