---
title: Supprimer le schéma cdc si vous envisagez d’activer la capture de données modifiées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a5d162635a9162871e51fe0664198302804aa487
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855756"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a>Supprimez le schéma cdc si vous envisagez d'activer la capture de données modifiées
  Une base de données contient déjà un schéma cdc. Si vous envisagez d'activer la capture de données modifiées après la mise à niveau, vous devez préalablement abandonner ce schéma cdc. Lorsque vous permettez la capture de données modifiées pour une base de données, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] créera un nouveau schéma nommé cdc.  
  
  
