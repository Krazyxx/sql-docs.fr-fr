---
title: 'Étude de cas : Création d’un écosystème d’entreprise avec Microsoft Dynamics ERP et de réplication SQL Server 2014 for Scalability and Performance | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 2b0b5ab7-4e08-431a-bd59-360177c4565c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 64a1423295b8117640de555a7132a44af98b87c0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470100"
---
# <a name="case-study-building-an-enterprise-ecosystem-with-microsoft-dynamics-erp-and-sql-server-2014-replication-for-scalability-and-performance"></a>Étude de cas : Création d’un écosystème d’entreprise avec Microsoft Dynamics ERP et de réplication SQL Server 2014 pour l’évolutivité et performances

  **Résumé :** Ce document couvre les scénarios suivants :  
Comment utiliser la réplication transactionnelle dans SQL Server 2014 pour distribuer les transactions à partir de clients Dynamics AX sur plusieurs nœuds. Comme les données sont conservées sur les nœuds en temps réel, la réplication transactionnelle fournit la redondance des données, ce qui augmente la disponibilité des données pour une analyse des performances plus efficace.  
Comment comprendre les spécificités impliquées tout en tirant parti de la réplication transactionnelle pour générer des écosystèmes d’entreprise hautement évolutifs dans Microsoft Dynamics ERP. Fournir une évolutivité et des performances élevées sans personnaliser les fonctionnalités prédéfinies AX.  
  
 La réplication transactionnelle est utilisée habituellement dans des flux de travail de serveur à serveur qui nécessitent un débit élevé. Ceux-ci incluent des scénarios, tels que l’amélioration de la disponibilité et de l’évolutivité, la création de rapports et d’entrepôts de données, l’intégration des données à partir de plusieurs sites, l’intégration de données hétérogènes et le déchargement du traitement par lots. Ce livre blanc décrit un scénario distinct et les modèles associés où la réplication transactionnelle est exploitée dans Microsoft Dynamics ERP. Il couvre également les défis et les meilleures pratiques quand la réplication transactionnelle est envisagée pour générer des solutions d’entreprise spécifiques au système ERP (Enterprise Resource Planning), ainsi que l’analyse des performances à différents stades.  
  
 Ce contenu convient aux développeurs, architectes et administrateurs de base de données. Il est supposé que les lecteurs de ce livre blanc ont des notions de base de SQL Server 2008, 2012 ou 2014, et connaissent l’administration SQL Server.  
  
 **Enregistreur :** Prabhakaran Sethuraman (PRAB), Microsoft  
  
 **Réviseurs techniques :** Prabhakaran Sethuraman (PRAB), Microsoft ; Santosh Padhy, Microsoft ; Pavel Majstrov, Microsoft ; Karthik Sankaranarayanan, Microsoft ; Jon Acone, Microsoft ; David Stahlkopf, Microsoft ; Kent Oldenburger, Microsoft ; Mandi Ohlinger, Microsoft ; Jason Roth, Microsoft  
  
 **Date de publication :** octobre 2015  
  
 **S’applique à :** SQL Server 2008, SQL Server 2012 et SQL Server 2014  
  
 Pour consulter le document, téléchargez le  
        [Étude de cas : Création d’un écosystème d’entreprise avec Microsoft Dynamics ERP et la réplication SQL Server 2014 pour l’évolutivité et performances](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx) document Word.  
  
  
