---
title: Composants du pilote OLE DB Driver pour SQL Server | Microsoft Docs
description: Composants OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 164b87135257f812898c254fd7fd4f5c762c72ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735247"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Composants OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server contient les composants suivants :  

|Composant|Description|  
|---------------|-----------------|  
|msoledbsql.dll|Le fichier de bibliothèque de liens dynamiques (DLL) qui contient l’ensemble du pilote OLE DB pour les fonctionnalités de SQL Server.|  
|msoledbsqlr.rll|Le fichier de ressources qui accompagne cet article pour le pilote OLE DB pour la bibliothèque de SQL Server.|   
|msoledbsql.h|Le pilote OLE DB pour le fichier d’en-tête SQL Server qui contient toutes les nouvelles définitions nécessaires pour pouvoir utiliser le pilote OLE DB pour SQL Server. Ce fichier d’en-tête remplace le fichier d’en-tête sqloledb.h.<br /><br /> Remarque : Vous pouvez référencer msoledbsql.h et sqloledb.h dans même programme tant que sqloledb.h soit défini en premier.|  
|msoledbsql.lib|Le fichier bibliothèque nécessaire pour appeler directement la [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) (fonction) qui fait partie du pilote OLE DB pour SQL Server.<br /><br /> Remarque : Si vous référencez le fichier msoledbsql.lib dans votre code de programmation, vous devez vérifier que le fichier msoledbsql.dll se trouve dans votre chemin système et dans le chemin système des utilisateurs qui emploient votre application.|  

## <a name="see-also"></a> Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
