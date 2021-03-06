---
title: Héritée de Transactions | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], inherited
- child packages
- inherited transactions [Integration Services]
ms.assetid: 90db5564-d41e-4cfe-8c9e-4e68d41eff1c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: aeb90951cea0b50226c2db87e22268822b58b1b4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62767815"
---
# <a name="inherited-transactions"></a>Transactions héritées
  Un package peut en exécuter un autre à l'aide de la tâche d'exécution de package. Le package enfant, qui est celui exécuté par la tâche d'exécution de package, peut créer sa propre transaction sur package, ou hériter de celle du package parent.  
  
 Un package enfant hérite de la transaction sur package parent si les deux conditions suivantes sont réunies :  
  
-   Le package est appelé par une tâche d'exécution de package.  
  
-   La tâche d'exécution de package qui a appelé le package a également joint la transaction sur package parent.  
  
 Les conteneurs et les tâches dans le package enfant ne peuvent pas être joints à la transaction de package parent, à moins que le package enfant lui-même soit joint à la transaction.  
  
## <a name="illustration-of-package-transactions"></a>Illustration de transactions de packages  
 Le diagramme suivant présente trois packages utilisant tous des transactions. Chaque package comprend plusieurs tâches. Afin de mettre en évidence le comportement des transactions, seules les tâches d'exécution de package sont indiquées. Le package A exécute les packages B et C. Le package B exécute à son tour les packages D et E, et le package C exécute le package F.  
  
 Les packages et les tâches ont les attributs de transaction suivants :  
  
-   **TransactionOption** a pour valeur **Required** sur les packages A et C.  
  
-   **TransactionOption** a pour valeur **Supported** sur les packages B et D, et sur les tâches d’exécution des packages B, D et F.  
  
-   **TransactionOption** a pour valeur **NotSupported** sur le package E, et sur les tâches d’exécution des packages C et E.  
  
 ![Flux de transactions héritées](media/mw-dts-executepack.gif "Flux de transactions héritées")  
  
 Seuls les packages B, D et F peuvent hériter des transactions de leurs packages parents.  
  
 Les packages B et D héritent de la transaction démarrée par le package A.  
  
 Les package F hérite de la transaction démarrée par le package C.  
  
 Les packages A et C contrôlent leurs propres transactions.  
  
 Le package E n'utilise pas de transactions.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Configurer un package pour l’utilisation de transactions](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
