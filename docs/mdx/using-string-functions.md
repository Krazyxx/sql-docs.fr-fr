---
title: À l’aide des fonctions de chaîne | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6e151d06d086569b16fcdf1dc3570f9b220dfcd6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928155"
---
# <a name="using-string-functions"></a>Utilisation des fonctions de chaîne


  Vous pouvez utiliser des fonctions de chaîne sur tous les objets ou presque de la syntaxe MDX (Multidimensional Expressions). Dans les procédures stockées, les fonctions de chaîne sont principalement utilisées pour convertir l'objet en représentation sous forme de chaîne. Les fonctions de chaîne permettent également d'évaluer une expression de chaîne sur un objet afin de retourner une valeur.  
  
 Les fonctions de chaîne plus largement utilisées sont **nom** et **Uniquename**. Ces fonctions retournent respectivement le nom et le nom unique d'un objet. Essentiellement, elles sont utilisées lors du débogage des calculs pour découvrir quel membre une fonction retourne.  
  
## <a name="examples"></a>Exemples  
 L'exemple des requêtes suivant montre comment utiliser ces fonctions :  
  
 `WITH`  
  
 `//Returns the name of the current Product on rows`  
  
 `MEMBER [Measures].[ProductName] AS [Product].[Product].CurrentMember.Name`  
  
 `//Returns the uniquename of the current Product on rows`  
  
 `MEMBER [Measures].[ProductUniqueName] AS [Product].[Product].CurrentMember.Uniquename`  
  
 `//Returns the name of the Product dimension`  
  
 `MEMBER [Measures].[ProductDimensionName] AS [Product].Name`  
  
 `SELECT  {[Measures].[ProductName],[Measures].[ProductUniqueName],[Measures].[ProductDimensionName]}`  
  
 `ON COLUMNS,`  
  
 `[Product].[Product].MEMBERS  ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Le **générer** fonction peut être utilisée pour exécuter une fonction de chaîne sur chaque membre d’un jeu et concaténer les résultats. Elle est parfois aussi utile lors du débogage des calculs car elle vous permet de visualiser le contenu d'un jeu. L'exemple suivant montre comment l'utiliser comme suit :  
  
 `WITH`  
  
 `//Returns the names of the current Product and its ancestors up to the All Member`  
  
 `MEMBER [Measures].[AncestorNames] AS`  
  
 `GENERATE(`  
  
 `ASCENDANTS([Product].[Product Categories].CurrentMember)`  
  
 `, [Product].[Product Categories].CurrentMember.Name, ", ")`  
  
 `SELECT`  
  
 `{[Measures].[AncestorNames]}`  
  
 `ON COLUMNS,`  
  
 `[Product].[Product Categories].MEMBERS  ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Un autre groupe de fonctions de chaîne largement utilisées est celles qui vous permettent de convertir une chaîne qui contient le nom unique d'un objet ou une expression qui est résolue en l'objet dans l'objet lui-même. L’exemple de requête suivant montre comment la **StrToMember** et **StrToSet** fonctions cela :  
  
 `SELECT`  
  
 `{StrToMember("[Measures].[Inter" + "net Sales Amount]")}`  
  
 `ON COLUMNS,`  
  
 `StrToSet("{`  
  
 `[Product].[Product Categories].[Category].&[3],`  
  
 `[Product].[Product Categories].[Product].&[477],`  
  
 `[Product].[Product Categories].[Product].&[788],`  
  
 `[Product].[Product Categories].[Product].&[708],`  
  
 `[Product].[Product Categories].[Product].&[711]`  
  
 `}")`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
> [!NOTE]  
>  Le **StrToMember** et **StrToSet** fonctions doivent être utilisées avec précaution. Elles peuvent entraîner des performances médiocres de requête si elles sont utilisées dans des définitions de calcul.  
  
## <a name="see-also"></a>Voir aussi  
 [Generate &#40;MDX&#41;](../mdx/generate-mdx.md)   
 [Name &#40;MDX&#41;](../mdx/name-mdx.md)   
 [UniqueName &#40;MDX&#41;](../mdx/uniquename-mdx.md)   
 [Fonctions &#40;syntaxe MDX&#41;](../mdx/functions-mdx-syntax.md)   
 [À l’aide de procédures stockées &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)   
 [StrToMember &#40;MDX&#41;](../mdx/strtomember-mdx.md)   
 [StrToSet &#40;MDX&#41;](../mdx/strtoset-mdx.md)  
  
  
