---
title: Bien démarrer avec SSMA pour DB2 Console (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f245c017-023e-4880-8721-8908d339525e
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 3b8417d75ab0a08532dd073b3ce7f803b3f7490c
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63453315"
---
# <a name="getting-started-with-ssma--for-db2-console-db2tosql"></a>Bien démarrer avec SSMA pour DB2 Console (DB2ToSQL)
Cette section décrit la procédure pour lancer et de vous familiariser avec l’application de console DB2. Dans la liste, dans le présent document, sont les conventions utilisées dans une fenêtre de sortie de Console SSMA classique.  
  
## <a name="launching-ssma-console"></a>Lancement de la Console SSMA  
Utilisez les étapes suivantes pour démarrer l’application de console SSMA :  
  
1.  Accédez à **Démarrer** et pointez sur **tous les programmes**.  
  
2.  Cliquez sur le  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Migration de l’invite de commandes DB2** raccourci.  
  
    Il affiche le menu de l’utilisation de la Console SSMA et `(/? Help)`, pour vous aider à vous familiariser avec l’application de console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procédure d’utilisation de la Console SSMA  
Une fois que la console est lancée avec succès sur votre système Windows, vous pouvez utiliser les étapes suivantes pour travailler dessus :  
  
1.  Configurer la Console SSMA via les fichiers de script. Pour plus d’informations sur cette section, consultez [création de fichiers de Script &#40;DB2ToSQL&#41; ](../../ssma/db2/creating-script-files-db2tosql.md) .  
  
2.  [Création de fichiers de la valeur de la Variable &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
  
3.  [Création des fichiers de connexion de serveur &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
4.  [Exécution de la Console SSMA &#40;DB2ToSQL&#41; ](../../ssma/db2/executing-the-ssma-console-db2tosql.md) selon les besoins de votre projet  
  
Fonctionnalités supplémentaires :  
  
1.  [La gestion des mots de passe](https://msdn.microsoft.com/56d546e3-8747-4169-aace-693302667e94) et exporter / importer sur d’autres ordinateurs de la fenêtre  
  
2.  [Génération de rapports](https://msdn.microsoft.com/69ef5fd9-190d-4c58-8199-b3f77d5e1883) pour afficher le code xml détaillé des rapports pour évaluation /conversion et migration des données de sortie. Rapports d’erreurs détaillées peuvent également être générées pour les commandes Actualiser et la synchronisation.  
  
## <a name="ssma-console-output-conventions"></a>Conventions de sortie de Console SSMA  
Lors de l’exécution les commandes de script SSMA et options, le programme de console affiche les résultats et les messages (information, erreur, etc.) à l’utilisateur sur la console ou le cas échéant, redirige vers un fichier de sortie xml. Chaque type de message dans la sortie est signifié par une couleur unique. Par exemple, le message texte en couleur blanche indique les commandes du fichier de script ; celui de couleur verte représente une invite pour les entrées d’utilisateur et ainsi de suite.  
  
![Output_Oracle de Console SSMA](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "Output_Oracle de Console SSMA")  
  
Interprétation de couleur de la sortie de console dans le tableau suivant :  
  
|Color|Description|  
|---------|---------------|  
|Rouge|Erreur irrécupérable pendant l’exécution|  
|Gris|Cachet de date et l’heure, le message à l’utilisateur|  
|Blanc|Commandes de fichier de script, type de message|  
|Jaune|Warning|  
|Vert|Invite pour l’entrée utilisateur|  
|Cyan|Guide de démarrage, terminer et le résultat d’une opération|  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour DB2](https://msdn.microsoft.com/79fbe8ea-471b-407a-be2a-4100d9b57c61)  
  
