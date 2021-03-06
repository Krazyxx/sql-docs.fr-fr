---
title: Schéma de FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], table schema
ms.assetid: e1cb3880-cfda-40ac-91fc-d08998287f44
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a5c2c2993b4c6ee002c2be0f8bbae28abaa2d87c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920127"
---
# <a name="filetable-schema"></a>Schéma de FileTable
  Décrit le schéma prédéfini et fixe d'un FileTable.  
  
|Nom d'attribut de fichier|type|Size|Par défaut|Description|Accessibilité du système de fichiers|  
|-------------------------|----------|----------|-------------|-----------------|-------------------------------|  
|**path_locator**|`hierarchyid`|variable|`hierarchyid` qui identifie la position de cet élément.|Position de ce nœud dans le FileNamespace hiérarchique.<br /><br /> Clé primaire de la table|Peut être créée et modifiée en définissant les valeurs de chemin d'accès Windows.|  
|**stream_id**|**[uniqueidentifier] rowguidcol**||Valeur retournée par la fonction `NEWID()`.|ID unique pour les données FILESTREAM.|Non applicable.|  
|**file_stream**|`varbinary(max)`<br /><br /> `filestream`|variable|NULL|Contient les données FILESTREAM.|Non applicable.|  
|**file_type**|`nvarchar(255)`|variable|NULL.<br /><br /> Une opération de création ou de changement de nom dans le système de fichiers remplit la valeur d'extension du fichier à partir du nom.|Représente le type du fichier.<br /><br /> Cette colonne peut être utilisée comme `TYPE COLUMN` lorsque vous créez un index de recherche en texte intégral.<br /><br /> **file_type** est une colonne calculée persistante.|Calculé automatiquement. Ne peut pas être définie.|  
|**Nom**|`nvarchar(255)`|variable|Valeur GUID.|Nom du fichier ou du répertoire.|Peut être créé ou modifié à l'aide des API Windows.|  
|**parent_path_locator**|`hierarchyid`|variable|`hierarchyid` qui identifie le répertoire qui contient cet élément.|`hierarchyid` du répertoire conteneur.<br /><br /> **parent_path_locator** est une colonne calculée persistante.|Calculé automatiquement. Ne peut pas être définie.|  
|**cached_file_size**|`bigint`|||Taille des données FILESTREAM, en octets.<br /><br /> **cached_file_size** est une colonne calculée persistante.|Bien que la taille du fichier mis en cache soit automatiquement mise à jour, elle peut être mal synchronisée dans des circonstances exceptionnelles. Pour calculer la taille exacte, utilisez la fonction `DATALENGTH()`.|  
|**creation_time**|`datetime2(4)`<br /><br /> `not null`|8 octets|Heure actuelle.|Date et heure de création du fichier.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**last_write_time**|`datetime2(4)`<br /><br /> `not null`|8 octets|Heure actuelle.|Date et heure de dernière mise à jour du fichier.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**last_access_time**|`datetime2(4)`<br /><br /> `not null`|8 octets|Heure actuelle.|Date et heure du dernier accès au fichier.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_directory**|`bit`<br /><br /> `not null`|1 octet|FALSE|Indique si la ligne représente un répertoire. Cette valeur est calculée automatiquement et ne peut pas être définie.|Calculé automatiquement. Ne peut pas être définie.|  
|**is_offline**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut de fichier hors connexion.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_hidden**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut de fichier masqué.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_readonly**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut de fichier en lecture seule.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_archive**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut Archive.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_system**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut de fichier système.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
|**is_temporary**|`bit`<br /><br /> `not null`|1 octet|FALSE|Attribut de fichier temporaire.|Calculé automatiquement. Peut également être défini à l'aide d'API Windows.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, modifier et supprimer des FileTables](create-alter-and-drop-filetables.md)  
  
  
