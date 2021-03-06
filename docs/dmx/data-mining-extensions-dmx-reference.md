---
title: Data Mining Extensions (DMX) référence | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dcf3231fbff0ec4c3ea32e94f7b974a62faf05e6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38032725"
---
# <a name="data-mining-extensions-dmx-reference"></a>Guide de référence du langage DMX (Data Mining Extensions)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Extensions DMX (Data Mining) est un langage que vous pouvez utiliser pour créer et utiliser des modèles d’exploration de données dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Vous pouvez utiliser DMX pour créer la structure de nouveaux modèles d'exploration de données, pour l'apprentissage de ces modèles et pour les explorer, les gérer et y effectuer des prévisions. Le langage DMX se compose d'instructions DDL (langage de définition de données), d'instructions DML (langage de manipulation de données), de fonctions et d'opérateurs.  
  
## <a name="microsoft-ole-db-for-data-mining-specification"></a>Spécification Microsoft OLE DB pour l'exploration de données  
 Les fonctionnalités d’exploration de données dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sont conçues pour répondre à la [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB pour la spécification de l’exploration de données.  
  
 Le [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB pour la spécification d’exploration de données définit les éléments suivants :  
  
-   Une structure pour conserver les informations qui définissent un modèle d'exploration de données.  
  
-   Un langage pour créer et utiliser des modèles d'exploration de données.  
  
 La spécification définit la base de l'exploration de données comme étant l'objet virtuel de modèle d'exploration de données. L'objet de modèle d'exploration de données encapsule tout ce qui est connu concernant un modèle d'exploration de données particulier. L'objet de modèle d'exploration de données est structuré comme une table SQL, avec des colonnes, des types de données et des méta-informations qui décrivent le modèle. Cette structure vous permet d'employer le langage DMX, qui est une extension du langage SQL, pour créer des modèles et les utiliser.  
  
 **Pour plus d’informations :** [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
##  <a name="BKMK_DMXStatements"></a> Instructions DMX  
 Vous pouvez utiliser des instructions DMX pour créer, traiter, supprimer, copier, explorer et effectuer des prévisions dans des modèles d'exploration de données. Il existe deux types d'instructions DMX : les instructions de définition de données et les instructions de manipulation de données. Chaque type d'instruction permet d'effectuer différentes sortes de tâches.  
  
 Les sections suivantes fournissent des informations supplémentaires sur l'utilisation des instructions DMX :  
  
-   [Instructions de définition de données](#BKMK_DDL)  
  
-   [Instructions de Manipulation de données](#BKMK_DML)  
  
-   [Requêtes de base](#BKMK_Queries)  
  
###  <a name="BKMK_DDL"></a> Instructions de définition de données  
 Les instructions de définition de données dans DMX permettent de créer et de définir de nouvelles structures et modèles d'exploration de données, d'importer et d'exporter des modèles et des structures d'exploration de données et de supprimer des modèles existants d'une base de données. Les instructions de définition de données dans DMX font partie du langage de définition de données (DDL).  
  
 En utilisant les instructions de définition de données dans DMX, vous pouvez effectuer les tâches suivantes :  
  
-   Créer une structure d’exploration de données à l’aide de la [CREATE MINING STRUCTURE](../dmx/create-mining-structure-dmx.md) instruction et ajouter un modèle d’exploration de données à la structure d’exploration de données à l’aide de la [ALTER MINING STRUCTURE](../dmx/alter-mining-structure-dmx.md) instruction.  
  
-   Créer un modèle d’exploration d’et de la structure d’exploration de données associée simultanément à l’aide de la [CREATE MINING MODEL](../dmx/create-mining-model-dmx.md) instruction pour créer un objet de modèle d’exploration de données vide de données.  
  
-   Exporter un modèle d’exploration d’et de la structure d’exploration de données associé à un fichier à l’aide de la [exporter](../dmx/export-dmx.md) instruction. Importer un modèle d’exploration d’et de la structure d’exploration de données associé à partir d’un fichier qui est créé par l’instruction d’exportation à l’aide de la [importation](../dmx/import-dmx.md) instruction.  
  
-   Copier la structure d’un modèle d’exploration de données existant dans un nouveau modèle et effectuez son apprentissage avec les mêmes données, à l’aide de la [SELECT INTO](../dmx/select-into-dmx.md) instruction.  
  
-   Supprimer complètement un modèle d’exploration de données à partir d’une base de données en utilisant le [DROP MINING MODEL](../dmx/drop-mining-model-dmx.md) instruction. Supprimer complètement une structure d’exploration de données et tous ses modèles d’exploration de données associée à partir de la base de données en utilisant le [DROP MINING STRUCTURE](../dmx/drop-mining-structure-dmx.md) instruction.  
  
 Pour en savoir plus sur les tâches d’exploration de données que vous pouvez effectuer à l’aide d’instructions DMX, consultez [Data Mining Extensions &#40;DMX&#41; référence des instructions](../dmx/data-mining-extensions-dmx-statements.md).  
  
 [Retour à instructions DMX](#BKMK_DMXStatements)  
  
###  <a name="BKMK_DML"></a> Instructions de Manipulation de données  
 Les instructions de manipulation de données dans DMX permettent d'utiliser des modèles d'exploration de données existants, d'explorer ces modèles et de créer des prévisions dans ces derniers. Les instructions de manipulation de données dans DMX font partie du langage de manipulation de données (DML).  
  
 En utilisant les instructions de manipulation de données dans DMX, vous pouvez effectuer les tâches suivantes :  
  
-   Former un modèle d’exploration de données à l’aide de la [INSERT INTO](../dmx/insert-into-dmx.md) instruction. Cette opération n'insert pas les données source réelles dans un modèle d'exploration de données, mais crée plutôt une abstraction qui décrit le modèle d'exploration de données que l'algorithme crée. La requête source pour une instruction INSERT INTO est décrite dans [ \<requête de source de données >](../dmx/source-data-query.md).  
  
-   Étendre l’instruction SELECT pour parcourir les informations qui sont calculées pendant l’apprentissage du modèle et stockées dans le modèle d’exploration de données, telles que les statistiques de la source de données. Voici les clauses que vous pouvez inclure pour étendre la puissance de l’instruction SELECT :  
  
    -   [SELECT DISTINCT FROM &#60;modèle &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
    -   [SELECT FROM &#60;modèle&#62;. CONTENU &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)  
  
    -   [SELECT FROM &#60;modèle&#62;. CAS &#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)  
  
    -   [SELECT FROM &#60;modèle&#62;. SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
    -   [SELECT FROM &#60;modèle&#62;. DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
-   Créer des prédictions basées sur un modèle d’exploration de données existant à l’aide de la [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) clause de l’instruction SELECT. La requête source pour une instruction PREDICTION JOIN est décrite dans [ \<requête de source de données >](../dmx/source-data-query.md).  
  
-   Supprimer toutes les données d’apprentissage à partir d’un modèle ou une structure à l’aide de la [supprimer &#40;DMX&#41; ](../dmx/delete-dmx.md) instruction.  
  
 Pour en savoir plus sur les tâches d’exploration de données que vous pouvez effectuer à l’aide d’instructions DMX, consultez [Data Mining Extensions &#40;DMX&#41; référence des instructions](../dmx/data-mining-extensions-dmx-statements.md).  
  
 [Retour à instructions DMX](#BKMK_DMXStatements)  
  
###  <a name="BKMK_Queries"></a> Principes de base de requête DMX  
 L’instruction SELECT est la base pour la plupart des requêtes DMX. En fonction des clauses que vous utilisez avec ce type d'instruction, vous pouvez explorer ou copier des modèles d'exploration de données, ou effectuer des prévisions dans ces derniers. La requête de prédiction utilise une forme de SELECT pour créer des prédictions basées sur des modèles d’exploration de données existants. Des fonctions augmentent vos capacités à explorer et interroger les modèles d'exploration de données au-delà des possibilités intrinsèques du modèle d'exploration de données.   
  
 Les fonctions DMX permettent d'obtenir des informations qui sont découvertes au cours de l'apprentissage de vos modèles, et de calculer de nouvelles informations. Ces fonctions peuvent être utilisées pour différents objectifs, notamment pour retourner des statistiques décrivant les données sous-jacentes ou l'exactitude d'une prévision ou pour retourner l'explication développée d'une prévision.  
  
 **Pour plus d’informations****informations :** [présentation de l’instruction DMX instruction Select](../dmx/understanding-the-dmx-select-statement.md), [fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md), [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md), [Data Mining Extensions &#40;DMX&#41; référence de fonction  ](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
 [Retour à instructions DMX](#BKMK_DMXStatements)  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des opérateurs](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40;DMX&#41; Conventions de syntaxe](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;DMX&#41; éléments de syntaxe](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
