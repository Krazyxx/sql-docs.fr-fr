---
title: Type de données DateTime change | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- time data type [ODBC]
- datetime data types [ODBC]
- date data type [ODBC]
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- compatibility [ODBC], datetime data types
ms.assetid: c38c79f9-8bb0-4633-ac86-542366c09a95
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5a87a1cbfbdff5eb428e73d74cdd1199955d673
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267698"
---
# <a name="datetime-data-type-changes"></a>Changements dans le type de données datetime
Dans ODBC 3. *x*, les identificateurs de date, heure et types de données timestamp SQL ont été modifiés à partir de SQL_DATE, SQL_TIME et SQL_TIMESTAMP (avec des instances de **#define** dans le fichier d’en-tête de 9, 10 et 11) à SQL_TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP (avec des instances de **#define** dans le fichier d’en-tête de 91, 92 et 93), respectivement. Les identificateurs de type C correspondants ont remplacé par SQL_C_DATE, SQL_C_TIME et SQL_C_TIMESTAMP SQL_C_TYPE_DATE, SQL_C_TYPE_TIME et SQL_C_TYPE_TIMESTAMP, respectivement.  
  
 La taille de colonne et les chiffres décimaux retournés pour les types de données datetime SQL dans ODBC 3. *x* sont le même que la précision et l’échelle retourné pour eux dans ODBC 2. *x*. Ces valeurs sont différentes de celles figurant dans les champs de descripteur SQL_DESC_PRECISION et SQL_DESC_SCALE. (Pour plus d’informations, consultez [taille de colonne, des chiffres décimaux, transférer la longueur en octets et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).)  
  
 Ces modifications affectent **SQLDescribeCol**, **SQLDescribeParam**, et **SQLColAttribute**; **SQLBindCol**, **SQLBindParameter**, et **SQLGetData**; et **SQLColumns**, **SQLGetTypeInfo** , **SQLProcedureColumns**, **SQLStatistics**, et **SQLSpecialColumns**.  
  
 Le tableau suivant montre comment le ODBC 3 *.x* Gestionnaire de pilotes effectue le mappage des date, time et timestamp C types de données entré dans le *TargetType* arguments de **SQLBindCol**et **SQLGetData** ou dans le *ValueType* argument de **SQLBindParameter**.  
  
|Type de données<br /><br /> code entré|2.*x* application<br /><br /> 2.*x* pilote|2.*x* application<br /><br /> 3.*x* pilote|3.*x* application<br /><br /> 2.*x* pilote|3.*x* application<br /><br /> 3.*x* pilote|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|Aucun mappage|SQL_C_TYPE_DATE (91)|Aucun mappage [1]|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|Erreur (DM)|Erreur (DM)|SQL_C_DATE (9)|Aucun mappage [2]|  
|SQL_C_TIME (10)|Aucun mappage|SQL_C_TYPE_TIME (92)|Aucun mappage [1]|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|Erreur (DM)|Erreur (DM)|SQL_C_TIME (10)|Aucun mappage [2]|  
|SQL_C_TIMESTAMP (11)|Aucun mappage|SQL_C_TYPE_TIMESTAMP (93)|Aucun mappage [1]|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|Erreur (DM)|Erreur (DM)|SQL_C_TIMESTAMP (11)|Aucun mappage [2]|  
  
 [1] en raison de cela, un ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote peut utiliser les codes de date, heure ou timestamp renvoyés dans les jeux de résultats retournés par les fonctions de catalogue.  
  
 [2] en raison de cela, un ODBC 3. *x* application fonctionne avec un ODBC 3. *x* pilote peut utiliser les codes de date, heure ou timestamp renvoyés dans les jeux de résultats retournés par les fonctions de catalogue.  
  
 Le tableau suivant montre comment le ODBC 3 *.x* Gestionnaire de pilotes effectue un mappage des types de données SQL date, time et timestamp entré dans le *ParameterType* argument de **SQLBindParameter**  ou dans le *DataType* argument de **SQLGetTypeInfo**.  
  
|Type de données<br /><br /> code entré|2.*x* application<br /><br /> 2.*x* pilote|2.*x* application<br /><br /> 3.*x* pilote|3.*x* application<br /><br /> 2.*x* pilote|3.*x* application<br /><br /> 3.*x* pilote|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|Aucun mappage|SQL_TYPE_DATE (91)|Aucun mappage [1]|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|Erreur (DM)|Erreur (DM)|SQL_DATE (9)|Aucun mappage [2]|  
|SQL_TIME (10)|Aucun mappage|SQL_TYPE_TIME (92)|Aucun mappage [1]|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|Erreur (DM)|Erreur (DM)|SQL_TIME (10)|Aucun mappage [2]|  
|SQL_TIMESTAMP (11)|Aucun mappage|SQL_TYPE_TIMESTAMP (93)|Aucun mappage [1]|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|Erreur (DM)|Erreur (DM)|SQL_TIMESTAMP (11)|Aucun mappage [2]|  
  
 [1] en raison de cela, un ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote peut utiliser les codes de date, heure ou timestamp renvoyés dans les jeux de résultats retournés par les fonctions de catalogue.  
  
 [2] en raison de cela, un ODBC 3. *x* application fonctionne avec un ODBC 3. *x* pilote peut utiliser les codes de date, heure ou timestamp renvoyés dans les jeux de résultats retournés par les fonctions de catalogue.
