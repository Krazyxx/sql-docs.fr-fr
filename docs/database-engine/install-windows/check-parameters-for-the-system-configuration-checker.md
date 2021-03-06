---
title: Paramètres de l’outil d’analyse de configuration système | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, system configuration checks
- failed system configuration checks [SQL Server]
- verifying configuration before installation
- SCC [SQL Server]
- system configuration checker
- scanning computer before installation [SQL Server]
- checking configuration before installation
- status information [SQL Server], system configuration checker
- parameters [SQL Server], system configuration checker
- configuration checkers [SQL Server]
- Setup [SQL Server], system configuration checker
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 869461d6054d3db263f96604c16bae39b63293a5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622077"
---
# <a name="check-parameters-for-the-system-configuration-checker"></a>Paramètres de l’outil d’analyse de configuration système

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Lors de l'exécution du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'outil d'analyse de configuration système (SCC) analyse l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera installé. L'outil SCC recherche toute anomalie susceptible d'empêcher une installation correcte de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Avant que le programme d'installation ne démarre l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le SCC extrait l'état de chaque élément. Puis, il compare le résultat avec les conditions requises et fournit une aide pour la suppression des problèmes importants.  
  
L'Outil d'analyse de configuration système génère un rapport qui contient une brève description de chaque règle exécutée et de l'état d'exécution. Le rapport de contrôle de configuration du système se trouve à l’emplacement %programfiles%\Microsoft SQL Server\140\Setup Bootstrap\Log\\\<YYYYMMDD_HHMM>\\\..    
  
Pour plus d’informations, consultez les liens suivants :

- [Configurations matérielle et logicielle requises pour l’installation de SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
- [Considérations sur la sécurité pour une installation SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
- [Mises à niveau de la version et de l’édition prises en charge](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
  
