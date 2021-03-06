---
title: Row, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords:
- Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 041356f05daaaef50e6e81d995209ab5379fc901
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63192823"
---
# <a name="row-property-ado"></a>Row, propriété (ADO)
Obtient ou définit un OLE DB **ligne** objet à partir d’ou sur un [ADORecordConstruction, Interface](../../../ado/reference/ado-api/adorecordconstruction-interface.md) objet. Lorsque vous utilisez **put Row** pour définir un **ligne** de l’objet, une ligne est transformée en ADO **enregistrement** objet.  
  
## <a name="readwritesyntax"></a>Read/write.Syntax  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ppRow*  
 Pointeur vers un OLE DB **ligne** objet.  
  
 *PRow*  
 OLE DB **ligne** objet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété renvoie les valeurs HRESULT standard, notamment S_OK et E_FAIL.  
  
## <a name="applies-to"></a>S'applique à  
 [ADORecordConstruction, interface](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
