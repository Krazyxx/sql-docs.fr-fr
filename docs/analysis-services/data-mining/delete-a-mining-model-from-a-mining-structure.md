---
title: Supprimer un modèle d’exploration de données à partir d’une Structure d’exploration de données | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b17489213e0f057d8f291095f01b65f97a977ff1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468843"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>supprimer un modèle d'exploration de données d'une structure d'exploration de données
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Vous pouvez supprimer les modèles d’exploration de données en utilisant le Concepteur d’exploration de données, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ou des instructions DMX.  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>Supprimer un modèle d'exploration de données à l'aide de des outils de données SQL Server  
  
1.  Sélectionnez l’onglet **Modèles d’exploration de données** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur le modèle à supprimer, puis sélectionnez **Supprimer**.  
  
     La boîte de dialogue **Supprimer les objets** s’ouvre.  
  
3.  Cliquez sur **OK**.  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>Supprimer un modèle d'exploration de données à l'aide de SQL Server Management Studio  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient le modèle.  
  
2.  Développez **Structures d’exploration de données**, puis développez **Modèles d’exploration de données**.  
  
3.  Cliquez avec le bouton droit sur le modèle à supprimer, puis sélectionnez **Supprimer**.  
  
     La suppression du modèle ne supprime pas les données d'apprentissage, seuls les métadonnées et les schémas créés lorsque vous avez formé le modèle sont supprimés.  
  
### <a name="delete-a-mining-model-using-dmx"></a>Supprimer un modèle d'exploration de données à l'aide de DMX  
  
-   [DROP MINING MODEL &#40;DMX&#41;](../../dmx/drop-mining-model-dmx.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures des modèles d’exploration de données](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
