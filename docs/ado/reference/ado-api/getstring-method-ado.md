---
title: GetString, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords:
- GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1570918c423291b6c4fdd212fcb82f518dfb766e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028196"
---
# <a name="getstring-method-ado"></a>GetString, méthode (ADO)
Retourne le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sous forme de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le **Recordset** comme une valeur de chaîne **Variant** (BSTR).  
  
#### <a name="parameters"></a>Paramètres  
 *StringFormat*  
 Un [StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md) valeur qui spécifie comment la **Recordset** doit être converti en une chaîne. Le *RowDelimiter*, *ColumnDelimiter*, et *NullExpr* paramètres sont utilisés uniquement avec un *StringFormat* de  **adClipString**.  
  
 *NumRows*  
 Facultatif. Le nombre de lignes à convertir dans le **Recordset**. Si *NumRows* n’est pas spécifié, ou si elle est supérieure au nombre total de lignes dans le **Recordset**, puis toutes les lignes dans le **Recordset** sont converties.  
  
 *ColumnDelimiter*  
 Facultatif. Un séparateur utilisé entre les colonnes, si spécifié, sinon le caractère de tabulation.  
  
 *RowDelimiter*  
 Facultatif. Délimiteur utilisé entre les lignes, dans le cas contraire, le caractère de retour chariot.  
  
 *NullExpr*  
 Facultatif. Une expression utilisée à la place d’une valeur null, si spécifié, sinon la chaîne vide.  
  
## <a name="remarks"></a>Notes  
 Données de ligne, mais aucune donnée de schéma, est enregistré dans la chaîne. Par conséquent, un **Recordset** ne peut pas être rouverte à l’aide de cette chaîne.  
  
 Cette méthode est équivalente à la RDO **GetClipString** (méthode).  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetString, exemple de méthode (VB)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
