---
title: Création de fichiers de Script (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ec23d188-b890-49b8-9a88-446df96269e4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: cddfa2e3fd5d1263bf4f9e5e0bb1fd4c6e8fe675
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63453414"
---
# <a name="creating-script-files-db2tosql"></a>Création de fichiers de Script (DB2ToSQL)
La première étape avant le lancement de l’application de console SSMA consiste à créer le fichier de script et, si nécessaire de créer le fichier de la valeur de la variable et le fichier de connexion de serveur.  
  
Le fichier de script peut être divisé en trois sections, reportages.., :  
  
1.  **config:** Permet à l’utilisateur définir les paramètres de configuration pour l’application de console.  
  
2.  **serveurs :** Permet à l’utilisateur définir des définitions de serveur de la source/cible. Cela peut également être dans un fichier de connexion de serveur distinct.  
  
3.  **commandes de script :** Permet à l’utilisateur d’exécuter des commandes de flux de travail SSMA.  
  
Chaque section est décrite en détail ci-dessous :  
  
## <a name="configuring-db2-console-settings"></a>Configuration des paramètres de la Console DB2  
Les configurations d’un script sont affichées dans le fichier de script de console.  
  
Si un des éléments sont spécifié dans le noeud configuration, elles sont définies comme par exemple, le paramètre global, ils s’appliquent pour toutes les commandes de script. Ces éléments de configuration peuvent également être définies au sein de chaque commande dans la section de la commande de script si l’utilisateur souhaite remplacer le paramètre global.  
  
Les options configurables par l’utilisateur sont les suivantes :  
  
1.  **Fournisseur de fenêtre de sortie :** Si l’attribut de messages supprimer est défini sur « true », la commande spécifique messages ne pas s’affichent sur la console. La description des attributs est donnée ci-dessous :  
  
    -   destination : Spécifie si la sortie doit obtenir imprimé à un fichier ou à stdout. Cela a la valeur false par défaut.  
  
    -   nom de fichier : Le chemin d’accès du fichier (facultatif).  
  
    -   supprimer-messages : Supprime les messages sur la console. Cela est « false » par défaut.  
  
    **Exemple :**  
  
    ```xml  
    <output-providers>  
  
      <output-window  
  
        suppress-messages="<true/false>"   (optional)  
  
        destination="<file/stdout>"        (optional)  
  
        file-name="<file-name>"            (optional)  
  
       />  
  
    </output-providers>  
    ```  
    *ou Gestionnaire de configuration*  
  
    ```xml  
    <...All commands...>  
  
      <output-window  
  
         suppress-messages="<true/false>"   (optional)  
  
         destination="<file/stdout>"        (optional)  
  
         file-name="<file-name>"            (optional)  
  
       />  
  
    </...All commands...>  
    ```  
  
2.  **Fournisseur de connexion de Migration de données :** Qui spécifie le serveur source/cible est à prendre en compte pour la migration de données.  Source-utilisation-last-used indique que le dernier serveur source utilisé est utilisé pour la migration de données. De même cible-utilisation-last-used indique que le dernier serveur cible utilisée est utilisé pour la migration de données. L’utilisateur peut également spécifier le serveur (source ou cible) en utilisant les attributs source ou cible-serveurs.  
  
    Seuls un ou l’autre attribut spécifié permet par exemple :  
  
    -   source-utilisation-last-used = « true » (valeur par défaut) ou serveur de source = « source_servername »  
  
    -   target-use-last-used="true" (default) or target-server="target_servername"  
  
    **Exemple :**  
  
    ```xml  
    <output-providers>  
  
      <data-migration-connection   source-use-last-used="true"  
  
                                   target-server="<target-server-unique-name>"/>  
  
    </output-providers>  
    ```  
    *ou Gestionnaire de configuration*  
  
    ```xml  
    <migrate-data>  
  
      <data-migration-connection   source-server="<source-server-unique-name>"  
  
                                   target-use-last-used="true"/>  
  
    </migrate-data>  
    ```  
  
3.  **Popup d’entrée utilisateur :** Cela permet la gestion des erreurs, lorsque les objets sont chargés à partir de la base de données. L’utilisateur fournit les modes d’entrée, et en cas d’erreur, la console se poursuit comme utilisateur spécifie.  
  
    Les modes sont les suivantes :  
  
    -   **Demandez-utilisateur -** invite l’utilisateur à continue('yes') ou d’erreur (« no »).  
  
    -   **erreur -** la console affiche une erreur et interrompt l’exécution.  
  
    -   **continuer-** la console se poursuit avec l’exécution.  
  
    Le mode par défaut est **erreur**.  
  
    **Exemple :**  
  
    ```xml  
    <output-providers>  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </output-providers>  
    ```  
    *ou Gestionnaire de configuration*  
  
    ```xml  
    <!-- Connect to target database -->  
  
    <connect-target-database server="<target-server-unique-name>">  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </connect-target-database>  
    ```  
  
4.  **Reconnectez le fournisseur :** Cela permet à l’utilisateur définir la paramètres dans le cas où la reconnexion des échecs de connexion. Cela peut être défini pour les serveurs source et cible.  
  
    Les modes de reconnexion sont :  
  
    -   reconnect-to-last-used-server: Si la connexion n’est pas active, il tente de se reconnecter au dernier serveur utilisé au maximum 5 fois.  
  
    -   générer une-erreur : Si la connexion n’est pas active, une erreur est générée.  
  
    Le mode par défaut est **générer une erreur**.  
  
    **Exemple :**  
  
    ```xml  
    <output-providers>  
  
      <reconnect-manager  on-source-reconnect="<reconnect-to-last-used-server/generate-an-error>"  
  
                          on-target-reconnect="<reconnect-to-last-used-server/generate-an-error>"/>  
  
    </output-providers>  
    ```  
    *ou Gestionnaire de configuration*  
  
    ```xml  
    <!--synchronization-->  
  
    <synchronize-target>  
  
      <reconnect-manager on-target-reconnect="reconnect-to-last-used-server"/>  
  
    </synchronize-target>  
    ```  
    *ou Gestionnaire de configuration*  
  
    ```xml  
    <!--data migration-->  
  
    <migrate-data server="<target-server-unique-name>">  
  
      <reconnect-manager  
  
        on-source-reconnect="reconnect-to-last-used-server"  
  
        on-target-reconnect="generate-an-error"/>  
  
    </migrate-data>  
    ```  
  
5.  **Convertisseur de remplacer le fournisseur :** Cela permet à l’utilisateur gérer les objets qui sont déjà présents sur la cible de la métabase. Les actions possibles sont les suivantes :  
  
    -   Erreur : La console affiche une erreur et interrompt l’exécution.  
  
    -   remplacer : Remplace les valeurs d’objet existantes. Cette action est effectuée par défaut.  
  
    -   Ignorer : La console ignore les objets qui existent déjà sur la base de données  
  
    -   utilisateur poser : Invite l’utilisateur pour l’entrée (« Oui » / « non »)  
  
    **Exemple :**  
  
    ```xml  
    <output-providers>  
  
      <object-overwrite action="<error/skip/overwrite/ask-user>"/>  
  
    </output-providers>  
    ```  
    *ou Gestionnaire de configuration*  
  
    ```xml  
    <convert-schema object-name="<object-name>">  
  
      <object-overwrite action="<error/skip/overwrite/ask-user>"/>  
  
    </convert-schema>  
    ```  
  
6.  **Fournisseur de configuration requise a échoué :** Cela permet à l’utilisateur gérer les éléments nécessaires au traitement d’une commande. Par défaut, le mode strict est 'false'. Si elle est définie sur « true », une exception est généré pour l’échec de la configuration requise.  
  
    **Exemple :**  
  
    ```xml  
    <output-providers>  
  
      <prerequisites strict-mode="<true/false>"/>  
  
    </output-providers>  
    ```  
  
7.  **Arrêter l’opération :** Pendant l’opération intermédiaire, si l’utilisateur veut arrêter l’opération, puis **« Ctrl + C »** raccourci clavier peut être utilisé. SSMA pour DB2 Console attendra la fin d’opération et termine l’exécution de la console.  
  
    Si l’utilisateur souhaite arrêter l’exécution immédiatement, puis, **« Ctrl + C »** raccourci clavier peut être enfoncée à nouveau pour un arrêt soudain de l’application de Console SSMA.  
  
8.  **Fournisseur de progression :** Indique la progression de chaque commande de console. Il est désactivé par défaut. Les attributs de rapport de progression comprennent :  
  
    -   inactif  
  
    -   chaque 1 %  
  
    -   chaque 2 %  
  
    -   chaque 5 %  
  
    -   chaque 10 %  
  
    -   chaque - 20 %  
  
    **Exemple :**  
  
    ```xml  
    <output-providers>  
  
      progress-reporting   enable="<true/false>"            (optional)  
  
                           report-messages="<true/false>"   (optional)  
  
                           report-progress="every-1%/every-2%/every-5%/every-10%/every-20%/off" (optional)/>  
  
    </output-providers>  
    ```  
    *ou Gestionnaire de configuration*  
  
    ```xml  
    <...All commands...>  
  
      <progress-reporting  
  
        enable="<true/false>"              (optional)  
  
        report-messages="<true/false>"     (optional)  
  
        report-progress="every-1%/every-2%/every-5%/every-10%/every-20%/off"     (optional)/>  
  
    </...All commands...>  
    ```  
  
9. **Détail de l’enregistreur d’événements :** Jeux de connecter un niveau de détail. Cela correspond à l’option de toutes les catégories dans l’interface utilisateur. Par défaut, le niveau de détail du journal est « erreur ».  
  
    Les options au niveau de l’enregistreur d’événements sont les suivantes :  
  
    -   Erreur irrécupérable : Seuls les messages d’erreur irrécupérable sont enregistrés.  
  
    -   Erreur : Seuls les messages d’erreur et d’erreur irrécupérable sont enregistrés.  
  
    -   Avertissement : Tous les niveaux à l’exception des messages de débogage et les informations sont enregistrées.  
  
    -   Info : Tous les niveaux à l’exception des messages de débogage sont enregistrés.  
  
    -   Débogage : Tous les niveaux de messages consignés.  
  
    > [!NOTE]  
    > Messages obligatoires sont enregistrés à n’importe quel niveau.  
  
    **Exemple :**  
  
    ```xml  
    <output-providers>  
  
      <log-verbosity level="fatal-error/error/warning/info/debug"/>  
  
    </output-providers>  
    ```  
    *ou Gestionnaire de configuration*  
  
    ```xml  
    <...All commands...>  
  
      <log-verbosity level="fatal-error/error/warning/info/debug"/>  
  
    </...All commands...>  
    ```  
  
10. **Remplacer le mot de passe chiffré :** Si « true », le mot de passe de texte en clair spécifiée dans la section de définition de serveur du fichier de connexion du serveur ou dans le fichier de script, substitutions de mot de passe chiffré stocké dans la mémoire protégée si existe. Si aucun mot de passe n’est spécifié en texte clair, l’utilisateur est invité à entrer le mot de passe.  
  
    Ici deux arriver :  
  
    1.  Si remplacer l’option est **false**, l’ordre de recherche sera protégé stockage -&gt;fichier de Script -&gt;fichier de connexion de serveur -&gt; inviter l’utilisateur.  
  
    2.  Si remplacer l’option est **true**, l’ordre de recherche sera fichier Script -&gt;fichier de connexion de serveur -&gt;inviter l’utilisateur.  
  
    **Exemple :**  
  
    ```xml  
    <output-providers>  
  
      <encrypted-password override="<true/false>"/>  
  
    </output-providers>  
    ```  
  
L’option non configurable est :  
  
-   **Nombre maximal des tentatives de reconnexion :** Lorsqu’une connexion établie expire ou s’arrête en raison d’une défaillance réseau, le serveur est nécessaire pour être reconnectées. Les tentatives de reconnexion sont autorisées à un maximum de **5** nouvelles tentatives après quoi, la console effectue automatiquement la reconnexion. La fonctionnalité de reconnexion automatique réduit vos efforts sur réexécuter le script.  
  
## <a name="server-connection-parameters"></a>Paramètres de connexion de serveur  
Paramètres de connexion de serveur peuvent être définis dans le fichier de script ou dans le fichier de connexion de serveur. Reportez-vous à la [création des fichiers de connexion de serveur &#40;OracleToSQL&#41; ](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md) section pour plus d’informations.  
  
## <a name="script-commands"></a>Commandes de script  
Le fichier de script contient une séquence de commandes de flux de travail de migration au format XML. L’application de console SSMA traite la migration dans l’ordre les commandes apparaissant dans le fichier de script.  
  
Par exemple, une migration de données standard d’une table spécifique dans une base de données DB2 suit la hiérarchie de : Schéma -&gt; Table.  
  
Lorsque toutes les commandes dans le fichier de script sont exécutées avec succès, l’application de console SSMA se termine et retourne le contrôle à l’utilisateur. Le contenu d’un fichier de script est plus ou moins statique avec des informations sur les variables contenues dans un [création de fichiers de valeur Variable &#40;OracleToSQL&#41; ](../../ssma/oracle/creating-variable-value-files-oracletosql.md) ou, dans une section distincte du fichier de script pour les valeurs des variables.  
  
**Exemple :**  
  
```xml  
<!--Sample of script file commands -->  
  
<ssma-script-file>  
  
  <script-commands>  
  
    <create-new-project project-folder="<project-folder>"  
  
                        project-name="<project-name>"  
  
                        overwrite-if-exists="<true/false>"/>  
  
    <connect-source-database server="<source-server-unique-name>"/>  
  
    <save-project/>  
  
    <close-project/>  
  
  </script-commands>  
  
</ssma-script-file>  
```  
Modèles consistant en des fichiers de script 3 (pour l’exécution des scénarios différents), fichier de la valeur de la variable et un fichier de connexion de serveur sont fournis dans le dossier d’exemples de Scripts de Console du répertoire de produit :  
  
-   AssessmentReportGenerationSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   VariableValueFileSample.xml  
  
-   ServersConnectionFileSample.xml  
  
Vous pouvez exécuter les modèles (fichiers) après avoir modifié les paramètres affichés dans celui-ci de pertinence.  
  
Vous trouverez la liste complète des commandes de script dans [l’exécution de la Console SSMA &#40;DB2ToSQL&#41;](../../ssma/db2/executing-the-ssma-console-db2tosql.md)  
  
## <a name="script-file-validation"></a>Validation de fichier de script  
L’utilisateur peut valider facilement son fichier de script par rapport au fichier de définition de schéma **'O2SSConsoleScriptSchema.xsd'** disponibles dans le dossier « Schémas ».  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de d’exploitation de la console est [création de fichiers de valeur Variable &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Création de fichiers de la valeur de la Variable &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
  
