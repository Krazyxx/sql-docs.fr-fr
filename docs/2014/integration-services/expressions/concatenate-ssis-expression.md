---
title: + (Concaténer) (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- concatenation [Integration Services]
- + (concatenate operator)
- concatenate operator (+)
ms.assetid: 0fed6334-7a4f-42dc-a611-191fcaa0e443
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 288e4aedc6112640aa511712ad90912b1d41b2fa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62769367"
---
# <a name="-concatenate-ssis-expression"></a>+ (Concaténer) (expression SSIS)
  Concatène deux expressions en une seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
character_expression1 + character_expression2  
  
```  
  
## <a name="arguments"></a>Arguments  
 *expression1, expression2*  
 Toute expression valide de type de données DT_STR, DT_WSTR, DT_TEXT, DT_NTEXT ou DT_IMAGE.  
  
## <a name="result-types"></a>Types de résultats  
 DT_WSTR  
  
## <a name="remarks"></a>Notes  
 L'expression peut utiliser l'un des types de données DT_STR et DT_WSTR (ou les deux).  
  
 La concaténation des types de données DT_STR et DT_WSTR renvoie un résultat de type DT_WSTR. La longueur de la chaîne est la somme des longueurs des chaînes d'origine exprimée en caractères.  
  
 Seules les données des types de données chaîne DT_STR et DT_WSTR ou de types de données BLOB (Binary Large Object Block) DT_TEXT, DT_NTEXT et DT_IMAGE peuvent être concaténées. Les autres types de données doivent être explicitement convertis dans l'un de ces types de données pour que la concaténation puisse être effectuée. Pour plus d’informations sur les conversions valides entre les types de données, consultez [Cast &#40;expression SSIS&#41;](cast-ssis-expression.md).  
  
 Les deux expressions doivent être du même type de données, ou l'une des expressions doit être implicitement convertible vers le type de données de l'autre expression. Par exemple, si la chaîne « La date de commande est » et la colonne **OrderDate** sont concaténées, les valeurs de la colonne **OrderDate** sont implicitement converties vers un type de données string. Deux valeurs numériques ne peuvent être concaténées que si elles sont toutes deux explicitement converties en un type de données chaîne.  
  
 Une concaténation ne peut utiliser qu’un seul type de données d’objet BLOB : DT_TEXT, DT_NTEXT ou DT_IMAGE.  
  
 Si l'un des éléments est NULL, le résultat est NULL.  
  
 Les littéraux de chaîne doivent être placés entre guillemets.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant concatène les valeurs des colonnes **FirstName** et **LastName** en les séparant par un espace.  
  
```  
FirstName + ' ' + LastName  
```  
  
 L’exemple suivant concatène les variables **ZIPCode** et **ZIPCode+4**. Les deux variables sont de type de données chaîne. La variable**ZIPCode+4** doit figurer entre crochets car elle contient le caractère « + ».  
  
```  
@ZIPCcode + "-" + @[ZipCode+4]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Priorités et associativité des opérateurs](operator-precedence-and-associativity.md)   
 [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md)  
  
  
