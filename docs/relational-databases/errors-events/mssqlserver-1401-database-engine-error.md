---
title: MSSQLSERVER_1401 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 23dc13b8dac23914cc4f337e4b39fbf84ee4b782
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700977"
---
# <a name="mssqlserver1401"></a>MSSQLSERVER_1401
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1401|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBM_MASTERSTARTUP|  
|Texte du message|Le démarrage de la routine du thread principal pour le processus de mise en miroir de la base de données a échoué pour la raison suivante : %ls. Corrigez la cause de cette erreur et redémarrez le service SQL Server.|  
  
## <a name="explanation"></a>Explication  
Le démarrage du thread de contrôle de la mise en miroir a échoué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], recherchez l'erreur associée qui a précédé ce message. Corrigez la cause de cette erreur, puis redémarrez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER).  
  
## <a name="see-also"></a> Voir aussi  
[Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser](~/database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
