---
title: 'Exemple : Restauration en ligne d’un fichier en lecture seule (mode de récupération complète) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- online restores [SQL Server], full recovery model
- restore sequences [SQL Server], online
ms.assetid: 7ea2d2af-086f-48dc-9636-38dc194c7090
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1b104eab4067f4eeb435c397708d0cad4d1e9cd4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876056"
---
# <a name="example-online-restore-of-a-read-only-file-full-recovery-model"></a>Exemple : Restauration en ligne d’un fichier en lecture seule (mode de restauration complète)
  Cette rubrique concerne les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui relèvent du mode de récupération complète et qui contiennent plusieurs fichiers ou groupes de fichiers.  
  
 Dans cet exemple, une base de données appelée `adb`qui utilise le mode de restauration complète, contient trois groupes de fichiers. Le groupe de fichiers `A` est en lecture-écriture, et les groupes de fichiers `B` et `C` sont en lecture seule. Au départ, tous les groupes de fichiers sont en ligne.  
  
 Un fichier en lecture seule `b1`du groupe de fichiers `B` de la base de données `adb` doit être restauré. Une sauvegarde ayant été réalisée depuis que le fichier est devenu accessible en lecture seule ; les sauvegardes du journal ne sont pas nécessaires. Le groupe de fichiers `B` est hors connexion pendant la restauration, mais le reste de la base de données demeure en ligne.  
  
## <a name="restore-sequence"></a>Séquence de restauration  
  
> [!NOTE]  
>  La syntaxe pour une séquence de restauration en ligne est la même que pour une séquence de restauration hors connexion.  
  
 Pour restaurer le fichier, l'administrateur de la base de données doit utiliser la séquence de restauration suivante :  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup  
WITH RECOVERY   
```  
  
 Le groupe de fichiers B est maintenant en ligne.  
  
## <a name="additional-examples"></a>Autres exemples  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de récupération simple&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers uniquement &#40;mode de récupération simple&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture seule &#40;mode de récupération simple&#41;](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de restauration complète&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers &#40;mode de récupération complète&#41;](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture/écriture &#40;mode de récupération complète&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Restauration en ligne &#40;SQL Server&#41;](online-restore-sql-server.md)   
 [Vue d’ensemble de la restauration et de la récupération &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)   
 [Restaurations de fichiers &#40;mode de récupération complète&#41;](file-restores-full-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
