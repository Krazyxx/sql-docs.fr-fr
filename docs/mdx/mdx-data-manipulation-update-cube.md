---
title: Instruction UPDATE CUBE (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 878f103e236a198ff71181a64b39400c8f6ea0ca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187623"
---
# <a name="mdx-data-manipulation---update-cube"></a>Manipulation de données MDX - UPDATE CUBE


  L'instruction UPDATE CUBE est utilisée pour l'écriture différée des données dans une cellule d'un cube qui agrège uniquement dans son parent à l'aide de l'agrégation SUM. Pour plus d’explications et un exemple, consultez « Fonctionnement des Allocations » dans ce billet de blog : [Création d’une Application de l’écriture différée avec Analysis Services (blog)](https://go.microsoft.com/fwlink/?LinkId=394977).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UPDATE [ CUBE ] Cube_Name   
   SET   
            <update clause>   
           [, <update clause> ...n ]  
  
<update clause> ::=   
      Tuple_Expression[.VALUE]= New_Value  
      [   
        USE_EQUAL_ALLOCATION   
        | USE_EQUAL_INCREMENT   
        | USE_WEIGHTED_ALLOCATION [ BY Weight_Expression]   
        | USE_WEIGHTED_INCREMENT [ BY Weight_Expression]  
      ]  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Une chaîne valide qui précise le nom d’un cube.  
  
 *Tuple_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un tuple.  
  
 *New_Value*  
 Une expression numérique valide.  
  
 *Weight_Expression*  
 Expression numérique MDX (Multidimensional Expressions) valide qui retourne une valeur décimale comprise entre 0 et 1.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez mettre à jour la valeur d'une cellule feuille ou non-feuille d'un cube, et allouer inévitablement la valeur d'une cellule non-feuille spécifiée à toutes les cellules feuilles dépendantes. La cellule spécifiée par l'expression de tuple peut être n'importe quelle cellule valide dans l'espace multidimensionnel (ce qui signifie que la cellule ne dispose d'aucune cellule feuille). Toutefois, la cellule doit être agrégée avec la [somme](../mdx/sum-mdx.md) fonction d’agrégation et ne doivent comporter un membre calculé dans le tuple qui est utilisé pour identifier la cellule.  
  
 Il peut être utile de considérer le **UPDATE CUBE** instruction comme une sous-routine qui générera automatiquement une série d’opérations d’écriture différée de cellule aux cellules feuille et non-feuille qui seront cumuleront dans une somme spécifiée.  
  
 Voici une description des méthodes d’allocation.  
  
 **USE_EQUAL_ALLOCATION :** Chaque cellule feuille qui contribue à la cellule mise à jour sera affecté une valeur égale basée sur l’expression suivante.  
  
```  
<leaf cell value> =   
<New Value> / Count(leaf cells that are contained in <tuple>)  
```  
  
 **USE_EQUAL_INCREMENT :** chaque cellule feuille qui contribue à la cellule mise à jour passera en fonction de l’expression suivante.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value > - <existing value>) /  
Count(leaf cells contained in <tuple>)  
```  
  
 **USE_WEIGHTED_ALLOCATION :** Chaque cellule feuille qui contribue à la cellule mise à jour sera attribué une valeur égale basée sur l’expression suivante.  
  
```  
<leaf cell value> = < New Value> * Weight_Expression  
```  
  
 **USE_WEIGHTED_INCREMENT :** Chaque cellule feuille qui contribue à la cellule mise à jour sera modifié en fonction de l’expression suivante.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value> - <existing value>)  * Weight_Expression  
```  
  
 Si une expression de poids n’est pas spécifiée, le **UPDATE CUBE** instruction utilise implicitement l’expression suivante.  
  
```  
Weight_Expression = <leaf cell value> / <existing value>  
```  
  
 Une expression de poids doit être exprimée sous forme de valeur décimale comprise entre zéro (0) et 1. Cette valeur spécifie le ratio de la valeur allouée que vous voulez affecter aux cellules feuilles affectées par l'allocation. Il est de la responsabilité du programmeur de l'application cliente de créer des expressions dont les valeurs agrégées de cumul seront égales à la valeur allouée de l'expression.  
  
> [!CAUTION]  
>  L'application cliente doit considérer simultanément l'allocation de toutes les dimensions afin d'éviter l'éventualité de résultats imprévus, notamment des valeurs de cumul incorrectes ou des données incohérentes.  
  
 Chaque **UPDATE CUBE** allocation doit être envisagée comme atomique fins transactionnelles. Ceci signifie que si l'une des opérations d'allocation échoue pour quelque raison que ce soit, par exemple une erreur de formule ou une violation de sécurité, l'ensemble de l'opération UPDATE CUBE échouera. Avant le calcul des opérations individuelles d'allocation, un instantané des données est réalisé pour garantir la correction des calculs résultants.  
  
> [!CAUTION]  
>  Lorsqu'elle est utilisée sur une mesure contenant des entiers, la méthode USE_WEIGHTED_ALLOCATION peut retourner des résultats imprécis causés par des arrondis successifs.  
  
> [!IMPORTANT]  
>  Quand les cellules mises à jour ne se chevauchent pas, la propriété de chaîne de connexion **Update Isolation Level** peut être utilisée pour améliorer les performances pour UPDATE CUBE.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [Instructions de Manipulation de données MDX &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
