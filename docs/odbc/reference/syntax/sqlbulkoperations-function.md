---
title: SQLBulkOperations, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBulkOperations
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBulkOperations
helpviewer_keywords:
- SQLBulkOperations function [ODBC]
ms.assetid: 7029d0da-b0f2-44e6-9114-50bd96f47196
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14e51f1d04012e22c198b7ed5f70d9b508933c5d
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538030"
---
# <a name="sqlbulkoperations-function"></a>SQLBulkOperations, fonction
**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ODBC  
  
 **Résumé**  
 **SQLBulkOperations** effectue les insertions en bloc et signet de bulk operations, notamment la mise à jour, supprimer et l’extraction par signet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLBulkOperations(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Operation);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
 *Opération*  
 [Entrée] Opération à effectuer :  
  
 SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK  
  
 Pour plus d’informations, consultez « Commentaires ».  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLBulkOperations** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLBulkOperations** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes . Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
 Pour toutes ces SQLSTATEs qui peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_ERROR (sauf 01xxx SQLSTATE) SQL_SUCCESS_WITH_INFO est retourné si une erreur se produit sur un ou plus, mais pas toutes, les lignes d’une opération de plusieurs ligne, SQL_ERROR est retournée si une erreur se produit sur un opération de ligne unique.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Chaîne de données tronquée à droite|Le *opération* argument a été SQL_FETCH_BY_BOOKMARK, et données de chaîne ou binaire retournées pour une ou plusieurs colonnes avec un type de données SQL_C_CHAR ou SQL_C_BINARY a entraîné la troncation des caractères non vides ou non NULL des données binaires.|  
|01S01|Erreur de ligne|Le *opération* argument a été SQL_ADD et une erreur s’est produite dans une ou plusieurs lignes lors de l’exécution de l’opération, mais au moins une ligne a été correctement ajoutée. (La fonction retourne SQL_SUCCESS_WITH_INFO.)<br /><br /> (Cette erreur est générée uniquement lorsqu’une application fonctionne avec un ODBC 2. *x* pilote.)|  
|01S07|Troncation fractionnelle|Le *opération* argument était SQL_FETCH_BY_BOOKMARK, le type de données de la mémoire tampon d’application n’était pas SQL_C_CHAR ou SQL_C_BINARY, et les données retournées dans les mémoires tampons d’application pour une ou plusieurs colonnes ont été tronquées. (Pour les types de données numériques C, la partie fractionnaire du nombre ont été tronquée. Pour le moment, timestamp et les types de données d’intervalle C qui contiennent un composant au moment, la partie fractionnaire du temps a été tronquée.)<br /><br /> (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation de l’attribut de type de données restreint|Le *opération* SQL_FETCH_BY_BOOKMARK a été l’argument et la valeur de données d’une colonne dans le jeu de résultats n’a pas pu être convertie au type de données spécifié par le *TargetType* argument dans l’appel à **SQLBindCol**.<br /><br /> Le *opération* argument était SQL_UPDATE_BY_BOOKMARK ou SQL_ADD, et la valeur de données dans les mémoires tampons d’application n’a pas pu être convertie au type de données d’une colonne dans le jeu de résultats.|  
|07009|Index de descripteur non valide|L’argument *opération* a été SQL_ADD, et une colonne a été liée avec un numéro de colonne supérieur au nombre de colonnes dans le jeu de résultats.|  
|21S02|Degré de la table dérivée ne correspond pas à la liste des colonnes|L’argument *opération* a été SQL_UPDATE_BY_BOOKMARK ; et aucune colonne ont été être mise à jour, car toutes les colonnes ont été soit indépendant ou en lecture seule, ou la valeur dans la mémoire tampon de longueur / d’indicateur lié était SQL_COLUMN_IGNORE.|  
|22001|Chaîne de données tronquée à droite|L’attribution d’un caractère ou d’une valeur binaire à une colonne dans le jeu de résultats a entraîné la troncation de non vide (pour les caractères) ou de caractères non-null (pour les binaires) ou d’octets.|  
|22003|Valeur numérique hors limites|Le *opération* argument était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK, et l’attribution d’une valeur numérique à une colonne dans le jeu de résultats a provoqué la partie entière (par opposition à fractionnaire) du nombre à tronquer.<br /><br /> L’argument *opération* a été SQL_FETCH_BY_BOOKMARK et retourner la valeur numérique pour un ou plusieurs colonnes dépendantes entraîneraient une perte de chiffres significatifs.|  
|22007|Format datetime non valide|Le *opération* argument était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK, et l’attribution d’une valeur de date ou timestamp à une colonne dans le jeu de résultats a provoqué l’année, mois ou champ jour hors plage.<br /><br /> L’argument *opération* a été SQL_FETCH_BY_BOOKMARK et retourner la valeur de date ou timestamp pour une ou plusieurs colonnes dépendantes aurait entraîné l’année, mois ou champ jour hors plage.|  
|22008|Dépassement du champ date/heure|Le *opération* argument a été SQL_ADD ou SQL_UPDATE_BY_BOOKMARK, et les performances des calculs arithmétiques sur les données envoyées à une colonne du jeu de résultats de la date/heure a entraîné dans un champ de date/heure (année, mois, jour, heure, minute ou seconde champ) du résultat ne relevant pas de la plage de valeurs autorisée pour le champ ou est non valide en fonction des règles de naturelle du calendrier grégorien de dates/heures.<br /><br /> Le *opération* argument a été SQL_FETCH_BY_BOOKMARK, et les performances des calculs arithmétiques sur les données récupérées à partir de l’ensemble de résultats de la date/heure a entraîné dans un champ de date/heure (l’année, mois, jour, heure, minute ou second champ) de la résultat ne relevant pas de la plage de valeurs autorisée pour le champ ou n’est pas valide en fonction de règles naturelle du calendrier grégorien de dates/heures.|  
|22015|Dépassement du champ Intervalle|Le *opération* argument était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK, et l’assignation d’une valeur numérique exacte ou le type d’intervalle C à un type de données SQL de l’intervalle a entraîné une perte de chiffres significatifs.<br /><br /> Le *opération* argument était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK ; lorsque vous attribuez à un intervalle de type SQL, il n’était aucune représentation de la valeur du type C dans l’intervalle de type SQL.<br /><br /> Le *opération* argument a été SQL_FETCH_BY_BOOKMARK et affectation d’une valeur numérique exacte ou d’intervalle de type SQL à un type d’intervalle C a provoqué une perte de chiffres significatifs dans le champ Début.<br /><br /> Le *opération* argument était SQL_FETCH_BY_BOOKMARK ; lorsque vous attribuez à un type d’intervalle C, il n’a aucune représentation de la valeur du type SQL dans le type d’intervalle C.|  
|22018|Valeur de caractère non valide pour la spécification de la casse|Le *opération* argument était SQL_FETCH_BY_BOOKMARK ; le type C était une valeur numérique exact ou approximatif, une valeur datetime ou un type de données d’intervalle ; le type SQL de la colonne a un type de données caractère ; et la valeur dans la colonne n’était pas valide littéral de type C dépendant.<br /><br /> L’argument *opération* a été SQL_ADD ou SQL_UPDATE_BY_BOOKMARK ; le type SQL était une valeur numérique exact ou approximatif, une valeur datetime ou un type de données d’intervalle ; le type C a été SQL_C_CHAR ; et la valeur dans la colonne n’est pas un littéral valid de la type SQL dépendant.|  
|23000|Violation de contrainte d’intégrité|Le *opération* argument était SQL_ADD, SQL_DELETE_BY_BOOKMARK ou SQL_UPDATE_BY_BOOKMARK, et une contrainte d’intégrité a été violée.<br /><br /> Le *opération* argument était SQL_ADD, et une colonne qui n’était pas liée est définie comme valeur NOT NULL et aucune valeur par défaut.<br /><br /> Le *opération* SQL_ADD, la longueur spécifiée dans la limite a été l’argument *StrLen_or_IndPtr* mémoire tampon a été SQL_COLUMN_IGNORE, et la colonne n’avait pas de valeur par défaut.|  
|24000|État de curseur non valide|Le *au paramètre StatementHandle* était dans un état exécuté, mais aucun jeu de résultats a été associé le *au paramètre StatementHandle*.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’un blocage de ressource avec une autre transaction.|  
|40003|Saisie semi-automatique des instructions inconnue|Échec de la connexion associée lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|42000|Syntaxe ou violation d’accès|Le pilote n’a pas pu verrouiller la ligne en fonction des besoins pour effectuer l’opération demandée dans le *opération* argument.|  
|44000|Violation de WITH CHECK OPTION|Le *opération* argument était SQL_ADD ou SQL_UPDATE_BY_BOOKMARK et l’insertion ou mise à jour a été effectuée sur une table affichée (ou une table dérivée à partir de la table affichée) qui a été créé en spécifiant **WITH CHECK OPTION**, de sorte qu’une ou plusieurs lignes affectées par l’insertion ou mise à jour ne pourra plus être présent dans la table affichée.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*. La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*. La fonction a été appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* d’un thread différent dans un application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLBulkOperations** fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.<br /><br /> (DM) spécifié *au paramètre StatementHandle* n’était pas dans un état d’exécution. La fonction a été appelée sans préalablement appeler **SQLExecDirect**, **SQLExecute**, ou une fonction de catalogue.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLSetPos** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) le pilote a été un ODBC 2. *x* pilote, et **SQLBulkOperations** a été appelé pour un *au paramètre StatementHandle* avant **SQLFetchScroll** ou **SQLFetch**  a été appelée.<br /><br /> (DM) **SQLBulkOperations** a été appelée après **SQLExtendedFetch** a été appelé sur le *au paramètre StatementHandle*.|  
|HY011|Attribut ne peut pas être défini maintenant|(DM) le pilote a été un ODBC 2. *x* pilote et l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR a été défini entre les appels à **SQLFetch** ou **SQLFetchScroll** et **SQLBulkOperations** .|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|Le *opération* argument a été SQL_ADD ou SQL_UPDATE_BY_BOOKMARK ; une valeur de données n’était pas un pointeur null ; le type de données C a été SQL_C_BINARY ou SQL_C_CHAR ; et la valeur de longueur de colonne était inférieure à 0, mais pas égale à SQL_DATA_AT_EXEC , SQL_COLUMN_IGNORE, SQL_NTS ou SQL_NULL_DATA, ou inférieure ou égale à SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> La valeur dans une mémoire tampon de longueur / d’indicateur était SQL_DATA_AT_EXEC ; le type SQL a été SQL_LONGVARCHAR, SQL_LONGVARBINARY ou un type de données spécifiques à la source de données de type long ; et le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** a été « Y ».<br /><br /> Le *opération* argument a été SQL_ADD, l’attribut d’instruction SQL_ATTR_USE_BOOKMARK a été défini sur SQL_UB_VARIABLE, et la colonne 0 a été liée à une mémoire tampon dont la longueur n’était pas égale à la longueur maximale pour le signet pour ce jeu de résultats. (Cette longueur est disponible dans le champ SQL_DESC_OCTET_LENGTH de l’IRD et peut être obtenue en appelant **SQLDescribeCol**, **SQLColAttribute**, ou **SQLGetDescField**.)|  
|HY092|Identificateur d’attribut non valide|(DM) la valeur spécifiée pour le *opération* argument n’est pas valide.<br /><br /> Le *opération* argument était SQL_ADD, SQL_UPDATE_BY_BOOKMARK ou SQL_DELETE_BY_BOOKMARK, et l’attribut d’instruction SQL_ATTR_CONCURRENCY a été paramétré à SQL_CONCUR_READ_ONLY.<br /><br /> Le *opération* argument était SQL_DELETE_BY_BOOKMARK, SQL_FETCH_BY_BOOKMARK ou SQL_UPDATE_BY_BOOKMARK et la colonne de signet n’était pas liée ou l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS a été SQL_UB_OFF.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|La pilote ou source de données ne prend pas en charge l’opération demandée dans le *opération* argument.|  
|HYT00|Délai d'expiration dépassé|Le délai d’expiration de requête a expiré avant que la source de données a retourné le jeu de résultats. Le délai d’expiration est défini via **SQLSetStmtAttr** avec un *attribut* argument de SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
  
> [!CAUTION]  
>  Pour plus d’informations sur les États de l’instruction qui **SQLBulkOperations** peut être appelée et ce qu’il doit faire pour assurer la compatibilité avec ODBC 2. *x* applications, consultez le [curseurs de bloc, curseurs avec défilement et compatibilité descendante](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) section dans l’annexe G: Instructions de pilote pour la compatibilité descendante.  
  
 Une application utilise **SQLBulkOperations** pour effectuer les opérations suivantes sur la table de base ou la vue qui correspond à la requête actuelle :  
  
-   Ajouter de nouvelles lignes.  
  
-   Mettre à jour un ensemble de lignes dans lequel chaque ligne est identifiée par un signet.  
  
-   Supprimer un ensemble de lignes dans lequel chaque ligne est identifiée par un signet.  
  
-   Extraire un ensemble de lignes dans lequel chaque ligne est identifiée par un signet.  
  
 Après un appel à **SQLBulkOperations**, la position du curseur de bloc n’est pas défini. L’application doit appeler **SQLFetchScroll** pour définir la position du curseur. Une application doit appeler **SQLFetchScroll** uniquement avec un *FetchOrientation* argument de SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE ou SQL_FETCH_BOOKMARK. La position du curseur n’est pas définie si l’application appelle **SQLFetch** ou **SQLFetchScroll** avec un *FetchOrientation* argument de SQL_FETCH_PRIOR, SQL_FETCH_NEXT, ou SQL_FETCH_RELATIVE.  
  
 Une colonne peut être ignorée dans les opérations en bloc effectuées par un appel à **SQLBulkOperations** en définissant la mémoire tampon de longueur / d’indicateur de colonne spécifiée dans l’appel à **SQLBindCol**, à SQL_COLUMN_IGNORE.  
  
 Il n’est pas nécessaire pour l’application pour définir l’attribut d’instruction SQL_ATTR_ROW_OPERATION_PTR lorsqu’il appelle **SQLBulkOperations** , car les lignes ne peut pas être ignorées lors de l’exécution des opérations en bloc avec cette fonction.  
  
 La mémoire tampon vers laquelle pointée l’attribut d’instruction SQL_ATTR_ROWS_FETCHED_PTR contient le nombre de lignes affectées par un appel à **SQLBulkOperations**.  
  
 Lorsque le *opération* argument est SQL_ADD ou SQL_UPDATE_BY_BOOKMARK et la liste de sélection de la spécification de requête associée au curseur contient plusieurs références à la même colonne, elle est définie par le pilote si une erreur est généré ou le pilote ignore les références en double et effectue les opérations demandées.  
  
 Pour plus d’informations sur l’utilisation **SQLBulkOperations**, consultez [la mise à jour des données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).  
  
## <a name="performing-bulk-inserts"></a>Exécution en masse insère  
 Pour insérer des données avec **SQLBulkOperations**, une application effectue la séquence d’étapes suivante :  
  
1.  Exécute une requête qui retourne un jeu de résultats.  
  
2.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE au nombre de lignes qu’il souhaite insérer.  
  
3.  Appels **SQLBindCol** pour lier les données qu’il souhaite insérer. Les données sont liées à un tableau de taille égale à la valeur de SQL_ATTR_ROW_ARRAY_SIZE.  
  
    > [!NOTE]  
    >  La taille du tableau vers lequel pointé l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR doit être égale à SQL_ATTR_ROW_ARRAY_SIZE ou SQL_ATTR_ROW_STATUS_PTR doit être un pointeur null.  
  
4.  Appels **SQLBulkOperations**(*au paramètre StatementHandle,* SQL_ADD) pour effectuer l’insertion.  
  
5.  Si l’application a défini l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR, il peut inspecter ce tableau pour afficher le résultat de l’opération.  
  
 Si une application lie la colonne 0 avant d’appeler **SQLBulkOperations** avec un *opération* argument de SQL_ADD, le pilote met à jour les mémoires tampons de colonnes dépendantes 0 avec les valeurs de signet pour le récemment ligne insérée. Dans ce cas, l’application doit avoir l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS à SQL_UB_VARIABLE avant d’exécuter l’instruction. (Cela ne fonctionne pas avec un ODBC 2. *x* pilote.)  
  
 Données de type long peuvent être ajoutées dans les parties par SQLBulkOperations, à l’aide d’appels de SQLParamData et SQLPutData. Pour plus d’informations, consultez « Fournissant Long données en bloc Inserts et Updates » plus loin dans cette référence de fonction.  
  
 Il n’est pas nécessaire pour l’application d’appeler **SQLFetch** ou **SQLFetchScroll** avant d’appeler **SQLBulkOperations** (sauf lorsque vous passez par rapport à une API ODBC 2. *x* pilote ; consultez [la compatibilité descendante et conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)).  
  
 Le comportement est définies par le pilote si **SQLBulkOperations**, avec un *opération* argument de SQL_ADD, est appelée sur un curseur qui contient les colonnes en double. Le pilote peut retourner une valeur SQLSTATE définie par le pilote, ajoutez les données à la première colonne qui s’affiche dans le résultat de définir ou d’effectuer d’autres comportements définis par le pilote.  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>Les mises à jour en bloc à l’aide de signets  
 Pour effectuer des mises à jour en bloc à l’aide de signets avec **SQLBulkOperations**, une application effectue les étapes suivantes dans la séquence :  
  
1.  Définit l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS à SQL_UB_VARIABLE.  
  
2.  Exécute une requête qui retourne un jeu de résultats.  
  
3.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE au nombre de lignes qu’il souhaite mettre à jour.  
  
4.  Appels **SQLBindCol** pour lier les données qu’il souhaite mettre à jour. Les données sont liées à un tableau de taille égale à la valeur de SQL_ATTR_ROW_ARRAY_SIZE. Il appelle également **SQLBindCol** pour lier la colonne 0 (la colonne de signet).  
  
5.  Copie les signets pour les lignes qu’il s’intéresse à la mise à jour dans le tableau lié à la colonne 0.  
  
6.  Met à jour les données dans les mémoires tampons liées.  
  
    > [!NOTE]  
    >  La taille du tableau vers lequel pointé l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR doit être égale à SQL_ATTR_ROW_ARRAY_SIZE ou SQL_ATTR_ROW_STATUS_PTR doit être un pointeur null.  
  
7.  Appels **SQLBulkOperations**(*au paramètre StatementHandle,* SQL_UPDATE_BY_BOOKMARK).  
  
    > [!NOTE]  
    >  Si l’application a défini l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR, il peut inspecter ce tableau pour afficher le résultat de l’opération.  
  
8.  Appelle éventuellement **SQLBulkOperations**(*au paramètre StatementHandle*, SQL_FETCH_BY_BOOKMARK) pour extraire les données dans les mémoires tampons d’application liée pour vérifier que la mise à jour a eu lieu.  
  
9. Si les données a été mis à jour, le pilote change la valeur dans le tableau d’état de ligne pour les lignes appropriées en SQL_ROW_UPDATED.  
  
 En bloc des mises à jour effectuées par **SQLBulkOperations** peut inclure des données de type long à l’aide d’appels à **SQLParamData** et **SQLPutData**. Pour plus d’informations, consultez « Fournissant Long données en bloc Inserts et Updates » plus loin dans cette référence de fonction.  
  
 Si les signets persistent entre les curseurs, l’application n’a pas besoin d’appeler **SQLFetch** ou **SQLFetchScroll** avant la mise à jour par les signets. Il peut utiliser des signets qu’il a stockée à partir d’un curseur précédent. Si les signets ne sont pas conservés entre les curseurs, l’application doit appeler **SQLFetch** ou **SQLFetchScroll** pour récupérer les signets.  
  
 Le comportement est définies par le pilote si **SQLBulkOperations**, avec un *opération* argument de SQL_UPDATE_BY_BOOKMARK, est appelée sur un curseur qui contient les colonnes en double. Le pilote peut renvoyer un SQLSTATE définis par le pilote, mettre à jour de la première colonne qui s’affiche dans le jeu de résultats ou effectuer d’autres comportements définis par le pilote.  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>Exécution en bloc extrait à l’aide de signets  
 Pour effectuer des extractions en bloc à l’aide de signets avec **SQLBulkOperations**, une application effectue les étapes suivantes dans la séquence :  
  
1.  Définit l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS à SQL_UB_VARIABLE.  
  
2.  Exécute une requête qui retourne un jeu de résultats.  
  
3.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE au nombre de lignes qu’il souhaite extraire.  
  
4.  Appels **SQLBindCol** pour lier les données qu’il souhaite extraire. Les données sont liées à un tableau de taille égale à la valeur de SQL_ATTR_ROW_ARRAY_SIZE. Il appelle également **SQLBindCol** pour lier la colonne 0 (la colonne de signet).  
  
5.  Copie les signets pour les lignes qu’il s’intéresse à l’extraction dans le tableau lié à la colonne 0. (Cela suppose que l’application a déjà obtenu les signets séparément).  
  
    > [!NOTE]  
    >  La taille du tableau vers lequel pointé l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR doit être égale à SQL_ATTR_ROW_ARRAY_SIZE ou SQL_ATTR_ROW_STATUS_PTR doit être un pointeur null.  
  
6.  Appels **SQLBulkOperations**(*au paramètre StatementHandle,* SQL_FETCH_BY_BOOKMARK).  
  
7.  Si l’application a défini l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR, il peut inspecter ce tableau pour afficher le résultat de l’opération.  
  
 Si les signets persistent entre les curseurs, l’application n’a pas besoin d’appeler **SQLFetch** ou **SQLFetchScroll** avant d’extraire des signets. Il peut utiliser des signets qu’il a stockée à partir d’un curseur précédent. Si les signets ne sont pas conservés entre les curseurs, l’application doit appeler **SQLFetch** ou **SQLFetchScroll** une seule fois pour récupérer les signets.  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>L’exécution en bloc supprime à l’aide de signets  
 Pour effectuer des suppressions en bloc à l’aide de signets avec **SQLBulkOperations**, une application effectue les étapes suivantes dans la séquence :  
  
1.  Définit l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS à SQL_UB_VARIABLE.  
  
2.  Exécute une requête qui retourne un jeu de résultats.  
  
3.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE au nombre de lignes qu’il souhaite supprimer.  
  
4.  Appels **SQLBindCol** pour lier la colonne 0 (la colonne de signet).  
  
5.  Copie les signets pour les lignes qu’il s’intéresse à supprimer dans le tableau lié à la colonne 0.  
  
    > [!NOTE]  
    >  La taille du tableau vers lequel pointé l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR doit être égale à SQL_ATTR_ROW_ARRAY_SIZE ou SQL_ATTR_ROW_STATUS_PTR doit être un pointeur null.  
  
6.  Appels **SQLBulkOperations**(*au paramètre StatementHandle,* SQL_DELETE_BY_BOOKMARK).  
  
7.  Si l’application a défini l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR, il peut inspecter ce tableau pour afficher le résultat de l’opération.  
  
 Si les signets persistent entre les curseurs, l’application n’a pas d’appeler **SQLFetch** ou **SQLFetchScroll** avant la suppression de signets. Il peut utiliser des signets qu’il a stockée à partir d’un curseur précédent. Si les signets ne sont pas conservés entre les curseurs, l’application doit appeler **SQLFetch** ou **SQLFetchScroll** une seule fois pour récupérer les signets.  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>En fournissant des données de type Long pour les mises à jour et insertions en bloc  
 Données de type long peuvent être fournies pour les insertions en bloc et les mises à jour effectuées par les appels à **SQLBulkOperations**. Pour insérer ou mettre à jour des données de type long, une application effectue les étapes suivantes en plus de la procédure décrite dans les sections « Effectuer des insertions en bloc » et « Exécution en bloc des mises à jour à l’aide de signets » plus haut dans cette rubrique.  
  
1.  Quand il lie les données à l’aide de **SQLBindCol**, l’application place une valeur définie par l’application, comme le numéro de colonne, dans le  *\*TargetValuePtr* mémoire tampon pour data-at-execution colonnes. La valeur peut être utilisée ultérieurement pour identifier la colonne.  
  
     L’application place le résultat de la SQL_LEN_DATA_AT_EXEC (*longueur*) (macro) dans le  *\*StrLen_or_IndPtr* mémoire tampon. Si le type de données SQL de la colonne est SQL_LONGVARBINARY, SQL_LONGVARCHAR ou un type de données spécifiques à la source de données de type long et que le pilote retourne « Y » pour le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo**, *longueur*  est le nombre d’octets de données à envoyer pour le paramètre ; sinon, il doit être une valeur non négative et est ignoré.  
  
2.  Lorsque **SQLBulkOperations** est appelée, s’il existe des colonnes de données en cours d’exécution, que la fonction retourne SQL_NEED_DATA et les passe à l’étape 3, ce qui suit. (S’il n’y a aucune colonne de données en cours d’exécution, le processus est terminé).  
  
3.  L’application appelle **SQLParamData** pour récupérer l’adresse de la  *\*TargetValuePtr* mémoire tampon pour la première colonne de data-at-execution à traiter. **SQLParamData** retourne SQL_NEED_DATA. L’application récupère la valeur définie par l’application à partir de la  *\*TargetValuePtr* mémoire tampon.  
  
    > [!NOTE]  
    >  Bien que les paramètres de data-at-execution ressemblent à des colonnes de données en cours d’exécution, la valeur retournée par **SQLParamData** est différent pour chacun.  
  
     Colonnes de Data-at-execution sont des colonnes dans un ensemble de lignes pour lequel les données sont envoyées avec **SQLPutData** quand une ligne est mise à jour ou insérée avec **SQLBulkOperations**. Elles sont liées avec **SQLBindCol**. La valeur retournée par **SQLParamData** est l’adresse de la ligne dans le **TargetValuePtr* mémoire tampon qui est en cours de traitement.  
  
4.  L’application appelle **SQLPutData** une ou plusieurs fois pour envoyer des données pour la colonne. Plusieurs appels n’est nécessaire si la valeur de données ne peut pas être retournée dans le  *\*TargetValuePtr* mémoire tampon spécifiée dans **SQLPutData**; appels multiples à **SQLPutData** pour la même colonne sont autorisées uniquement lors de l’envoi des données de caractères C à une colonne avec un type de données de spécifique à la source de données, binaire ou caractère ou lors de l’envoi des données binaires de C à une colonne avec un caractère, binaire, ou le type de données spécifique à la source de données.  
  
5.  L’application appelle **SQLParamData** pour signaler que toutes les données a été envoyé pour la colonne.  
  
    -   S’il existe plus de colonnes de data-at-execution **SQLParamData** retourne SQL_NEED_DATA et l’adresse de la *TargetValuePtr* mémoire tampon pour la colonne data-at-execution suivante à traiter. L’application répète les étapes 4 et 5.  
  
    -   S’il n’y a pas d’autres colonnes de data-at-execution, le processus est terminé. Si l’instruction a été exécutée avec succès, **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO ; si l’exécution a échoué, elle retourne SQL_ERROR. À ce stade, **SQLParamData** peut retourner n’importe quel SQLSTATE qui peut être retourné par **SQLBulkOperations**.  
  
 Si l’opération est annulée ou une erreur se produit dans **SQLParamData** ou **SQLPutData** après **SQLBulkOperations** retourne SQL_NEED_DATA et avant l’envoi de données pour tous les colonnes de données en cours d’exécution, l’application peut appeler uniquement **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions** , **SQLParamData**, ou **SQLPutData** pour l’instruction ou la connexion associée à l’instruction. Si elle appelle une autre fonction pour l’instruction ou la connexion associée à l’instruction, la fonction retourne SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction).  
  
 Si l’application appelle **SQLCancel** tandis que le pilote a toujours besoin de données pour les colonnes de données en cours d’exécution, le pilote annule l’opération. L’application peut ensuite appeler **SQLBulkOperations** nouveau ; annulation n’affecte pas l’état de curseur ou la position actuelle du curseur.  
  
## <a name="row-status-array"></a>Tableau d’état des lignes  
 Le tableau d’état de ligne contient des valeurs d’état pour chaque ligne de données dans l’ensemble de lignes après un appel à **SQLBulkOperations**. Le pilote définit les valeurs d’état dans ce tableau après un appel à **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**, ou **SQLBulkOperations** . Ce tableau est rempli initialement par un appel à **SQLBulkOperations** si **SQLFetch** ou **SQLFetchScroll** n’a pas été appelé avant **SQLBulkOperations** . Ce tableau est indiqué par l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR. Le nombre d’éléments dans les tableaux d’état de ligne doit égal au nombre de lignes dans l’ensemble de lignes (comme défini par l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE). Pour plus d’informations sur ce tableau d’état de ligne, consultez [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Exemple de code  
 L’exemple suivant extrait les 10 lignes de données à la fois à partir de la table Customers. Il invite ensuite l’utilisateur pour une action à prendre. Pour réduire le trafic réseau, la mémoire tampon exemple met à jour, suppressions et insère localement dans les tableaux liés, mais aux offsets au-delà de l’ensemble de lignes de données. Lorsque l’utilisateur choisit d’envoyer des mises à jour, suppressions et insertions à la source de données, le code définit la liaison de décalage de façon appropriée et appelle **SQLBulkOperations**. Par souci de simplicité, l’utilisateur ne peut pas mettre en mémoire tampon plus de 10 mises à jour, suppressions ou insertions.  
  
```cpp  
// SQLBulkOperations_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include "stdio.h"  
  
#define UPDATE_ROW 100  
#define DELETE_ROW 101  
#define ADD_ROW 102  
#define SEND_TO_DATA_SOURCE 103  
#define UPDATE_OFFSET 10  
#define INSERT_OFFSET 20  
#define DELETE_OFFSET 30  
  
// Define structure for customer data (assume 10 byte maximum bookmark size).  
typedef struct tagCustStruct {  
   SQLCHAR Bookmark[10];  
   SQLINTEGER BookmarkLen;  
   SQLUINTEGER CustomerID;  
   SQLINTEGER CustIDInd;  
   SQLCHAR CompanyName[51];  
   SQLINTEGER NameLenOrInd;  
   SQLCHAR Address[51];  
   SQLINTEGER AddressLenOrInd;  
   SQLCHAR Phone[11];  
   SQLINTEGER PhoneLenOrInd;  
} CustStruct;  
  
// Allocate 40 of these structures. Elements 0-9 are for the current rowset,  
// elements 10-19 are for the buffered updates, elements 20-29 are for  
// the buffered inserts, and elements 30-39 are for the buffered deletes.  
CustStruct CustArray[40];  
SQLUSMALLINT RowStatusArray[10], Action, RowNum, NumUpdates = 0, NumInserts = 0,  
NumDeletes = 0;  
SQLLEN BindOffset = 0;  
SQLRETURN retcode;  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLHSTMT hstmt = NULL;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // Set the following statement attributes:  
   // SQL_ATTR_CURSOR_TYPE:           Keyset-driven  
   // SQL_ATTR_ROW_BIND_TYPE:         Row-wise  
   // SQL_ATTR_ROW_ARRAY_SIZE:        10  
   // SQL_ATTR_USE_BOOKMARKS:         Use variable-length bookmarks  
   // SQL_ATTR_ROW_STATUS_PTR:        Points to RowStatusArray  
   // SQL_ATTR_ROW_BIND_OFFSET_PTR:   Points to BindOffset  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_KEYSET_DRIVEN, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER)sizeof(CustStruct), 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_USE_BOOKMARKS, (SQLPOINTER)SQL_UB_VARIABLE, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_OFFSET_PTR, &BindOffset, 0);  
  
   // Bind arrays to the bookmark, CustomerID, CompanyName, Address, and Phone columns.  
   retcode = SQLBindCol(hstmt, 0, SQL_C_VARBOOKMARK, CustArray[0].Bookmark, sizeof(CustArray[0].Bookmark), &CustArray[0].BookmarkLen);  
   retcode = SQLBindCol(hstmt, 1, SQL_C_ULONG, &CustArray[0].CustomerID, 0, &CustArray[0].CustIDInd);  
   retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, CustArray[0].CompanyName, sizeof(CustArray[0].CompanyName), &CustArray[0].NameLenOrInd);  
   retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, CustArray[0].Address, sizeof(CustArray[0].Address), &CustArray[0].AddressLenOrInd);  
   retcode = SQLBindCol(hstmt, 4, SQL_C_CHAR, CustArray[0].Phone, sizeof(CustArray[0].Phone), &CustArray[0].PhoneLenOrInd);  
  
   // Execute a statement to retrieve rows from the Customers table.  
   retcode = SQLExecDirect(hstmt, (SQLCHAR*)"SELECT CustomerID, CompanyName, Address, Phone FROM Customers", SQL_NTS);  
  
   // Fetch and display the first 10 rows.  
   retcode = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
   // DisplayCustData(CustArray, 10);  
  
   // Call GetAction to get an action and a row number from the user.  
   // while (GetAction(&Action, &RowNum)) {  
   Action = SQL_FETCH_NEXT;  
   RowNum = 2;  
   switch (Action) {  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmt, Action, RowNum);  
         // DisplayCustData(CustArray, 10);  
         break;  
  
      case UPDATE_ROW:  
         // Check if we have reached the maximum number of buffered updates.  
         if (NumUpdates < 10) {  
            // Get the new customer data and place it in the next available element of  
            // the buffered updates section of CustArray, copy the bookmark of the row  
            // being updated to the same element, and increment the update counter.  
            // Checking to see we have not already buffered an update for this  
            // row not shown.  
            // GetNewCustData(CustArray, UPDATE_OFFSET + NumUpdates);  
            memcpy(CustArray[UPDATE_OFFSET + NumUpdates].Bookmark,  
               CustArray[RowNum - 1].Bookmark,  
               CustArray[RowNum - 1].BookmarkLen);  
            CustArray[UPDATE_OFFSET + NumUpdates].BookmarkLen =  
               CustArray[RowNum - 1].BookmarkLen;  
            NumUpdates++;  
         } else {  
            printf("Buffers full. Send buffered changes to the data source.");  
         }  
         break;  
      case DELETE_ROW:  
         // Check if we have reached the maximum number of buffered deletes.  
         if (NumDeletes < 10) {  
            // Copy the bookmark of the row being deleted to the next available element  
            // of the buffered deletes section of CustArray and increment the delete  
            // counter. Checking to see we have not already buffered an update for  
            // this row not shown.  
            memcpy(CustArray[DELETE_OFFSET + NumDeletes].Bookmark,  
               CustArray[RowNum - 1].Bookmark,  
               CustArray[RowNum - 1].BookmarkLen);  
  
            CustArray[DELETE_OFFSET + NumDeletes].BookmarkLen =  
               CustArray[RowNum - 1].BookmarkLen;  
  
            NumDeletes++;  
         } else  
            printf("Buffers full. Send buffered changes to the data source.");  
         break;  
  
      case ADD_ROW:  
         // reached maximum number of buffered inserts?  
         if (NumInserts < 10) {  
            // Get the new customer data and place it in the next available element of  
            // the buffered inserts section of CustArray and increment insert counter.  
            // GetNewCustData(CustArray, INSERT_OFFSET + NumInserts);  
            NumInserts++;  
         } else  
            printf("Buffers full. Send buffered changes to the data source.");  
         break;  
  
      case SEND_TO_DATA_SOURCE:  
         // If there are any buffered updates, inserts, or deletes, set the array size  
         // to that number, set the binding offset to use the data in the buffered  
         // update, insert, or delete part of CustArray, and call SQLBulkOperations to  
         // do the updates, inserts, or deletes. Because we will never have more than  
         // 10 updates, inserts, or deletes, we can use the same row status array.  
         if (NumUpdates) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumUpdates, 0);  
            BindOffset = UPDATE_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_UPDATE_BY_BOOKMARK);  
            NumUpdates = 0;  
         }  
  
         if (NumInserts) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumInserts, 0);  
            BindOffset = INSERT_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_ADD);  
            NumInserts = 0;  
         }  
  
         if (NumDeletes) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumDeletes, 0);  
            BindOffset = DELETE_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_DELETE_BY_BOOKMARK);  
            NumDeletes = 0;  
         }  
  
         // If there were any updates, inserts, or deletes, reset the binding offset  
         // and array size to their original values.  
         if (NumUpdates || NumInserts || NumDeletes) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);  
            BindOffset = 0;  
         }  
         break;  
   }  
   // }  
  
   // Close the cursor.  
   SQLFreeStmt(hstmt, SQL_CLOSE);  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une mémoire tampon à une colonne dans un jeu de résultats|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Extraction d’un bloc de données ou le défilement à travers un résultat défini|[SQLFetchScroll, fonction](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Obtention d’un champ unique d’un descripteur|[SQLGetDescField, fonction](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Obtention de plusieurs champs d’un descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Définition d’un champ unique d’un descripteur|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Définition de plusieurs champs d’un descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Positionnement du curseur, l’actualisation des données dans l’ensemble de lignes, ou la mise à jour ou suppression de données dans l’ensemble de lignes|[SQLSetPos, fonction](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Définition d’un attribut d’instruction|[SQLSetStmtAttr, fonction](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
