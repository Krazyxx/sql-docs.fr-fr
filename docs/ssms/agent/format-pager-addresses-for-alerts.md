---
title: Mettre en forme des adresses de radiomessagerie pour les alertes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4d47ffe7db5442f3ad238825d9c8012a05f4ef4b
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65096584"
---
# <a name="format-pager-addresses-for-alerts"></a>Format Pager Addresses for Alerts
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment mettre en fou deme les adresses de radiomessagerie pour les alertes de l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour mettre en forme des adresses de radiomessagerie, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent afficher des informations sur une alerte. Les autres utilisateurs doivent disposer du rôle de base de données fixe **SQLAgentOperatorRole** dans la base de données **msdb** .  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-format-pager-addresses"></a>Pour mettre en forme des adresses de radiomessagerie  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus pour développer le serveur qui contient l'alerte que vous souhaitez envoyer à un récepteur de radiomessagerie.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server** , puis sélectionnez **Propriétés**.  
  
3.  Sous **Sélectionner une page**, sélectionnez **Système d'alerte**.  
  
4.  Dans les zones **Ligne À** et **Ligne Cc** du champ **Format d’adresse pour les messages de radiomessagerie** , entrez le préfixe ou le suffixe de l’adresse de radiomessagerie. L'adresse réelle de radiomessagerie de l'opérateur est insérée lors de l'envoi d'une notification.  
  
5.  Dans la zone **Objet** , entrez le préfixe ou le suffixe de la ligne Objet.  
  
6.  Cochez la case **Inclure le corps du message dans la page de notification** pour inclure l’e-mail complet, ainsi que le message de radiomessagerie (contrairement à la ligne Objet uniquement).  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
