---
title: Glossaire ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], glossary
- glossary [ODBC]
ms.assetid: e8227000-1944-42e5-a881-1f549e1ff9d1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33116adaf74ed2d3fc52fec460859a7672ce2d0a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057781"
---
# <a name="odbc-glossary"></a>Glossaire ODBC
## <a name="a"></a>A  
 **plan d’accès**  
 Un plan généré par le moteur de base de données pour exécuter une instruction SQL. Équivalent au code exécutable compilé à partir d’un langage de troisième génération, tel que C.  
  
 **Fonction d’agrégation**  
 Une fonction qui génère une valeur unique à partir d’un groupe de valeurs, souvent utilisé avec **GROUP BY** et **HAVING** clauses. Incluront des fonctions d’agrégation **AVG**, **nombre**, **MAX**, **MIN**, et **somme**. Également appelé *définir des fonctions*. *Voir aussi* fonction scalaire.  
  
 **ANSI**  
 American National Standards Institute. L’API ODBC est basé sur l’Interface de niveau d’appel ANSI.  
  
 **APD**  
 *Consultez* descripteur de paramètre d’application (APD).  
  
 **API**  
 Interface de programmation d’application. Un ensemble de routines qu’une application utilise pour demander et exécuter des services de niveau inférieur. L’API ODBC est composé des fonctions ODBC.  
  
 **application**  
 Un programme exécutable qui appelle des fonctions de l’API ODBC.  
  
 **descripteur de paramètre d’application (APD)**  
 Un descripteur qui décrit les paramètres dynamiques utilisés dans une instruction SQL avant toute conversion spécifiée par l’application.  
  
 **descripteur de ligne d’application (ARD)**  
 Un descripteur qui représente les métadonnées de colonne et les données dans les mémoires tampons de l’application, qui décrit une ligne de données suivant toute conversion de données spécifiée par l’application.  
  
 **ARD**  
 *Consultez* descripteur de ligne d’application (ARD).  
  
 **auto-commit mode**  
 Mode de validation de transaction dans laquelle les transactions sont validées immédiatement après leur exécution.  
  
## <a name="b"></a>B  
 **changement de comportement**  
 Une modification de certaines fonctionnalités à partir d’ODBC 3 *.x* comportement ODBC 2. *x* comportement, ou vice versa. Dû en modifiant l’attribut d’environnement SQL_ATTR_ODBC_VERSION.  
  
 **Objet binaire volumineux (BLOB)**  
 Toutes les données binaires sur un certain nombre d’octets, tels que 255. En général beaucoup plus de temps. Ce type de données est généralement envoyé au et récupérée à partir de la source de données dans les parties. Également appelé *données de type long*.  
  
 **binding**  
 Sous forme verbale, le fait d’associer une colonne dans un jeu de résultats ou un paramètre dans une instruction SQL avec une variable d’application. Comme un nom, l’association.  
  
 **décalage de la liaison**  
 Une valeur ajoutée pour les adresses de tampons de données et les adresses de mémoire tampon de longueur / d’indicateur pour tous les lié aux adresses de nouveau des données, produire colonne ou du paramètre.  
  
 **curseur de bloc**  
 Un curseur capable d’extraire plusieurs lignes de données à la fois.  
  
 **buffer**  
 Un morceau de mémoire de l’application utilisée pour passer des données entre l’application et le pilote. Mémoires tampons sont souvent inventées par paires : un *tampon de données* et un *tampon de longueur de données*.  
  
 **byte**  
 Huit bits ou un octet. *Voir aussi* octet.  
  
## <a name="c"></a>C  
 **Type de données C**  
 Le type de données d’une variable dans un programme C, dans ce cas, l’application.  
  
 **catalog**  
 L’ensemble des tables système dans une base de données qui décrivent la forme de la base de données. Également appelé un *schéma* ou *dictionnaire de données*.  
  
 **fonction de catalogue**  
 Une fonction ODBC utilisée pour récupérer les informations de catalogue de la base de données.  
  
 **INTERFACE CLI**  
 *Consultez* API.  
  
 **client/server**  
 Une stratégie d’accès de base de données dans lequel un ou plusieurs clients accéder aux données via un serveur. Les clients implémentent généralement l’interface utilisateur, tandis que les contrôles serveur de base de données access.  
  
 **column**  
 Le conteneur pour un élément d’information dans une ligne unique. Également appelé *champ*.  
  
 **commit**  
 Pour apporter les modifications dans une transaction permanente.  
  
 **concurrency**  
 La capacité de plusieurs transactions à accéder aux mêmes données en même temps.  
  
 **Niveau de conformité**  
 Un ensemble discret de fonctionnalités prises en charge par une pilote ou source de données. ODBC définit des niveaux de conformité d’API et les niveaux de conformité de SQL.  
  
 **connection**  
 Une instance particulière d’une source de données et de pilote.  
  
 **connexion de navigation**  
 Rechercher sur le réseau pour se connecter à des sources de données. Connexion de navigation peut impliquer plusieurs étapes. Par exemple, l’utilisateur peut parcourir tout d’abord le réseau pour les serveurs et puis parcourir un serveur particulier pour une base de données.  
  
 **handle de connexion**  
 Handle vers une structure de données qui contient des informations sur une connexion.  
  
 **Ligne actuelle**  
 La ligne actuellement vers lequel pointe le curseur. Opérations positionnées agissent sur la ligne actuelle.  
  
 **cursor**  
 Un élément logiciel qui retourne des lignes de données à l’application. Probablement nommé d’après le curseur clignotant sur un ordinateur Terminal Server ; comme ce curseur indique la position actuelle sur l’écran, un curseur sur un jeu de résultats indique la position actuelle dans le jeu de résultats.  
  
## <a name="d"></a>D  
 **mémoire tampon de données**  
 Une mémoire tampon utilisée pour passer des données. Souvent associées comportant des données mémoire tampon est un *tampon de longueur de données*.  
  
 **dictionnaire de données**  
 *Consultez* catalogue.  
  
 **mémoire tampon de longueur de données**  
 Une mémoire tampon utilisée pour transmettre la longueur de la valeur d’une correspondant *tampon de données*. Le tampon de longueur de données est également utilisé pour stocker des indicateurs, par exemple si la valeur de données est terminée.  
  
 **Source de données**  
 Les données que l’utilisateur veut accès et son système d’exploitation associé SGBD et la plateforme de réseau (le cas échéant).  
  
 **Type de données**  
 Le type d’un élément de données. ODBC définit des types de données C et SQL. *Voir aussi* indicateur de type.  
  
 **colonne de Data-at-execution**  
 Une colonne pour laquelle les données sont envoyées après **SQLSetPos** est appelée. Par conséquent, nommé, car les données sont envoyées au moment de l’exécution, plutôt que d’être placées dans un tampon de l’ensemble de lignes. Données de type long sont généralement envoyées dans les parties au moment de l’exécution.  
  
 **paramètre de Data-at-execution**  
 Un paramètre pour lequel les données sont envoyées après **SQLExecute** ou **SQLExecDirect** est appelée. Par conséquent, nommé, car les données sont envoyées lorsque l’instruction SQL est exécutée au lieu d’être placé dans une mémoire tampon de paramètre. Données de type long sont généralement envoyées dans les parties au moment de l’exécution.  
  
 **database**  
 Collection de données dans un SGBD discrète. Également un SGBD.  
  
 **Moteur de base de données**  
 Le logiciel dans un SGBD qui analyse et exécute des instructions SQL et accède aux données physiques.  
  
 **DBMS**  
 Système de gestion de base de données. Couche logicielle entre la base de données physique et l'utilisateur. Le SGBD (système de gestion de base de données) gère tous les accès à la base de données.  
  
 **Pilote de SGBD**  
 Un pilote qui accède aux données physiques via un moteur de base de données autonome.  
  
 **DDL**  
 Langage de définition de données. Instructions SQL qui définissent, par opposition à manipuler des données. Par exemple, **CREATE TABLE**, **CREATE INDEX**, **GRANT**, et **RÉVOQUER**.  
  
 **identificateur délimité**  
 Un identificateur qui est placé entre guillemets identificateur afin qu’il peut contenir des caractères spéciaux ou à des mots clés (également appelé un identificateur entre guillemets).  
  
 **descriptor**  
 Une structure de données qui conserve des informations sur les données de la colonne ou de paramètres dynamiques. La représentation physique du descripteur n’est pas définie ; applications obtenir un accès direct à un descripteur uniquement en manipulant des ses champs en appelant les fonctions ODBC avec le handle du descripteur.  
  
 **base de données de bureau**  
 Un SGBD est conçu pour s’exécuter sur un ordinateur personnel. En règle générale, ces SGBD ne fournit pas d’un moteur de base de données autonome et doit être accessible via un pilote basé sur fichier. Les moteurs de ces pilotes ont réduit généralement la prise en charge pour SQL et les transactions. Par exemple, dBASE, Paradox, Btrieve ou Microsoft® FoxPro.  
  
 **diagnostic**  
 Un enregistrement contenant les informations de diagnostic sur la dernière fonction appelée et utilisé un handle spécifique. Les enregistrements de diagnostic sont associés de l’environnement, connexion, l’instruction et handles de descripteur.  
  
 **DML**  
 Langage de Manipulation de données. Instructions SQL qui manipulent, par opposition à définir des données. Par exemple, **insérer**, **mise à jour**, **supprimer**, et **sélectionnez**.  
  
 **driver**  
 Une bibliothèque de routine qui expose les fonctions de l’API ODBC. Les pilotes sont spécifiques à un système SGBD unique.  
  
 **Gestionnaire de pilotes**  
 Une bibliothèque de routine qui gère l’accès aux pilotes pour l’application. Le Gestionnaire de pilotes charge et décharge (ou se connecte à et se déconnecte) pilotes et passe des appels aux fonctions ODBC pour le pilote correct.  
  
 **DLL d’installation du pilote**  
 Une DLL qui contient les fonctions d’installation et de configuration spécifiques au pilote.  
  
 **curseur dynamique**  
 Un curseur de défilement capable de détecter les lignes mises à jour, supprimées ou inséré dans le jeu de résultats.  
  
 **SQL dynamique**  
 Un type d’embedded SQL dans SQL instructions sont créées et compilées au moment de l’exécution. *Voir aussi* SQL statique.  
  
## <a name="e"></a>E  
 **Embedded SQL**  
 Les instructions SQL qui sont incluses directement dans un programme écrit dans un autre langage, tels que les anciennes applications COBOL ou C. ODBC n’utilise pas embedded SQL. *Voir aussi* SQL statique *et* SQL dynamique.  
  
 **environment**  
 Un contexte global d’accès aux données ; associé à l’environnement est toute information qui est globale par nature, telles qu’une liste de toutes les connexions dans cet environnement.  
  
 **handle d’environnement**  
 Handle vers une structure de données qui contient des informations sur l’environnement.  
  
 **clause d’échappement**  
 Une clause dans une instruction SQL.  
  
 **execute**  
 Pour exécuter une instruction SQL.  
  
## <a name="f"></a>F  
 **curseur FAT**  
 *Consultez* curseur de bloc.  
  
 **fetch**  
 Pour récupérer une ou plusieurs lignes à partir d’un jeu de résultats.  
  
 **field**  
 *Consultez* colonne.  
  
 **pilote basé sur fichier**  
 Un pilote qui accède directement aux données physiques. Dans ce cas, le pilote contient un moteur de base de données et sert de pilote et de source de données.  
  
 **source de données de fichier**  
 Une source de données pour quelle connexion les informations sont stockées dans un fichier .dsn.  
  
 **Clé étrangère**  
 Une ou plusieurs colonnes dans une table qui correspondent à la clé primaire dans une autre table.  
  
 **curseur avant uniquement**  
 Un curseur peut uniquement mettre en œuvre via le jeu de résultats et généralement n'extrait qu’une seule ligne à la fois. La plupart des bases de données relationnelles prennent en charge uniquement les curseurs avant uniquement.  
  
## <a name="h"></a>H  
 **handle**  
 Une valeur qui identifie de façon unique un élément tel qu’une structure de fichiers ou de données. Handles sont uniquement explicites pour le logiciel qui crée et les utilise, mais est transmis à d’autres logiciels pour identifier les choses. ODBC définit des handles pour les environnements, les connexions, les instructions et les descripteurs.  
  
## <a name="i"></a>I  
 **descripteur de paramètre d’implémentation (IPD)**  
 Un descripteur qui décrit les paramètres dynamiques utilisés dans une instruction SQL après toute conversion spécifiée par l’application.  
  
 **descripteur de ligne d’implémentation (IRD)**  
 Un descripteur qui décrit une ligne de données avant toute conversion spécifiée par l’application.  
  
 **DLL d’installation**  
 Une DLL qui installe des composants ODBC et configure les sources de données.  
  
 **Integrity Enhancement Facility**  
 Un sous-ensemble de SQL conçue pour maintenir l’intégrité d’une base de données.  
  
 **niveau de conformité d’interface**  
 Le niveau de l’interface ODBC 3.7 pris en charge par un pilote ; peut être Core, niveau 1 ou niveau 2.  
  
 **interoperability**  
 La capacité d’une application à utiliser le même code lors de l’accès aux données dans différents SGBD.  
  
 **IPD**  
 *Consultez* descripteur de paramètre d’implémentation (IPD).  
  
 **IRD**  
 *Consultez* descripteur de ligne d’implémentation (IRD).  
  
 **ISO/IEC**  
 Commission électrotechnique d’organisation/International normes internationales. L’API ODBC est basé sur l’Interface de niveau d’appel de norme ISO/IEC.  
  
## <a name="j"></a>J  
 **join**  
 Une opération dans une base de données relationnelle qui lie les lignes de deux ou plusieurs tables en faisant correspondre les valeurs dans les colonnes spécifiées.  
  
## <a name="k"></a>K  
 **key**  
 Une ou plusieurs colonnes dont les valeurs identifient une ligne. *Voir aussi* clé étrangère *et* clé primaire.  
  
 **keyset**  
 Un jeu de clés utilisé par un curseur mixte ou commandé par keyset pour récupérer à nouveau les lignes.  
  
 **curseur keyset**  
 Un curseur de défilement qui détecte des lignes mises à jour et supprimées à l’aide d’un jeu de clés.  
  
## <a name="l"></a>L  
 **literal**  
 Représentation sous forme de caractère de la valeur réelle des données dans une instruction SQL.  
  
 **locking**  
 Le processus par lequel un SGBD limite l’accès à une ligne dans un environnement multi-utilisateur. Le SGBD généralement définit un bit sur une ligne ou de la page physique qui contient une ligne qui indique la ligne ou page est verrouillée.  
  
 **données de type long**  
 Toutes les données binaires ou caractères dépassant une certaine longueur, telles que 255 octets ou caractères. En général beaucoup plus de temps. Ce type de données est généralement envoyé au et récupérée à partir de la source de données dans les parties. Également appelé *BLOB*s ou *CLOB*s.  
  
## <a name="m"></a>M  
 **source de données machine**  
 Une source de données pour la connexion sont stockées sur le système (par exemple, le Registre).  
  
 **Mode de validation manuelle**  
 Un mode de validation de transaction dans laquelle des transactions doivent être validées explicitement en appelant **SQLTransact**.  
  
 **metadata**  
 Données qui décrivent un paramètre dans une instruction SQL ou une colonne dans un jeu de résultats. Par exemple, le type de données, longueur d’octet et de précision d’un paramètre.  
  
 **pilotes à plusieurs niveaux**  
 *Consultez* pilote de SGBD.  
  
## <a name="n"></a>N  
 **Valeur NULL**  
 N’avoir aucune valeur explicitement attribué. En particulier, une valeur NULL est différente de zéro ou une valeur vide.  
  
## <a name="o"></a>O  
 **octet**  
 Huit bits ou un seul octet. *Voir aussi* octets.  
  
 **longueur en octets**  
 La longueur en octets d’une mémoire tampon ou les données qu’il contient.  
  
 **ODBC**  
 Open Database Connectivity. Spécification d’une API qui définit un ensemble standard de routines avec laquelle une application peut accéder aux données dans une source de données.  
  
 **Administrateur ODBC**  
 Un programme exécutable qui appelle le programme d’installation DLL pour configurer des sources de données.  
  
 Ouvrir le groupe  
 Une société qui publie des normes. En particulier, il publie des normes de groupe d’accès SQL (trous).  
  
 **accès concurrentiel optimiste**  
 Une stratégie pour augmenter la concurrence dans laquelle les lignes ne sont pas verrouillées. Au lieu de cela, avant d’être mis à jour ou supprimés, un curseur vérifie si elles ont été modifiés depuis leur dernière lecture. Dans ce cas, la mise à jour ou suppression échoue. *Voir aussi* d’accès concurrentiel pessimiste.  
  
 **jointure externe**  
 Jointure dans les lignes non correspondantes et correspondants sont retournés. Les valeurs de toutes les colonnes de la table sans correspondance dans les lignes non correspondantes sont définies sur NULL.  
  
 **Propriétaire**  
 Le propriétaire d’une table.  
  
## <a name="p"></a>P  
 **parameter**  
 Une variable dans une instruction SQL, marquée avec un marqueur de paramètre ou d’un point d’interrogation ( ?). Paramètres sont liés aux variables d’application et leurs valeurs récupérées lors de l’instruction est exécutée.  
  
 **descripteur de paramètre**  
 Un descripteur qui décrit les paramètres d’exécution utilisés dans une instruction SQL, soit avant toute conversion spécifié par l’application (APD ou un descripteur de paramètre d’application) ou après toute conversion spécifié par l’application (une implémentation descripteur de paramètre, ou IPD).  
  
 **tableau d’opération de paramètres**  
 Un tableau contenant les valeurs à une application peut définir pour indiquer que le paramètre correspondant doit être ignoré dans un **SQLExecDirect** ou **SQLExecute** opération.  
  
 **tableau de paramètres état**  
 Tableau qui contient l’état d’un paramètre après un appel à **SQLExecDirect** ou **SQLExecute**.  
  
 **accès concurrentiel pessimiste**  
 Une stratégie pour l’implémentation de sérialisation, dans lequel les lignes sont verrouillées afin que les autres transactions ne peuvent pas les modifier. *Voir aussi* d’accès concurrentiel optimiste *et* la sérialisation.  
  
 **mise à jour positionnée**  
 Toute opération qui agit sur la ligne actuelle. Par exemple, positionné mise à jour et supprimer des instructions, **SQLGetData**, et **SQLSetPos**.  
  
 **instruction de mise à jour positionnée**  
 Une instruction SQL utilisée pour mettre à jour les valeurs dans la ligne actuelle.  
  
 **instruction positionnée delete**  
 Une instruction SQL utilisée pour supprimer la ligne actuelle.  
  
 **prepare**  
 Pour compiler une instruction SQL. Un plan d’accès est créé en préparant une instruction SQL.  
  
 **Clé primaire**  
 Une ou plusieurs colonnes qui identifie de façon unique une ligne dans une table.  
  
 **procedure**  
 Un groupe d’un ou plusieurs précompilé d’instructions SQL qui sont stockées sous la forme d’un objet nommé dans une base de données.  
  
 **colonne de procédure**  
 Un argument dans un appel de procédure, la valeur retournée par une procédure ou une colonne dans un jeu de résultats créé par une procédure.  
  
## <a name="q"></a>Q  
 **qualifier**  
 Une base de données qui contient une ou plusieurs tables.  
  
 **query**  
 Une instruction SQL. Parfois utilisé pour désigner un **sélectionnez** instruction.  
  
 **identificateur entre guillemets**  
 Un identificateur qui est placé entre guillemets identificateur afin qu’il peut contenir des caractères spéciaux ou à des mots clés (également appelés dans SQL-92 comme un identificateur délimité).  
  
## <a name="r"></a>R  
 **radix**  
 La base d’un système de nombre. Généralement de 2 ou 10.  
  
 **record**  
 *Consultez* ligne.  
  
 **jeu de résultats**  
 L’ensemble de lignes créé en exécutant un **sélectionnez** instruction.  
  
 **Code de retour**  
 La valeur retournée par une fonction ODBC.  
  
 **restaurer**  
 Pour retourner les valeurs modifiées par une transaction à leur état d’origine.  
  
 **row**  
 Un ensemble de colonnes associées qui décrivent une entité spécifique. Également appelé un *enregistrement*.  
  
 **descripteur de ligne**  
 Un descripteur qui décrit les colonnes d’un jeu de résultats, avant toute conversion spécifié par l’application (un descripteur de ligne d’implémentation ou IRD) ou après toute conversion spécifié par l’application (un descripteur de ligne d’application ou ARD).  
  
 **tableau d’opération de ligne**  
 Un tableau contenant les valeurs à une application peut définir pour indiquer que la ligne correspondante doit être ignorée dans un **SQLSetPos** opération.  
  
 **tableau d’état de ligne**  
 Tableau qui contient l’état d’une ligne après un appel à **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos**.  
  
 **rowset**  
 L’ensemble de lignes retournées dans une seule extraction par un curseur de bloc.  
  
 **mémoires tampons d’ensemble de lignes**  
 Les mémoires tampons liées aux colonnes d’un jeu de résultats et dans laquelle les données pour un ensemble de lignes sont retournées.  
  
## <a name="s"></a>S  
 **SAG**  
 *Consultez* groupe d’accès SQL (trous).  
  
 **Fonction scalaire**  
 Une fonction qui génère une valeur unique à partir d’une valeur unique. Par exemple, une fonction qui modifie la casse des données de caractères.  
  
 **schema**  
 *Consultez* catalogue.  
  
 **curseur de défilement**  
 Un curseur que vous pouvez vous déplacer vers l’avant ou vers l’arrière dans le jeu de résultats.  
  
 **serializability**  
 Indique si deux transactions s’exécutant simultanément un résultat qui est identique à l’exécution de série (ou séquentielle) de ces transactions. Les transactions sont tenues de garantir l’intégrité de base de données.  
  
 **base de données de serveur**  
 Un SGBD destiné à être exécuté dans un environnement client/serveur. Ces SGBD fournit un moteur de base de données autonome qui fournit la prise en charge enrichie pour SQL et les transactions. Ils sont accessibles via des pilotes basés sur SGBD. Par exemple, Oracle, Informix, DB/2 ou Microsoft® SQL Server.  
  
 **fonction Set**  
 *Consultez* fonction d’agrégation.  
  
 **DLL d’installation**  
 *Consultez* DLL d’installation du pilote *et* DLL d’installation du traducteur.  
  
 **pilote de niveau unique**  
 *Consultez* pilote basé sur le fichier.  
  
 **SQL**  
 Structured Query Language. Un langage utilisé par les bases de données relationnelles pour interroger, mettre à jour et gérer les données.  
  
 **Groupe d’accès SQL (trous)**  
 Un consortium d’entreprises concernés avec SQL SGBD. Interface de niveau d’appel de The Open Group est basée sur le travail effectué à l’origine par le groupe d’accès SQL.  
  
 **Niveau de conformité SQL**  
 Niveau de la grammaire SQL-92 pris en charge par un pilote ; peut être entrée, FIPS transitoires, intermédiaire ou intégral.  
  
 **Type de données SQL**  
 Le type de données d’une colonne ou un paramètre tel qu’il est stocké dans la source de données.  
  
 **SQLSTATE**  
 Une valeur de cinq caractères qui indique une erreur particulière.  
  
 **Instruction SQL**  
 Une phrase complète dans SQL qui commence par un mot clé et complètement décrit une action à entreprendre. Par exemple, sélectionnez * à partir de commandes. Il ne faut pas confondre les instructions SQL avec des instructions.  
  
 **state**  
 Une condition bien définie d’un élément. Par exemple, une connexion a sept États, y compris les données non allouées, allouées, connectées et besoin d’écrire. Certaines opérations peuvent être effectuées uniquement lorsqu’un élément est dans un état particulier. Par exemple, une connexion peut être libérée uniquement lorsqu’il est dans un état alloué et non, par exemple, lorsqu’il est dans un état connecté.  
  
 **transition d’état**  
 Le déplacement d’un élément d’un état à un autre. ODBC définit des transitions d’état rigoureux pour environnements, les connexions et les instructions.  
  
 **instruction**  
 Un conteneur pour toutes les informations relatives à une instruction SQL. Il ne faut pas confondre les instructions avec des instructions SQL.  
  
 **descripteur d’instruction**  
 Handle vers une structure de données qui contient des informations sur une instruction.  
  
 **curseur statique**  
 Un curseur de défilement qui ne peut pas détecter les mises à jour, supprime ou insère dans le jeu de résultats. Généralement implémenté en effectuant une copie du jeu de résultats.  
  
 **SQL statique**  
 Un type d’embedded SQL dans SQL instructions sont codées en dur et de compilation lorsque le reste du programme est compilé. *Voir aussi* SQL dynamique.  
  
 **procédure stockée**  
 *Consultez* procédure.  
  
## <a name="t"></a>T  
 **table**  
 Une collection de lignes.  
  
 **thunking**  
 La conversion de 16 bits résout les adresses 32 bits, ou inversement, lorsque les applications 16 bits sont utilisées avec les pilotes ODBC 32 bits.  
  
 **transaction**  
 Une unité atomique de travail. Le travail dans une transaction doit être effectué dans son ensemble ; Si une partie de la transaction échoue, la transaction entière échoue.  
  
 **Isolation des transactions**  
 Action de l’isolation des transactions entre les effets de toutes les autres transactions.  
  
 **Niveau d’isolation de transaction**  
 Une mesure de la manière dont une transaction est isolée. Il existe cinq niveaux d’isolation de transaction : Lecture non validée, lecture validée, lecture renouvelée, sérialisable et le contrôle de version.  
  
 **DLL de conversion**  
 Une DLL utilisé pour convertir des données à partir d’un jeu de caractères à un autre.  
  
 **DLL d’installation du traducteur**  
 Une DLL qui contient les fonctions d’installation et de configuration spécifiques au traducteur.  
  
 **two-phase commit**  
 Le processus de validation d’une transaction distribuée en deux phases. Dans la première phase, le processeur de transaction vérifie que toutes les parties de la transaction peuvent être validés. Dans la deuxième phase, toutes les parties de la transaction sont validées. Si n’importe quelle partie de la transaction indique dans la première phase, qu’il ne peut pas être validé, la deuxième phase n’a pas lieu. ODBC ne prend pas en charge les validations en deux phases.  
  
 **Indicateur de type**  
 Valeur entière passée à ou retournée à partir d’une fonction ODBC pour indiquer le type de données d’une variable d’application, un paramètre ou une colonne. ODBC définit des indicateurs de type pour les types de données C et SQL.  
  
## <a name="v"></a>V  
 **Vue**  
 Une autre façon de consulter les données dans une ou plusieurs tables. Une vue est généralement créée comme un sous-ensemble des colonnes à partir d’une ou plusieurs tables. Dans ODBC, les vues sont généralement équivalentes aux tables.
