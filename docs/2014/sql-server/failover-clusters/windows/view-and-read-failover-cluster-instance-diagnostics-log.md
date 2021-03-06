---
title: Afficher et lire le journal de diagnostic de l’instance de cluster de basculement | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 68074bd5-be9d-4487-a320-5b51ef8e2b2d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 19308ee2838238f0dea6cfdaeb228a250591613b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63049335"
---
# <a name="view-and-read-failover-cluster-instance-diagnostics-log"></a>Afficher et lire le journal de diagnostic de l'instance de cluster de basculement
  Toutes les erreurs et tous les événements d'avertissements critiques pour la DLL de ressource SQL Server sont écrits dans le journal des événements Windows. Un journal en cours des informations de diagnostic spécifiques de SQL Server est capturé par la procédure stockée système [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) ; il est écrit dans les fichiers journaux de diagnostics du cluster de basculement de SQL Server (également appelés journaux *SQLDIAG*).  
  
-   **Avant de commencer :**  [Recommandations](#Recommendations), [sécurité](#Security)  
  
-   **Pour afficher le journal de Diagnostic à l’aide de :**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
-   **Pour les paramètres de journal de Diagnostic à configurer, à l’aide de :** [Transact-SQL](#TsqlConfigure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
 Par défaut, le SQLDIAG sont stockés dans un dossier LOG local du répertoire d’instance SQL Server, par exemple, « C\Program Files\Microsoft SQL Server\MSSQL12. \<Nom_instance > \MSSQL\LOG » du nœud propriétaire de l’Instance de Cluster de basculement (FCI) AlwaysOn. La taille de chaque fichier journal SQLDIAG est fixée à 100 Mo. Dix fichiers journaux de ce type sont stockés sur l'ordinateur avant qu'ils ne soient recyclés pour les nouveaux journaux.  
  
 Les journaux utilisent le format de fichier d'événements étendus. La fonction système **sys.fn_xe_file_target_read_file** peut être utilisée pour lire les fichiers créés par les événements étendus. Au format XML, un événement par ligne est retourné. Interrogez la vue système pour analyser les données XML définies comme ensemble de résultats. Pour plus d’informations, consultez [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 L’autorisation VIEW SERVER STATE est exigée pour exécuter **fn_xe_file_target_read_file**.  
  
 Ouvrez SQL Server Management Studio en tant qu'administrateur  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour afficher les fichiers journaux de diagnostics :**  
  
1.  Dans le menu de **Fichier** , sélectionnez **Ouvrir**, puis **Fichier**et choisissez le fichier journal de diagnostics à afficher.  
  
2.  Les événements sont affichés sous forme de lignes dans le volet droit. Par défaut, seules les colonnes **name**et **timestamp** sont affichées.  
  
     Cela permet également d'activer le menu **ExtendedEvents** .  
  
3.  Pour afficher plus de colonnes, allez dans le menu de **ExtendedEvents** , puis sélectionnez **Choisir les colonnes**.  
  
     Une boîte de dialogue dans laquelle vous pouvez sélectionner les colonnes à afficher s'ouvre.  
  
4.  Vous pouvez filtrer et trier les données d'événement à l'aide du menu **ExtendedEvents** , en sélectionnant l'option **Filtre** .  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour afficher les fichiers journaux de diagnostics :**  
  
 Pour consulter tous les éléments de journal du fichier journal SQLDIAG, utilisez la requête suivante :  
  
```  
SELECT  
xml_data.value('(event/@name)[1]','varchar(max)') AS 'Name'  
,xml_data.value('(event/@package)[1]','varchar(max)') AS 'Package'  
,xml_data.value('(event/@timestamp)[1]','datetime') AS 'Time'  
,xml_data.value('(event/data[@name=''state'']/value)[1]','int') AS 'State'  
,xml_data.value('(event/data[@name=''state_desc'']/text)[1]','varchar(max)') AS 'State Description'  
,xml_data.value('(event/data[@name=''failure_condition_level'']/value)[1]','int') AS 'Failure Conditions'  
,xml_data.value('(event/data[@name=''node_name'']/value)[1]','varchar(max)') AS 'Node_Name'  
,xml_data.value('(event/data[@name=''instancename'']/value)[1]','varchar(max)') AS 'Instance Name'  
,xml_data.value('(event/data[@name=''creation time'']/value)[1]','datetime') AS 'Creation Time'  
,xml_data.value('(event/data[@name=''component'']/value)[1]','varchar(max)') AS 'Component'  
,xml_data.value('(event/data[@name=''data'']/value)[1]','varchar(max)') AS 'Data'  
,xml_data.value('(event/data[@name=''info'']/value)[1]','varchar(max)') AS 'Info'  
FROM  
 ( SELECT object_name AS 'event'  
  ,CONVERT(xml,event_data) AS 'xml_data'  
  FROM sys.fn_xe_file_target_read_file('C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log\SQLNODE1_MSSQLSERVER_SQLDIAG_0_129936003752530000.xel',NULL,NULL,NULL)   
)   
AS XEventData  
ORDER BY Time;  
  
```  
  
> [!NOTE]  
>  Vous pouvez filtrer les résultats pour des composants spécifiques ou exécuter une déclaration à l'aide de la clause WHERE.  
  
##  <a name="TsqlConfigure"></a> Utilisation de Transact-SQL  
 **Pour configurer les propriétés du journal de diagnostics**  
  
> [!NOTE]  
>  Pour obtenir un exemple de cette procédure, consultez [Exemple (Transact-SQL)](#TsqlExample)plus loin dans cette section.  
  
 À l’aide de l’instruction de langage de définition de données (DDL), `ALTER SERVER CONFIGURATION`, vous pouvez démarrer ou arrêter la journalisation des données de diagnostic capturées par le [sp_server_diagnostics &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) procédure et les journaux SQLDIAG de jeu paramètres de configuration, tels que le nombre de substitutions du fichier journal, taille du fichier journal et son emplacement. Pour plus d'informations sur la syntaxe, consultez [Setting diagnostic log options](/sql/t-sql/statements/alter-server-configuration-transact-sql#Diagnostic).  
  
###  <a name="ConfigTsqlExample"></a> Exemples (Transact-SQL)  
  
####  <a name="TsqlExample"></a> Setting diagnostic log options  
 Les exemples de cette section montrent comment définir les valeurs de l'option de journal de diagnostics.  
  
##### <a name="a-starting-diagnostic-logging"></a>A. Début de la journalisation des diagnostics  
 L'exemple suivant démarre la journalisation de données de diagnostics.  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG ON;  
```  
  
##### <a name="b-stopping-diagnostic-logging"></a>B. Fin de la journalisation des diagnostics  
 L'exemple suivant met fin à la journalisation des données de diagnostics.  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG OFF;  
```  
  
##### <a name="c-specifying-the-location-of-the-diagnostic-logs"></a>C. Spécification de l'emplacement des journaux de diagnostics  
 L'exemple suivant définit l'emplacement des journaux de diagnostics sur le chemin d'accès au fichier spécifié.  
  
```  
ALTER SERVER CONFIGURATION  
SET DIAGNOSTICS LOG PATH = 'C:\logs';  
```  
  
##### <a name="d-specifying-the-maximum-size-of-each-diagnostic-log"></a>D. Spécification de la taille maximale de chaque journal de diagnostics  
 L'exemple suivant définit la taille maximale de chaque journal de diagnostics sur 10 mégaoctets.  
  
```  
ALTER SERVER CONFIGURATION   
SET DIAGNOSTICS LOG MAX_SIZE = 10 MB;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Stratégie de basculement pour les instances de cluster de basculement](failover-policy-for-failover-cluster-instances.md)  
  
  
