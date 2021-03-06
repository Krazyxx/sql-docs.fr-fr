---
title: Utilisation de l’extraction pour extraire les données sources (MDX) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 81c873d0ea6e5c21d97fc719ce1c72a773df43e5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62802841"
---
# <a name="mdx-data-manipulation---retrieve-source-data-using-drillthrough"></a>Manipulation de données MDX - Récupérer des données sources à l’aide de DRILLTHROUGH
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  L’instruction MDX (Multidimensional Expressions) utilise l’instruction [DRILLTHROUGH](../../../mdx/mdx-data-manipulation-drillthrough.md)pour récupérer un ensemble de lignes à partir des données sources d’une cellule d’un cube.  
  
 Pour exécuter une instruction **DRILLTHROUGH** sur un cube, une action d’extraction doit être définie pour ce dernier. Pour définir une action d’extraction, dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], dans le Concepteur de cube, dans la barre d’outils du volet **Actions** , cliquez sur **Nouvelle action d’extraction**. Dans la nouvelle action d’extraction, spécifiez le nom de l’action, la cible, la condition et les colonnes retournées par une instruction **DRILLTHROUGH** .  
  
## <a name="drillthrough-statement-syntax"></a>Syntaxe de l'instruction DRILLTHROUGH  
 L’instruction **DRILLTHROUGH** utilise la syntaxe suivante :  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 La clause **SELECT** identifie la cellule du cube qui contient les données sources à récupérer. Cette clause **SELECT** est identique à une instruction **SELECT** MDX ordinaire, à la différence qu’un seul membre peut être spécifié sur chaque axe dans la clause **SELECT** . Si plusieurs membres sont spécifiés sur un axe, une erreur se produit.  
  
 La syntaxe `<Max_Rows>` spécifie le nombre maximum de lignes de chaque ensemble de lignes retourné. Si le fournisseur OLE DB utilisé pour la connexion à la source de données ne prend pas en charge **DBPROP_MAXROWS**, le paramètre `<Max_Rows>` est ignoré.  
  
 La syntaxe `<First_Rowset>` identifie la partition d’où l’ensemble de lignes est d’abord retourné.  
  
 La syntaxe `<Return_Columns>` identifie les colonnes de la base de données sous-jacente à retourner.  
  
## <a name="drillthrough-statement-example"></a>Exemple d'instruction DRILLTHROUGH  
 L’exemple suivant illustre l’utilisation de l’instruction **DRILLTHROUGH** . Dans cet exemple, l'instruction DRILLTHROUGH interroge les feuilles des dimensions Store, Product et Time le long de la dimension Stores (axe de découpage), puis retourne le groupe de mesures du service, l'ID de service et le prénom de l'employé.  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manipulation de données &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-manipulating-data.md)  
  
  
