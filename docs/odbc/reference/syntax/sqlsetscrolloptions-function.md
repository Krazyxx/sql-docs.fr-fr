---
title: Sqlsetscrolloptions, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbdd2038bc217a7ca2a2efe08940c03c5da5d8f0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62985236"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions, fonction
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : Déprécié  
  
 **Résumé**  
 Dans ODBC 3 *.x*, la fonction ODBC 2.0 **SQLSetScrollOptions** a été remplacé par des appels à **SQLGetInfo** et **SQLSetStmtAttr**.  
  
> [!NOTE]
>  Pour plus d’informations sur ce que le Gestionnaire de pilotes mappe cette fonction lorsqu’un ODBC 2 *.x* application fonctionne avec un ODBC 3 *.x* pilote, consultez [mappage de fonctions déconseillées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)dans l’annexe g : Instructions de pilote pour la compatibilité descendante.  
> 
> [!NOTE]
>  Lorsque le Gestionnaire de pilotes mappe **SQLSetScrollOptions** pour une application qui fonctionne avec un ODBC 3 *.x* pilote qui ne prend pas en charge **SQLSetScrollOptions**, le pilote Le gestionnaire définit l’option d’instruction SQL_ROWSET_SIZE, pas l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE, à la *la RowsetSize* argument dans **SQLSetScrollOption**. Par conséquent, **SQLSetScrollOptions** ne peut pas être utilisé par une application lors de l’extraction de plusieurs lignes par un appel à **SQLFetch** ou **SQLFetchScroll**. Il peut être uniquement utilisé lorsque l’extraction de plusieurs lignes par un appel à **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Notes  
 Si votre application s’exécutera sur un système d’exploitation 64 bits, consultez [informations sur ODBC 64 bits](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
