---
title: POWER (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3d25801b7cc7f6282ebc8cf7b1ce7839159312dc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62897409"
---
# <a name="power-ssis-expression"></a>POWER (expression SSIS)
  Renvoie le résultat de l'élévation d'une expression numérique à une puissance donnée. La valeur du paramètre de la puissance doit s'évaluer à un entier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique valide.  
  
 *puissance*  
 Expression numérique valide.  
  
## <a name="result-types"></a>Types de résultats  
 DT_R8  
  
## <a name="remarks"></a>Notes  
 Les arguments *numeric_expression* et *power* sont convertis dans le type de données DT_R8 avant le calcul de la puissance. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
 Si l’argument *numeric_expression* correspond à la valeur zéro et que l’argument *power* est négatif, l’évaluateur d’expression retourne une erreur et le résultat obtenu est Null.  
  
 Si *numeric_expression* ou *power* correspond à des résultats indéterminés, la valeur Null est retournée.  
  
 L’argument *power* peut être une fraction. Par exemple, vous pouvez utiliser la valeur 0,5 comme puissance.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant utilise un littéral numérique. La fonction élève 4 à la puissance 3 et renvoie 64.  
  
```  
POWER(4,3)  
```  
  
 L’exemple suivant utilise la colonne **Length** et la variable **DimensionCount** . Si l’argument **Length** a la valeur 8 et l’argument **DimensionCount** la valeur 2, le résultat obtenu est 64.  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
