---
title: StringFormatEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2740c7fb25b71e3588bebb924ea9d5f907e3560
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910898"
---
# <a name="stringformatenum"></a>StringFormatEnum
Spécifie le format lors de la récupération une [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sous forme de chaîne.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adClipString**|2|Délimite les lignes par *RowDelimiter*, les colonnes par *ColumnDelimiter*et les valeurs par null *NullExpr*. Ces trois paramètres de la [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) méthode sont valides uniquement avec un *StringFormat* de **adClipString**.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>S'applique à  
 [GetString, méthode (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
