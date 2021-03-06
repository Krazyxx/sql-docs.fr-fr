---
title: Initialisation d’objets dans un assembly personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 97ee8e554fa246848b64ebafb0961f35d65f15c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63264719"
---
# <a name="initializing-custom-assembly-objects"></a>Initialisation d'objets Assembly personnalisés
  Dans certains cas, vous pouvez être amené à initialiser des valeurs de propriété et de champ dans vos classes d'assembly personnalisées lorsque vous les instanciez. Vous aurez vraisemblablement besoin d'initialiser vos classes personnalisées avec des valeurs disponibles à partir des collections d'objets globales du rapport. Pour cela, substituez la méthode **OnInit** de l’objet **Code** d’un rapport. Pour accéder à **OnInit**, utilisez l’élément **Code** de la définition de rapport. Il existe deux techniques pour une propriété lors de l’initialisation ou de valeurs de champ des classes dans un assembly personnalisé que vous projetez d’utiliser dans votre rapport : Vous pouvez déclarer et créer une nouvelle instance de votre classe à l’aide **OnInit**, ou vous pouvez appeler une méthode publiquement disponible à l’aide **OnInit**.  
  
## <a name="global-object-collections-and-initialization"></a>Collections d'objets globales et initialisation  
 Plusieurs collections sont disponibles pour initialiser vos variables de classe personnalisées. Vous pouvez utiliser les collections **Globals** et **User**. Les collections **Parameters**, **Fields** et **ReportItems** ne sont pas disponibles au moment où, dans le cycle de vie du rapport, la méthode **OnInit** est appelée. Pour utiliser les collections partagées, **Globals** ou **User**, vous devez inclure la référence d’objet **Report**. Par exemple, pour initialiser votre classe personnalisée selon la langue actuelle de l’utilisateur qui accède au rapport, votre élément **Code** peut se présenter comme suit :  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 L'une des méthodes permettant d'initialiser les valeurs de propriété et de champ d'une classe comme montré précédemment consiste à déclarer votre classe et à créer une nouvelle instance de celle-ci en appelant un constructeur substitué.  
  
 Une autre méthode permettant d’initialiser les valeurs de propriété et de champ des classes dans vos assemblys personnalisés consiste à appeler une méthode publiquement disponible que vous définissez à partir de la méthode **OnInit**. Vous devez d'abord ajouter un nom d'instance pour votre classe dans le fichier de définition de rapport. Une fois que vous avez ajouté la référence d'assembly et le nom d'instance appropriés, vous pouvez appeler votre méthode d'initialisation pour initialiser les valeurs de propriété et de champ pour votre classe. Votre méthode **OnInit** peut se présenter comme suit :  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 Pour plus d’informations sur l’ajout d’une référence d’assembly et d’un nom de l’instance pour votre classe personnalisée, consultez [Ajouter une référence d’assembly à un rapport &#40;SSRS&#41;](../report-design/add-an-assembly-reference-to-a-report-ssrs.md).  
  
 Pour plus d’informations sur les collections d’objets globales, consultez [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'assemblages personnalisés avec des rapports](using-custom-assemblies-with-reports.md)  
  
  
