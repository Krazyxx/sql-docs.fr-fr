---
title: Modifier le mappage de Type (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7f9d9530-6c04-41d9-bbe7-d91820a30066
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2bbe1636db483ad24f7744fe4d9902c520e07dbb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63138864"
---
# <a name="edit-type-mapping-accesstosql"></a>Modifier le mappage de Type (AccessToSQL)
Le **modifier le mappage de Type** boîte de dialogue vous permet de spécifier comment les types sont mappés entre les objets de base de données source et de destination.  
  
Vous pouvez accéder à cette boîte de dialogue à plusieurs endroits :  
  
-   Lorsque vous sélectionnez une base de données source ou un objet de base de données, le **le mappage de Type** onglet s’affiche à droite de l’Explorateur de métadonnées. Cliquez sur **ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
-   Sur le **outils** menu, sélectionnez **paramètres du projet** ou **par défaut des paramètres de projet**. Dans la boîte de dialogue, sélectionnez **le mappage de Type**. Cliquez sur **ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
Mappages de types de table spécifiques de remplacent la base de données et les mappages de type de projet. Mappages spécifiques à la base de données remplacent les mappages de projet.  
  
## <a name="options"></a>Options  
**Type de source**  
Sélectionnez le type de données source à mapper à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.  
  
Si le type de données est de longueur variable, les champs suivants seront affiche sous **type de Source**:  
  
**From**  
Spécifiez la longueur minimale pour ce mappage. Par exemple, pour le **texte** type de données, vous pouvez entrer 10 pour spécifier que ce mappage est pour une plage commençant à **text(10)**.  
  
**Pour**  
Spécifiez la longueur maximale pour ce mappage. Par exemple, pour le **texte** type de données, vous pouvez entrer 20 pour spécifier que ce mappage s’applique à une plage et se termine au **text(20)**.  
  
**Type de cible**  
Sélectionnez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données à laquelle le type de données source est mappé. Lorsque SSMA crée la table ou la procédure stockée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le type de source de données changera à ce type de données.  
  
Si le type de données est de longueur variable, le champ suivant apparaît sous **type cible**:  
  
**Replace with**  
Spécifier la longueur de la cible pour ce mappage. Par exemple, pour le **nvarchar** type de données, vous pouvez entrer 20 pour spécifier que le type de données source spécifiée doit être mappé à **nvarchar (20)**.  
  
