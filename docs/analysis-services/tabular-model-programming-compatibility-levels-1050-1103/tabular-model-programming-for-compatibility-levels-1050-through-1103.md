---
title: Analysis Services (tabulaire) modèle de programmation pour les niveaux de compatibilité 1050-1103 | Microsoft Docs
ms.date: 05/14/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ddc25ab4d4358c8000c5a7bfe9a9de9dd5e87ed6
ms.sourcegitcommit: 4cb96c291529e9bdf0a95fb3610b350583eb36d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65709141"
---
# <a name="tabular-model-programming-for-compatibility-levels-1050-through-1103"></a>Programmation de modèles tabulaires pour les niveaux de compatibilité 1050 à 1103
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

  Les modèles tabulaires utilisent des constructions relationnelles pour modéliser les données Analysis Services utilisées par les applications analytiques et de rapports. Ces modèles s'exécutent sur une instance Analysis Service qui est configurée pour le mode tabulaire, en utilisant un moteur d'analyse en mémoire pour le stockage et les analyses de table rapides qui agrègent et calculent des données à mesure qu'elles sont demandées.  
  
 Si les besoins de votre solution BI personnalisée sont mieux remplis par une base de données de modèles tabulaires, vous pouvez utiliser l'une des bibliothèques Analysis Services et interfaces de programmation clientes pour intégrer votre application à des modèles tabulaires sur une instance Analysis Services. Pour interroger et calculer des données de modèle tabulaire, vous pouvez utiliser MDX ou DAX incorporé dans votre code.  
  
 Pour les modèles tabulaires créés dans les versions antérieures d’Analysis Services, dans les modèles particuliers aux niveaux de compatibilité 1050 à 1103, les objets que vous travaillez par programmation dans AMO, ADOMD.NET, XMLA ou OLE DB sont fondamentalement les mêmes pour les deux sous forme de tableau et solutions multidimensionnelles. Plus précisément, les métadonnées d’objets définies pour les modèles multidimensionnels sont également utilisée pour les niveaux de compatibilité de modèle tabulaire 1050-1103.  
  
 À compter de SQL Server 2016, les modèles tabulaires peuvent créés ou mis à niveau vers le niveau de compatibilité 1200 ou supérieur, qui utilise des métadonnées tabulaires pour définir le modèle. Métadonnées et programmabilité sont fondamentalement différentes à ce niveau. Consultez [tabulaire modèle de programmation pour le niveau de compatibilité 1200 et supérieur](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md) et [mettre à niveau Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md) pour plus d’informations.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Annotations CSDL pour Business Intelligence &#40;CSDLBI&#41;](https://docs.microsoft.com/bi-reference/csdl/csdl-annotations-for-business-intelligence-csdlbi)  
  
 [Présentation du modèle d’objet tabulaire à compatibilité niveaux 1050 à 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [Informations techniques de référence sur les annotations pour le décisionnel dans CSDL](https://docs.microsoft.com/bi-reference/csdl/technical-reference-for-bi-annotations-to-csdl)  
  

[IMDEmbeddedData, interface](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/imdembeddeddata-interface.md)


  
  
