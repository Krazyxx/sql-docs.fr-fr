---
title: Commentaires (syntaxe MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 17693d0dc76dd6cb8b3a4d0c3ead9f95c0599580
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181563"
---
# <a name="comments-mdx-syntax"></a>Commentaires (syntaxe MDX)


  Les commentaires sont des chaînes de texte non exécutables figurant dans un code de programmation (les commentaires sont également appelés remarques). Vous pouvez utiliser des commentaires pour documenter du code ou désactiver temporairement des parties d'instructions et de scripts MDX (Multidimensional Expressions) en cours d'analyse. À l’aide de commentaires pour documenter du code, vous pouvez faciliter sa maintenance. Les commentaires servent souvent à enregistrer le nom du programme, le nom de l'auteur et les dates des principales mises à jour. Vous pouvez également utiliser des commentaires pour décrire des calculs compliqués ou expliquer une méthode de programmation.  
  
 Les commentaires de la syntaxe MDX respectent les principes suivants :  
  
-   Tous les caractères alphanumériques ou les symboles peuvent être utilisés dans un commentaire.  Tous les caractères dans un commentaire sont ignorés.  
  
-   La longueur d'un commentaire dans une instruction ou un script n'est pas limitée. Un commentaire peut être constitué d’une ou plusieurs lignes.  
  
 La syntaxe MDX prend en charge trois types de caractères de commentaire :  
  
 // (doubles barres obliques)  
 Ces caractères de commentaire peuvent être utilisés directement dans une ligne de code ou en début de ligne. Tout ce qui se trouve entre les doubles barres obliques et la fin de ligne fait partie du commentaire. Pour un commentaire de plusieurs lignes, les doubles barres obliques doivent apparaître au début de chaque ligne. Pour plus d’informations, consultez [ &#40;commentaire&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md).  
  
 -- (doubles tirets)  
 Ces caractères de commentaire peuvent être utilisés directement dans une ligne de code ou en début de ligne. Tout ce qui se trouve entre les doubles tirets et la fin de ligne fait partie du commentaire. Pour un commentaire de plusieurs lignes, les doubles tirets doivent apparaître au début de chaque ligne. Pour plus d’informations, consultez [-- &#40;commentaire&#41; &#40;MDX&#41;](../mdx/comment-mdx-operator-reference.md).  
  
 /* ... \*/ (barre oblique-astérisque paires de caractères)  
 Ces caractères de commentaire peuvent être utilisés directement dans une ligne de code devant être exécuté, en début de ligne ou même dans du code exécutable. Tout depuis le commentaire ouvrant (/\*) pour le commentaire fermant (\*/) est considéré comme étant le commentaire. Pour un commentaire de plusieurs lignes, la paire de caractères de commentaire (/\*) doit commencer le commentaire et la paire de caractères de commentaire de fermeture (\*/) doit se terminer le commentaire. Aucun autre caractère de commentaire ne peut apparaître dans les lignes de commentaire. Pour plus d’informations, consultez [/ *... \*/ (Commentaire)](../mdx/comment-mdx.md).  
  
## <a name="example"></a>Exemple  
 La requête suivante offre des exemples des trois types de commentaire :  
  
 `//An example of a comment using the double-forward slash`  
  
 `--An example of a comment using the double-hypen`  
  
 `/*An example of a`  
  
 `multi-line`  
  
 `comment*/`  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `ON Columns,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments de syntaxe MDX &#40;MDX&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
