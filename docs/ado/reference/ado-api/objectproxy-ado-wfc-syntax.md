---
title: ObjectProxy (ADO - syntaxe WFC) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af28755fee20c478237edec22936fc694995d554
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63459409"
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO - syntaxe WFC)
Un **ObjectProxy** objet représente un serveur et est retourné par la **createObject** méthode de la [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) objet. La classe ObjectProxy possède une méthode, **appeler**, ce qui peut appeler une méthode sur le serveur et retourner un objet à cet appel.  
  
 **package com.ms.wfc.data**  
  
## <a name="methods"></a>Méthodes  
  
### <a name="call-method-adowfc-syntax"></a>Méthode d’appel (syntaxe ADO/WFC)  
 Appelle une méthode sur le serveur représenté par l’objet ObjectProxy. Si vous le souhaitez, les arguments de méthode peuvent être passés en tant que tableau d’objets.  
  
#### <a name="syntax"></a>Syntaxe  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>Valeur renvoyée  
 Object  
 Objet qui résulte de l’appel de la méthode.  
  
#### <a name="parameters"></a>Paramètres  
 *ObjectProxy*  
 Un **ObjectProxy** objet qui représente le serveur.  
  
 *method*  
 Chaîne contenant le nom de la méthode à appeler sur le serveur.  
  
 *args*  
 Facultatif. Un tableau d’objets qui sont des arguments à la méthode sur le serveur. Types de données Java sont automatiquement converties en types de données pouvant être utilisée sur le serveur.
