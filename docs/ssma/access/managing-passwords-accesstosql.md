---
title: La gestion des mots de passe (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b099d0f9-dd37-4c87-8b6f-ed0177881ea4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: bfa7b7481589ccb636147b3842a15b92f1a59d43
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63453688"
---
# <a name="managing-passwords-accesstosql"></a>La gestion des mots de passe (AccessToSQL)
Cette section concerne la sécurisation des mots de passe de base de données et la procédure pour importer ou exporter les sur les serveurs :  
  
1.  Sécurisation de mot de passe  
  
2.  Exportation ni importation de mot de passe chiffré  
  
## <a name="securing-password"></a>Sécurisation de mot de passe  
SSMA vous permet de sécuriser votre mot de passe d’une base de données.  
  
Utilisez la procédure suivante pour implémenter une connexion sécurisée :  
  
Spécifiez un mot de passe à l’aide d’une des trois méthodes suivantes :  
  
1.  **Texte clair :** Tapez le mot de passe de base de données dans l’attribut de valeur du nœud « password ». Il se trouve sous le nœud de définition de serveur dans la section serveur du fichier de script ou du fichier de connexion de serveur.  
  
    Les mots de passe en texte clair ne sont pas sécurisés. Par conséquent, vous rencontrerez le message d’avertissement suivant dans la sortie de console : *« Serveur &lt;id serveur&gt; mot de passe n’est fourni sous forme de texte en clair non sécurisées, application de Console SSMA fournit une option pour protéger le mot de passe via le chiffrement, consultez option - securepassword dans le fichier d’aide SSMA pour en savoir plus informations ».*  
  
    **Mots de passe chiffrés :** Le mot de passe, dans ce cas, est stockée sous forme chiffrée sur l’ordinateur local dans ProtectedStorage.ssma.  
  
    -   **Sécurisation des mots de passe**  
  
        -   Exécuter le `SSMAforAccessConsole.exe` avec le `-securepassword` et ajoutez le commutateur à la ligne de commande en passant le serveur de connexion ou fichier de script contenant le nœud de mot de passe dans la section de définition de serveur.  
  
        -   À l’invite de commandes, l’utilisateur est invité à entrer le mot de passe de base de données et confirmez-le.  
  
            Les ID de définition de serveur et ses mots de passe chiffrés correspondants sont stockés dans un fichier sur l’ordinateur local  
  
            Exemple 1 :
            
                Specify password
                
                C:\SSMA\SSMAforAccessConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx  
            
            Exemple 2 :
            
                C:\SSMA\SSMAforAccessConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
  
    -   **Suppression des mots de passe chiffrés**  
  
        Exécuter le `SSMAforAccessConsole.exe` avec la`-securepassword` et `-remove` passer à la ligne de commande en passant l’ID de serveur pour supprimer les mots de passe chiffrés à partir du fichier de stockage protégé présent sur l’ordinateur local.  
  
            C:\SSMA\SSMAforAccessConsole.EXE -securepassword -remove all
            C:\SSMA\SSMAforAccessConsole.EXE -securepassword -remove "source_1,target_1"  
  
    -   **Liste des ID de serveur dont les mots de passe sont chiffrés.**  
  
        Exécuter le SSMAforAccessConsole.exe avec la `-securepassword` et `-list` passer à la ligne de commande pour répertorier tous les ID de serveur dont les mots de passe ont été chiffrés.  
  
            C:\SSMA\SSMAforAccessConsole.EXE -securepassword -list  
  
    > [!NOTE]  
    > 1.  Le mot de passe en texte clair mentionné dans le fichier de connexion de serveur ou de script est prioritaire sur le mot de passe chiffré dans le fichier sécurisé.  
    > 2.  Lorsqu’il n’existe aucun mot de passe dans la section serveur de fichier de connexion de serveur ou le fichier de script, ou si elle n’a pas été sécurisée sur l’ordinateur local, la console vous invite à entrer le mot de passe.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Exporter ou importer des mots de passe chiffrés  
L’application de Console SSMA vous permet d’exporter des mots de passe de base de données chiffrées présentes dans un fichier sur l’ordinateur local à un fichier sécurisé et inversement. Il permet de rendre la machine de mots de passe chiffrés indépendants. La fonctionnalité d’exportation lit l’id de serveur et le mot de passe à partir de l’ordinateur local, stockage protégé et enregistre les informations dans un fichier chiffré. L’utilisateur est invité à entrer le mot de passe pour le fichier sécurisé. Assurez-vous que le mot de passe entré est la longueur de 8 caractères ou plus. Ce fichier sécurisé est portable sur des ordinateurs différents. Fonctionnalité d’importation lit les informations d’id et mot de passe de serveur à partir du fichier sécurisé. L’utilisateur est invité à entrer le mot de passe pour le fichier sécurisé et ajoute les informations sur le stockage local protégé.  


    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforAccessConsole.EXE -securepassword -export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE -p -e "AccessDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  


    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforAccessConsole.EXE -securepassword -import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE -p -i "AccessDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la Console SSMA (accès)](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
