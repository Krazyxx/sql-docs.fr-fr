---
title: Déconnexion et reconnexion du Recordset | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0cefdb81aa9e9a1a5f7ad7ba1f6db86d1ae95e2d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161712"
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>Déconnexion et reconnexion du recordset
Une des fonctionnalités plus puissantes d’ADO est la capacité à ouvrir un jeu d’enregistrements côté client à partir d’une source de données, puis vous déconnectez le jeu d’enregistrements à partir de la source de données. Une fois que le jeu d’enregistrements a été déconnecté, la connexion à la source de données peut être fermée, libérant ainsi les ressources sur le serveur utilisé pour assurer la maintenance. Vous pouvez continuer à afficher et modifier les données dans le jeu d’enregistrements pendant qu’il est déconnecté et vous reconnecter à la source de données et envoyer vos mises à jour en mode batch.  
  
 Pour déconnecter un jeu d’enregistrements, ouvrez-le dans un emplacement du curseur d’adUseClient et puis définissez la propriété ActiveConnection égale à Nothing. (Les utilisateurs C++ doivent affecter ActiveConnection égale à NULL pour vous déconnecter.)  
  
 Nous allons utiliser un jeu d’enregistrements déconnecté plus loin dans cette section lorsque nous aborderons la persistance des recordsets pour résoudre un scénario dans lequel nous avons besoin pour que les données dans un jeu d’enregistrements disponible pour une application, tandis que l’ordinateur client n’est pas connecté à un réseau.  
  
## <a name="see-also"></a>Voir aussi  
 [Mode batch](../../../ado/guide/data/batch-mode.md)
