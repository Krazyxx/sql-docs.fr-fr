---
title: Mapper les ports TCP/IP aux nœuds NUMA (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- memory [SQL Server], NUMA
- affinity NUMA
- ports [SQL Server], working with NUMA
- CPU [SQL Server], NUMA support
- NUMA, How to map a port to a NUMA node
- NUMA affinity
- TCP/IP [SQL Server], NUMA support
- non-uniform memory access
ms.assetid: 07727642-0266-4cbc-8c55-3c367e4458ca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 138e5743e18ba6e39aa55aaec6931413dd21175b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62781743"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a>Mapper les ports TCP/IP aux nœuds NUMA (SQL Server)
  Cette rubrique explique comment mapper des ports TCP/IP à des nœuds NUMA (Non-Uniform Memory Access) à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Au démarrage, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] écrit les informations relatives aux nœuds dans le journal des erreurs.  
  
 Pour déterminer quel numéro de nœud utiliser, consultez les informations sur les nœuds dans le journal des erreurs ou dans la vue **sys.dm_os_schedulers** . Pour définir l'adresse et le port TCP/IP d'un ou de plusieurs nœuds, ajoutez une bitmap d'identification de nœud (masque d'affinité) entre crochets après le numéro de port. Les nœuds peuvent être spécifiés au format décimal ou hexadécimal. Pour créer la bitmap, numérotez d'abord les nœuds de droite à gauche en commençant par zéro (par exemple, 76543210). Créez une représentation binaire de la liste des nœuds en attribuant la valeur 1 aux nœuds que vous souhaitez utiliser et la valeur 0 aux nœuds que vous ne souhaitez pas utiliser. Par exemple, pour utiliser les nœuds NUMA 0, 2 et 5, spécifiez 00100101.  
  
|||  
|-|-|  
|Numéro de nœud NUMA|76543210|  
|Masque pour 0, 2 et 5 en comptant à partir de la droite|00100101|  
  
 Convertissez la représentation binaire (00100101) au format décimal `[37]`ou hexadécimal `[0x25]`. Pour écouter tous les nœuds, n'indiquez aucun identificateur de nœud.  
  
 Si un port est mappé à plusieurs nœuds NUMA, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attribue les connexions aux nœuds les unes après les autres sans chercher à équilibrer la charge entre les nœuds.  
  
> [!NOTE]  
>  Pour activer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour écouter sur plusieurs ports TCP pour chaque adresse IP, consultez [Configurer le moteur de base de données de manière à écouter sur plusieurs ports TCP](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a>Pour mapper un port TCP/IP à un nœud NUMA  
  
1.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], développez **Configuration du réseau SQL Server**, puis cliquez sur **Protocoles pour** *\<nom_instance>*.  
  
2.  Dans le volet de détails, double-cliquez sur **TCP/IP**.  
  
3.  Sous l'onglet **Adresses IP** , dans la zone **Port TCP** de la section correspondant à l'adresse IP à configurer, ajoutez l'identificateur du nœud NUMA entre crochets, après le numéro de port. Par exemple, pour le port TCP 1500 et les nœuds 0, 2 et 5, utilisez `1500[37]` ou `1500[0x25]`.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer SQL Server pour utiliser Soft-NUMA &#40;SQL Server&#41;](soft-numa-sql-server.md)  
  
  
