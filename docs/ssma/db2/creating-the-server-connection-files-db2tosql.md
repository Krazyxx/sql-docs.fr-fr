---
title: Création des fichiers de connexion de serveur (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 685419f6-8606-462c-be12-8bace45bede6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ea6d9a77cc7639bc9adc8daa38f12d0e21dbfb71
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298912"
---
# <a name="creating-the-server-connection-files-db2tosql"></a>Création des fichiers de connexion de serveur (DB2ToSQL)
Informations sur le serveur peuvent être spécifiées dans la section serveurs du fichier de script ou dans un fichier de connexion de serveur distinct. Le paramètre de ligne de commande pour le fichier de connexion de serveur est, `-c <serverconnectionfile>`. Si le même id de serveur est présent dans le fichier de script et le fichier de connexion de serveur, la définition du serveur dans le fichier de script est considéré comme.  
  
**Exemple : 1**  
  
```  
<!--Sample of server connection file commands -->  
  
<db2 name="<source-server-unique-name>">  
  
    <standard-mode>  
  
      <connection-provider value ="OleDB Provider"/>  
  
      <!-- Defines server manager to connect.  
  
              Available manager attribute values  
  
              • zOs      - upgrades the project (default)  
  
              • LUW       - displays an error and halts the execution-->  
  
      <database-manager value="$Db2Manager$"/>  
  
      <server-name value="$Db2HostName$" />  
  
      <port value="$Db2Port$" />  
  
      <initial-catalog value="$Db2Instance$" />  
  
      <user-id value="$Db2UserName$" />  
  
      <password value="$Db2Password$"/>  
  
    </standard-mode>  
  
</db2>  
```  
  
```  
<sql-server name="<target-server-unique-name>">  
  
  <sql-server-authentication>  
  
    <server value="<server-name>"/>  
  
    <database value="<database-name>"/>  
  
    <user-id value="<user-name>"/>  
  
    <password value="<password>"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de d’exploitation de la console est [l’exécution de la Console SSMA &#40;DB2ToSQL&#41;](../../ssma/db2/executing-the-ssma-console-db2tosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la console SSMA](https://msdn.microsoft.com/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
