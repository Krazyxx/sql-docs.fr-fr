---
title: Configurer le journal d’historique des travaux | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d6d18a4654fc14aa5c0997734184ec700fad3162
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65095509"
---
# <a name="set-up-the-job-history-log"></a>Configurer le journal d'historique des travaux
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique décrit la façon de définir le journal de l'historique des travaux [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
-   **Avant de commencer :**  [Sécurité](#Security)  
  
-   **Pour configurer le journal d’historique des travaux, avec :** [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
**Pour définir le journal d'historique des travaux**  
  
1.  Dans **l’Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés de l'Agent SQL Server** , sélectionnez la page **Historique** .  
  
4.  Sélectionnez les options appropriées :  
  
    1.  Activez la case à cocher **Limiter la taille de l'historique des travaux**, puis tapez le nombre maximal de lignes pour le journal de l'historique des travaux, ainsi que le nombre maximal de lignes par travail.  
  
    2.  Activez la case à cocher **Supprimer automatiquement l'historique de l'agent**, puis spécifiez une période de temps, de telle façon que l'historique antérieur à cette période soit purgé du journal.  
  
## <a name="see-also"></a> Voir aussi  
[Implémenter des travaux](../../ssms/agent/implement-jobs.md)  
[Surveiller l'activité des travaux](../../ssms/agent/monitor-job-activity.md)  
[Créer des travaux](../../ssms/agent/create-jobs.md)  
  
