---
title: Value (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6eb91bb43407311a58e495b5f9391186821d3a67
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63251424"
---
# <a name="value-mdx"></a>Value (MDX)


  Retourne la valeur du membre actuel de la dimension de mesures située à l'intersection du membre actuel des hiérarchies d'attribut dans le contexte de la requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression[.Value]   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Le **valeur** fonction retourne la valeur du membre spécifié sous forme de chaîne. Le **valeur** argument est facultatif, car la valeur d’un membre est la propriété par défaut d’un membre et est la valeur retournée pour un membre si aucune autre valeur n’est spécifiée. Pour plus d’informations sur les propriétés des membres, consultez [propriétés de membre intrinsèques &#40;MDX&#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md) et [propriétés de membre définies par l’utilisateur &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne la valeur d'un membre ainsi que le nom du membre de manière explicite.  
  
```  
WITH MEMBER [Date].[Calendar].NumericValue as [Date].[Calendar].[July 1, 2001].Value  
MEMBER [Date].[Calendar].MemberName AS [Date].[Calendar].[July 1, 2001].Name  
  
SELECT {[Date].[Calendar].NumericValue, [Date].[Calendar].MemberName} ON 0  
from [Adventure Works]  
```  
  
 L'exemple ci-dessous retourne la valeur d'un membre en tant que valeur par défaut retournée pour un membre sur un axe.  
  
```  
SELECT {[Date].[Calendar].[July 1, 2001]} ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [MemberValue &#40;MDX&#41;](../mdx/membervalue-mdx.md)   
 [Properties &#40;MDX&#41;](../mdx/properties-mdx.md)   
 [Name &#40;MDX&#41;](../mdx/name-mdx.md)   
 [UniqueName &#40;MDX&#41;](../mdx/uniquename-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
