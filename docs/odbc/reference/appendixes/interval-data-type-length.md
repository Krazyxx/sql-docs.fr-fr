---
title: Longueur du Type de données d’intervalle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16d0590d3297b52891bf399822ce984674022583
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188916"
---
# <a name="interval-data-type-length"></a>Longueur des types de données d’intervalle
Les règles suivantes sont utilisées pour déterminer la longueur d’un type de données d’intervalle en caractères. Durée est exprimée en nombre de caractères. Le nombre d’octets varie selon le jeu de caractères. La longueur inclut les valeurs suivantes ajoutés ensemble :  
  
-   Deux caractères pour chaque champ dans l’intervalle qui n’est pas le champ Début.  
  
-   Dans le champ Début, le nombre de caractères qui est la précision de début expresse ou implicite. Si la précision de début n’est pas spécifiée, la valeur par défaut est 2.  
  
-   Pour le séparateur entre les champs d’un caractère.  
  
-   Un plus la précision en expresse ou implicite. Si la précision en secondes n’est pas spécifiée, la valeur par défaut est 6.  
  
 Valeurs de longueur de colonne spécifique pour chaque type de données d’intervalle sont contenues dans [taille de la colonne](../../../odbc/reference/appendixes/column-size.md).
