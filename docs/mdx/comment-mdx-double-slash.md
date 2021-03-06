---
title: (Comment) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6570694bc38eb6f32f660006f1ed1b6797793b7b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63306340"
---
# <a name="comment-mdx-double-slash"></a>Barre oblique double de commentaire MDX


  Indique un texte défini par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>Paramètres  
 *Comment_Text*  
 Chaîne contenant le texte du commentaire.  
  
## <a name="remarks"></a>Notes  
 Il est possible d'insérer des commentaires sur une ligne distincte, à la fin d'une ligne de script MDX (Multidimensional Expressions), ou à l'intérieur d'une instruction MDX. Le serveur n'évalue pas ces commentaires.  
  
 Utilisez // pour un commentaire d'une seule ligne uniquement. Les commentaires insérés à l'aide de // sont délimités par le caractère de fin de paragraphe.  
  
 Il n'y a pas de longueur maximale pour les commentaires.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
// This member returns the gross profit margin for product types  
// and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM // Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaire &#40;MDX&#41;](../mdx/comment-mdx.md)   
 [-- &#40;Comment&#41; &#40;MDX&#41;](../mdx/comment-mdx-operator-reference.md)   
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
