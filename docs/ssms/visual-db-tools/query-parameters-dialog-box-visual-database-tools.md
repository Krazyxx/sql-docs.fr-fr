---
title: Paramètres de la requête, boîte de dialogue (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7b841a4874c8fefa735547cdd42ff0cb704c1ccc
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65098226"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>Paramètres de la requête, boîte de dialogue (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Cette boîte de dialogue permet d'entrer des valeurs pour les paramètres définis dans la requête. Elle apparaît lorsque vous exécutez une requête qui contient des paramètres qui exigent une entrée de l'utilisateur final au moment de l'exécution.  
  
## <a name="options"></a>Options  
**Name**  
Énumère les paramètres définis pour la requête en cours d'exécution. Si la requête contient des paramètres nommés, les noms apparaissent dans la liste. Si la requête contient des paramètres sans nom, les noms des paramètres définis par le système sont répertoriés pour chaque paramètre dans la requête.  
  
**Value**  
Entrez la valeur de chaque paramètre énuméré sous **Nom**. La dernière valeur utilisée apparaît comme valeur par défaut du paramètre.  
  
## <a name="example"></a> Exemple  
La requête suivante dans le volet SQL ouvre la boite de dialogue Paramètres de la requête lorsqu'elle est exécutée dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a> Voir aussi  
[Requête avec des paramètres &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
