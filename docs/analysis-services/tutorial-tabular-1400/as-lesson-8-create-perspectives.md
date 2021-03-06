---
title: 'Analysis Services tutorial leçon 8 : créer des perspectives | Microsoft Docs'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 29a49478d75d7af5670f3e693cd87a5238c4ae11
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57684936"
---
# <a name="create-perspectives"></a>Créer des perspectives

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon, vous créez une perspective Internet Sales. Une perspective définit un sous-ensemble visualisable d'un modèle et des points de vue du modèle focalisés sur un domaine d'activité ou sur une application. Lorsqu’un utilisateur se connecte à un modèle à l’aide d’un point de vue, ils voient uniquement les objets de modèle (tables, colonnes, les mesures, hiérarchies et KPI) en tant que champs définis dans cette perspective. Pour plus d’informations, consultez [Perspectives](../tabular-models/perspectives-ssas-tabular.md).
  
La perspective Internet Sales que vous créez dans cette leçon exclut l’objet de la table DimCustomer. Lorsque vous créez une perspective qui exclut certains objets de vue, cet objet existe toujours dans le modèle. Toutefois, il n’est pas visible dans une liste de champs de client création de rapports. Les colonnes calculées et les mesures incluses ou non dans une perspective peuvent toujours être calculées à partir de données d'objet exclues.  
  
L'objectif de cette leçon est plutôt de décrire comment créer des points de vue et de vous familiariser avec les outils de création de modèles tabulaires. Si vous décidez plus tard ce modèle pour inclure des tables supplémentaires, vous pouvez créer des perspectives supplémentaires pour définir les différents points de vue du modèle, par exemple, les ventes et les stocks.  
  
Durée estimée pour effectuer cette leçon : **Cinq minutes**  
  
## <a name="prerequisites"></a>Prérequis  

Cet article fait partie d’un didacticiel de modélisation tabulaire, qui doit être effectué dans l’ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 7 : Créer des indicateurs de Performance clés](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Créer des perspectives  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Pour créer une perspective Internet Sales  
  
1.  Cliquez sur le **modèle** menu > **Perspectives** > **créer et gérer**.  
  
2.  Dans la boîte de dialogue **Perspectives** , cliquez sur **Nouvelle perspective**.  
  
3.  Double-cliquez sur le **nouvelle Perspective** en-tête de colonne et puis renommerez **Internet Sales**.  
  
4.  Sélectionnez toutes les tables *sauf* **DimCustomer**.  
  
    ![as-lesson8-perspectives](../tutorial-tabular-1400/media/as-lesson8-perspectives.png)
  
    Dans une leçon ultérieure, vous utilisez la fonctionnalité analyser dans Excel pour tester cette perspective. La liste de champs de tableau croisé dynamique Excel inclut chaque table à l’exception de la table DimCustomer.  

## <a name="whats-next"></a>Quelle est l’étape suivante ?

[Leçon 9 : Créer des hiérarchies](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md).
  
  
  
  
