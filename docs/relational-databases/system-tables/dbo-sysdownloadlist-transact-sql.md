---
title: dbo.sysdownloadlist (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysdownloadlist
- sysdownloadlist_TSQL
- dbo.sysdownloadlist_TSQL
- sysdownloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sysdownloadlist system table
ms.assetid: 71087a4c-e829-488e-aa7d-a9476e2b4779
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d0568403cb7f5bdf48d9be33e1b40f0be3fc1c33
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470827"
---
# <a name="dbosysdownloadlist-transact-sql"></a>dbo.sysdownloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient la file d'attente des instructions de téléchargement pour l'ensemble des serveurs cibles.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**Int**|Colonne d'identité indiquant la séquence naturelle d'insertion des lignes|  
|**source_server**|**sysname**|Nom du serveur source|  
|**operation_code**|**tinyint**|Code d'opération pour le travail :<br /><br /> **1** = INS (INSERTION)<br /><br /> **2** = UPD (MISE À JOUR)<br /><br /> **3** = SUPPR (SUPPRESSION)<br /><br /> **4** = START<br /><br /> **5** = ARRÊTER|  
|**object_type**|**tinyint**|Code du type d'objet.|  
|**object_id** <sup>1</sup>|**uniqueidentifier**|Numéro d'identification de l'objet.|  
|**target_server**|**sysname**|Nom du serveur cible|  
|**error_message**|**nvarchar(1024)**|Message d'erreur si le serveur cible rencontre une erreur lors du traitement de la ligne spécifique|  
|**date_posted**|**datetime**|Date et heure à laquelle le travail a été posté vers le serveur cible|  
|**date_downloaded**|**datetime**|Date et heure à laquelle le travail a été téléchargé pour la dernière fois|  
|**status**|**tinyint**|État du travail :<br /><br /> **0** ne = pas encore téléchargé<br /><br /> **1** = téléchargé avec succès|  
|**deleted_object_name**|**sysname**|Nom de l'objet supprimé.|  
  
 <sup>1</sup> le **object_id** colonne peut être une valeur de **-1**, qui correspond à une valeur ALL si la **operation_code** colonne est une valeur de suppression.  
  
  
