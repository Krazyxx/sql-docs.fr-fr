---
title: onReadyStateChange, événement (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- onReadyStateChange event [ADO]
ms.assetid: bf2ae3ac-bfe4-4709-b50a-ea7c282c3164
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e544c3f373f5e85254d40915e6b6f241a6b70379
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225903"
---
# <a name="onreadystatechange-event-rds"></a>onReadyStateChange, événement (RDS)
Le **onReadyStateChange** événement est appelé chaque fois que la valeur de la [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) modifications apportées aux propriétés.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
onReadyStateChange  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 Le **ReadyState** propriété reflète la progression d’un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet comme il récupère de manière asynchrone des données dans son [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet. Utilisez le **onReadyStateChange** événement pour surveiller les modifications dans le **ReadyState** propriété chaque fois qu’ils se produisent. Cela est plus efficace que de manière périodique et vérifiant la valeur de propriété.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)


