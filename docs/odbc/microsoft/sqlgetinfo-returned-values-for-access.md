---
title: Valeurs de retournées par SQLGetInfo pour Access | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Access driver
- SQLGetInfo function [ODBC], Access Driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
- Access driver [ODBC], SQLGetInfo
ms.assetid: c551e07f-30c4-41a2-8991-6010a3511d76
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a79e97721f246d47f8fab413be8074836f753cbe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63135307"
---
# <a name="sqlgetinfo-returned-values-for-access"></a>Valeurs retournées par SQLGetInfo pour Access
Le tableau suivant répertorie le langage C# defines pour le *fInfoType* argument et les valeurs correspondantes retournées par **SQLGetInfo**. Ces informations peuvent être extraites en passant le répertoriés en langage C# defines à **SQLGetInfo** dans le *fInfoType* argument. Pour plus d’informations sur les valeurs retournées par **SQLGetInfo**, consultez le *de référence du programmeur ODBC*.  
  
> [!NOTE]  
>  Où **SQLGetInfo** retourne un masque de bits 32 bits, une barre verticale (&#124;) représente une opération OR au niveau du bit.  
  
|InfoType|Valeur retournée|  
|--------------|--------------------|  
|SQL_ACCESSIBLE_PROCEDURES|"Y"|  
|SQL_ACCESSIBLE_TABLES|"Y"|  
|SQL_ACTIVE_ENVIRONMENTS|0|  
|SQL_AGGREGATE_FUNCTIONS|Ensemble de tous les|  
|SQL_ALTER_DOMAIN|0|  
|SQL_ALTER_TABLE|0|  
|SQL_ASYNC_MODE|0|  
|SQL_BATCH_ROW_COUNT|0|  
|SQL_BATCH_SUPPORT|0|  
|SQL_BOOKMARK_PERSISTENCE|Valeurs multiples|  
|SQL_CATALOG_LOCATION|SQL_QL_START|  
|SQL_CATALOG_NAME|"Y"|  
|SQL_CATALOG_NAME_SEPARATOR|"."|  
|SQL_CATALOG_TERM|« Database »|  
|SQL_CATALOG_USAGE|Valeurs multiples|  
|SQL_COLLATION_SEQ|""|  
|SQL_COLUMN_ALIAS|"Y"|  
|SQL_CONCAT_NULL_BEHAVIOR|SQL_CB_NON_NULL|  
|SQL_CONVERT_BIGINT|0|  
|SQL_CONVERT_BINARY|Valeurs multiples|  
|SQL_CONVERT_BIT|0|  
|SQL_CONVERT_CHAR|Valeurs multiples|  
|SQL_CONVERT_DATE|Valeurs multiples|  
|SQL_CONVERT_DECIMAL|0|  
|SQL_CONVERT_DOUBLE|Valeurs multiples|  
|SQL_CONVERT_FLOAT|Valeurs multiples|  
|SQL_CONVERT_FUNCTIONS|SQL_FN_CVT_CONVERT|  
|SQL_CONVERT_INTEGER|Valeurs multiples|  
|SQL_CONVERT_LONGVARBINARY|Valeurs multiples|  
|SQL_CONVERT_LONGVARCHAR|Valeurs multiples|  
|SQL_CONVERT_NUMERIC|Valeurs multiples|  
|SQL_CONVERT_REAL|Valeurs multiples|  
|SQL_CONVERT_SMALLINT|Valeurs multiples|  
|SQL_CONVERT_TIME|Valeurs multiples|  
|SQL_CONVERT_TIMESTAMP|Valeurs multiples|  
|SQL_CONVERT_TINYINT|Valeurs multiples|  
|SQL_CONVERT_VARBINARY|Valeurs multiples|  
|SQL_CONVERT_VARCHAR|Valeurs multiples|  
|SQL_CORRELATION_NAME|SQL_CN_ANY|  
|SQL_CREATE_ASSERTION|0|  
|SQL_CREATE_CHARACTER_SET|0|  
|SQL_CREATE_COLLATION|0|  
|SQL_CREATE_DOMAIN|0|  
|SQL_CREATE_SCHEMA|0|  
|SQL_CREATE_TABLE|SQL_CT_CREATE_TABLE|  
|SQL_CREATE_TRANSLATION|0|  
|SQL_CREATE_VIEW|SQL_CV_CREATE_VIEW|  
|SQL_CURSOR_COMMIT_BEHAVIOR|SQL_CB_CLOSE|  
|SQL_CURSOR_ROLLBACK_BEHAVIOR|SQL_CB_CLOSE|  
|SQL_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_DATA_SOURCE_NAME|La source de données à partir du fichier Odbc.ini, ou « » si le mot clé DRIVER est utilisé dans le fichier Odbc.ini|  
|SQL_DATA_SOURCE_READ_ONLY|"N"|  
|SQL_DATABASE_NAME|Nom de fichier|  
|SQL_DATETIME_LITERALS|0|  
|SQL_DBMS_NAME|« ACCÈS »|  
|SQL_DBMS_VER|Valeurs multiples|  
|SQL_DDL_INDEX|Valeurs multiples|  
|SQL_DEFAULT_TXN_ISOLATION|SQL_TXN_READ_COMMITTED|  
|SQL_DESCRIBE_PARAMETER|0|  
|SQL_DRIVER_HDBC|Gérée par le Gestionnaire de pilotes.|  
|SQL_DRIVER_HENV|Gérée par le Gestionnaire de pilotes.|  
|SQL_DRIVER_HLIB|Gérée par le Gestionnaire de pilotes.|  
|SQL_DRIVER_HSTMT|Gérée par le Gestionnaire de pilotes.|  
|SQL_DRIVER_NAME|"OdbcJt32.dll"|  
|SQL_DRIVER_ODBC_VER|"3.51.0000"|  
|SQL_DRIVER_VER|« 4.00.*nnnn*» (*nnnn* spécifie la date de génération)|  
|SQL_DROP_ASSERTION|0|  
|SQL_DROP_CHARACTER_SET|0|  
|SQL_DROP_COLLATION|0|  
|SQL_DROP_DOMAIN|0|  
|SQL_DROP_SCHEMA|0|  
|SQL_DROP_TABLE|SQL_DT_DROP_TABLE|  
|SQL_DROP_TRANSLATION|0|  
|SQL_DROP_VIEW|SQL_DV_DROP_VIEW|  
|SQL_EXPRESSIONS_IN_ORDERBY|"Y"|  
|SQL_FILE_USAGE|SQL_FILE_CATALOG|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT|  
|SQL_GETDATA_EXTENSIONS|Valeurs multiples|  
|SQL_GROUP_BY|SQL_GB_GROUP_BY_CONTAINS_SELECT|  
|SQL_IDENTIFIER_CASE|SQL_IC_MIXED|  
|SQL_IDENTIFIER_QUOTE_CHAR|« ' » (guillemet arrière)|  
|SQL_KEYWORDS|Valeurs multiples|  
|SQL_LIKE_ESCAPE_CLAUSE|"N"|  
|SQL_MAX_BINARY_LITERAL_LEN|255|  
|SQL_MAX_CATALOG_NAME_LEN|66|  
|SQL_MAX_CHAR_LITERAL_LEN|255|  
|SQL_MAX_COLUMN_NAME_LEN|64|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|10|  
|SQL_MAX_COLUMNS_IN_INDEX|32|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|10|  
|SQL_MAX_COLUMNS_IN_SELECT|255|  
|SQL_MAX_COLUMNS_IN_TABLE|255|  
|SQL_MAX_CONCURRENT_ACTIVITIES|0|  
|SQL_MAX_CURSOR_NAME_LEN|64|  
|SQL_MAX_DRIVER_CONNECTIONS|64|  
|SQL_MAX_INDEX_SIZE|255|  
|SQL_MAX_PROCEDURE_NAME_LEN|64|  
|SQL_MAX_ROW_SIZE|2096|  
|SQL_MAX_ROW_SIZE_INCLUDES_LONG|"N"|  
|SQL_MAX_SCHEMA_NAME_LEN|0|  
|SQL_MAX_STATEMENT_LEN|65000|  
|SQL_MAX_TABLE_NAME_LEN|64|  
|SQL_MAX_TABLES_IN_SELECT|16|  
|SQL_MAX_USER_NAME_LEN|0|  
|SQL_MULT_RESULT_SETS|"N"|  
|SQL_MULTIPLE_ACTIVE_TXN|"Y"|  
|SQL_NEED_LONG_DATA_LEN|"N"|  
|SQL_NON_NULLABLE_COLUMNS|SQL_NNC_NON_NULL|  
|SQL_NULL_COLLATION|SQL_NC_LOW|  
|SQL_NUMERIC_FUNCTIONS|Valeurs multiples|  
|SQL_ODBC_SAG_CLI_ CONFORMANCE|SQL_OSCC_COMPLIANT|  
|SQL_ODBC_SQL_INTEGRITY|"N"|  
|SQL_ODBC_VER|À partir du Gestionnaire de pilotes|  
|SQL_OJ_CAPABILITIES|Valeurs multiples|  
|SQL_ORDER_BY_COLUMNS_IN_SELECT|"N"|  
|SQL_OUTER_JOINS|"Y"|  
|SQL_PROCEDURE_TERM|« REQUÊTE »|  
|SQL_PROCEDURES|"Y"|  
|SQL_QUOTED_IDENTIFIER_CASE|SQL_IC_MIXED|  
|SQL_ROW_UPDATES|"N"|  
|SQL_SCHEMA_TERM|""|  
|SQL_SCHEMA_USAGE|0|  
|SQL_SCROLL_OPTIONS|Valeurs multiples|  
|SQL_SEARCH_PATTERN_ESCAPE|"\\"|  
|SQL_SERVER_NAME|« ACCÈS »|  
|SQL_SPECIAL_CHARACTERS|"~`@#$%^&*_-+=\\}{"';:?/><,.!'[]&#124;"|  
|SQL_STRING_FUNCTIONS|Valeurs multiples|  
|SQL_SUBQUERIES|Valeurs multiples|  
|SQL_SYSTEM_FUNCTIONS|0|  
|SQL_TABLE_TERM|« TABLE »|  
|SQL_TIMEDATE_ADD_INTERVALS|0|  
|SQL_TIMEDATE_DIFF_INTERVALS|0|  
|SQL_TIMEDATE_FUNCTIONS|Valeurs multiples|  
|SQL_TXN_CAPABLE|SQL_TC_ALL|  
|SQL_TXN_ISOLATION_OPTION|SQL_TXN_READ_COMMITTED|  
|SQL_UNION|Valeurs multiples|  
|SQL_USER_NAME|« ADMIN »|
