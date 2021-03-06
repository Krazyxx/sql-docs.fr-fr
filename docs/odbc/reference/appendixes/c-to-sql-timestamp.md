---
title: 'C en SQL : Timestamp | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], timestamp
- timestamp data type [ODBC]
- converting data from c to SQL types [ODBC], timestamp
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a738712a8fb1b032ef8244f579b10fdcc22becee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241432"
---
# <a name="c-to-sql-timestamp"></a>C en SQL : Horodateur
L’identificateur pour le type de données ODBC C timestamp est :  
  
 SQL_C_TYPE_TIMESTAMP  
  
 Le tableau suivant présente les types de données à laquelle les données timestamp C peuvent être converties à ODBC SQL. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de C en Types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificateur de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longueur d’octet de colonne > = longueur d’octet de caractère<br /><br /> 19 < = longueur d’octet de colonne < longueur d’octet de caractère<br /><br /> Colonne de longueur d’octet < 19<br /><br /> Valeur de données n’est pas une date valide|n/a<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longueur de colonne caractère > = longueur de caractères de données<br /><br /> 19 < = longueur de colonne caractère < longueur des données de caractères<br /><br /> Colonne de longueur < 19 caractères<br /><br /> Valeur de données n’est pas une date valide|n/a<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Champs d’heure sont égales à zéro<br /><br /> Champs d’heure sont différentes de zéro<br /><br /> Valeur de données ne contient pas une date valide|n/a<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|Champs de fractions de seconde sont égales à zéro [a]<br /><br /> Fractional seconds fields are nonzero[a]<br /><br /> Valeur de données ne contient-elle pas une heure valide|n/a<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Champs de fractions de secondes ne sont pas tronqués.<br /><br /> Champs de fractions de seconde sont tronquées<br /><br /> Valeur de données n’est pas une date valide|n/a<br /><br /> 22008<br /><br /> 22007|  
  
 [a] la date, les champs de la structure d’horodatage sont ignorés.  
  
 Pour plus d’informations sur les valeurs qui sont valides dans une structure SQL_C_TIMESTAMP, consultez [les Types de données C](../../../odbc/reference/appendixes/c-data-types.md), plus haut dans cette annexe.  
  
 Lorsque les données timestamp C sont converties en données de caractères SQL, les données de caractères résultant sont dans la «*aaaa*-*mm*-*jj* *hh*:*mm*:*ss*[.*f...*] « format.  
  
 Le pilote ignore la valeur de longueur/indicateur lors de la conversion des données à partir du type de données timestamp C et suppose que la taille du tampon de données est la taille du type de données timestamp C. La valeur de longueur / d’indicateur est passée dans le *StrLen_or_Ind* argument dans **SQLPutData** et dans la mémoire tampon spécifiée avec la *StrLen_or_IndPtr* argument dans **SQLBindParameter**. Le tampon de données est spécifié avec la *DataPtr* argument dans **SQLPutData** et *ParameterValuePtr* argument dans **SQLBindParameter**.
