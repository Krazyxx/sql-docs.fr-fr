---
title: Gestionnaire de connexions Azure Resource Manager | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.openlocfilehash: 8e7786c57909241f17af4247d01759cb77067782
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47699037"
---
# <a name="azure-resource-manager-connection-manager"></a>Gestionnaire de connexions Azure Resource Manager
Le **gestionnaire de connexions Azure Resource Manager** permet à un package SSIS de gérer les ressources Azure à l’aide d’un [principal du service](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

Le **gestionnaire de connexions Azure Resource Manager** est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Pour créer et configurer un **gestionnaire de connexions Azure Resource Manager**, effectuez les étapes suivantes :

1. Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS**, sélectionnez **AzureResourceManager**, puis cliquez sur **Ajouter**.
2. Dans l’**Éditeur du gestionnaire de connexions Azure Resource Manager**, spécifiez l’**ID d’application**, la **clé de l’application** et l’**ID de locataire** du principal du service. Pour plus d’informations sur ces propriétés, consultez [cet](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) article.
3. Cliquez sur **OK** pour fermer la boîte de dialogue.
4. Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .
