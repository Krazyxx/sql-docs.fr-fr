---
title: Filtrer les données avant l’exportation (Complément MDS pour Excel) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 003cf7c4871b89067316d2331f658f95a179e37b
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488084"
---
# <a name="filter-data-before-exporting-mds-add-in-for-excel"></a>Filtrer les données avant l’exportation (Complément MDS pour Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous pouvez filtrer les données quand vous souhaitez limiter leur taille ou leur étendue pour les exporter vers Excel.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
### <a name="to-filter-data-before-exporting"></a>Pour filtrer les données avant l’exportation  
  
1.  Ouvrez Excel et accédez à l'onglet **Données de référence** , puis connectez-vous à un référentiel MDS. Pour plus d’informations, consultez [Se connecter à un référentiel MDS &#40;complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Dans le volet **Explorateur de données de référence** , sélectionnez un modèle et une version. La liste des entités est remplie.  
  
    -   Si le volet **Explorateur de données de référence** n'est pas visible, dans le groupe **Se connecter et charger** , cliquez sur **Afficher l'Explorateur**.  
  
    -   Si le volet **Explorateur de données de référence** est désactivé, cela signifie que la feuille de calcul existante contient déjà des données managées MDS. Pour activer le volet, ouvrez une nouvelle feuille de calcul.  
  
3.  Dans le volet **Explorateur de données de référence** , dans la liste des entités, cliquez sur l'entité à filtrer.  
  
4.  Sur le ruban, dans le groupe **Se connecter et charger** , cliquez sur **Filtre**.  
  
5.  Remplissez la boîte de dialogue **Filtrer** en sélectionnant les attributs (colonnes) à afficher, en définissant l'ordre des colonnes, et si nécessaire, en filtrant les données afin de retourner moins de lignes. Affichez le volet **Résumé** pour connaître le volume des données qui seront retournées. Pour plus d’informations, consultez [Boîte de dialogue Filtrer &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Cliquez sur **Charger les données**. La feuille est renseignée avec les données managées MDS.  
  
    > [!NOTE]  
    >  -   Seul le premier million de membres est chargé dans Excel.  
    > -   Dans les colonnes qui représentent des listes contraintes (attributs basés sur un domaine), seules les 25 000 premières valeurs sont chargées par défaut.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Publier des données d’Excel dans Master Data Services &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble : Exportation des données vers Excel &#40;complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Boîte de dialogue Filtrer &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Réorganiser des colonnes &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  
