---
title: ExecuteOptionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ExecuteOptionEnum
helpviewer_keywords:
- ExecuteOptionEnum enumeration [ADO]
ms.assetid: 68bfa83a-5df4-4bef-8736-0f88ae8c29ea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7512f456d1423caf6318903119c2ad55c1938dec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301293"
---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
Spécifie comment un fournisseur doit exécuter une commande.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adAsyncExecute**|0x10|Indique que la commande doit s’exécuter de façon asynchrone.<br /><br /> Cette valeur ne peut pas être combinée avec la [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valeur **adCmdTableDirect**.|  
|**adAsyncFetch**|0x20|Indique que les lignes restantes après la quantité spécifiée dans le [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) propriété doit-elle être récupérée de manière asynchrone.|  
|**adAsyncFetchNonBlocking**|0x40|Indique que le thread principal ne bloque jamais lors de la récupération. Si la ligne demandée n’a pas été récupérée, la ligne actuelle déplace automatiquement à la fin du fichier.<br /><br /> Si vous ouvrez un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) à partir d’un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) contenant un stocké de façon permanente **Recordset**, **adAsyncFetchNonBlocking** n’aura pas un effet ; l’opération doit être synchrone et bloquante.<br /><br /> **adAsynchFetchNonBlocking** n’a aucun effet lorsque la [adCmdTableDirect](../../../ado/reference/ado-api/commandtypeenum.md) option est utilisée pour ouvrir le **Recordset**.|  
|**adExecuteNoRecords**|0x80|Indique que le texte de commande est une commande ou une procédure stockée qui ne retourne pas de lignes (par exemple, une commande qui insère des données uniquement). Si toutes les lignes sont récupérées, elles sont ignorées et pas retournées.<br /><br /> **adExecuteStream** peut uniquement être passée comme paramètre facultatif pour le **commande** ou **connexion exécuter** (méthode).|  
|**adExecuteStream**|0x400|Indique que les résultats d’une exécution de commande doivent être retournés sous forme de flux.<br /><br /> **adExecuteStream** peut uniquement être passée comme paramètre facultatif pour le **Command Execute** (méthode).|  
|**adExecuteRecord**||Indique que le **CommandText** est une commande ou une procédure stockée qui retourne une seule ligne qui doit être retournée comme un **enregistrement** objet.|  
|**adOptionUnspecified**|-1|Indique que la commande n’est pas spécifiée.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.ExecuteOption.ASYNCEXECUTE|  
|AdoEnums.ExecuteOption.ASYNCFETCH|  
|AdoEnums.ExecuteOption.ASYNCFETCHNONBLOCKING|  
|AdoEnums.ExecuteOption.NORECORDS|  
|AdoEnums.ExecuteOption.UNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Execute, méthode (commande ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|[Execute, méthode (objet Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|  
|[Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Requery, méthode](../../../ado/reference/ado-api/requery-method.md)|
