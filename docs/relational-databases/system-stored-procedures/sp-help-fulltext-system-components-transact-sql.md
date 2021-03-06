---
title: sp_help_fulltext_system_components (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_components_TSQL
- sp_help_fulltext_components
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_system_components
ms.assetid: ac1fc7a0-7f46-4a12-8c5c-8d378226a8ce
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 61301b0c6916ba11cb54cc0c8d8ab961cc3ae659
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534321"
---
# <a name="sphelpfulltextsystemcomponents-transact-sql"></a>sp_help_fulltext_system_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Retourne des informations sur les analyseurs lexicaux, le filtre et les gestionnaires de protocoles. **sp_help_fulltext_system_components** retourne également une liste des identificateurs de bases de données et catalogues de texte intégral qui ont utilisé le composant spécifié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_fulltext_system_components   
         { 'all'| [ @component_type = ] 'component_type' }  
    , [ @param = ] 'param'  
```  
  
## <a name="arguments"></a>Arguments  
 'all'  
 Retourne des informations pour tous les composants de recherche en texte intégral.  
  
`[ @component_type = ] component_type` Spécifie le type de composant. *component_type* peut prendre l’une des opérations suivantes :  
  
-   **wordbreaker**  
  
-   **filter**  
  
-   **Gestionnaire de protocole**  
  
-   **fullpath**  
  
 Si vous spécifiez un chemin d'accès complet, *param* doit également être spécifié avec le chemin d'accès complet à la bibliothèque de liens dynamiques (DLL) du composant, sans quoi un message d'erreur est retourné.  
  
`[ @param = ] param` Selon le type de composant, c’est une des opérations suivantes : un identificateur de paramètres régionaux (LCID), l’extension de fichier «. » du préfixe, le nom du composant complet du Gestionnaire de protocole ou le chemin d’accès complet à la DLL de composant.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Le jeu de résultats suivant est retourné pour les composants système.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**componenttype**|**sysname**|Type de composant. Il peut s'agir :<br /><br /> Filter<br /><br /> protocol handler<br /><br /> wordbreaker|  
|**componentname**|**sysname**|Nom du composant.|  
|**clsid**|**uniqueidentifier**|Identificateur de classe du composant.|  
|**fullpath**|**nvarchar (256)**|Chemin d'accès de l'emplacement du composant.<br /><br /> NULL = l’appelant n’est pas membre **serveradmin** rôle serveur fixe.|  
|**version**|**nvarchar(30)**|Numéro de version du composant.|  
|**manufacturer**|**sysname**|Nom du fabricant du composant.|  
  
 Le jeu de résultats suivant est retourné uniquement si un ou plusieurs catalogues de texte intégral existent et utilisent *component_type*.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**dbid**|**Int**|ID de la base de données.|  
|**ftcatid**|**Int**|Identificateur du catalogue de texte intégral.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **public** rôle ; Toutefois, les utilisateurs peuvent voir uniquement les informations sur les catalogues de texte intégral pour lequel ils ont l’autorisation VIEW DEFINITION. Seuls les membres du rôle de serveur fixe **serveradmin** peuvent voir les valeurs de la colonne **fullpath** .  
  
## <a name="remarks"></a>Notes  
 Cette méthode est particulièrement importante lors de la préparation d'une mise à niveau. Exécutez la procédure stockée dans une base de données spécifique et utilisez le résultat afin de déterminer si un catalogue sera affecté par la mise à niveau.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-listing-all-full-text-system-components"></a>A. Liste de tous les composants système de texte intégral  
 L'exemple suivant répertorie tous les composants systèmes de texte intégral enregistrés sur l'instance de serveur.  
  
```  
EXEC sp_help_fulltext_system_components 'all';  
GO  
```  
  
### <a name="b-listing-word-breakers"></a>B. Liste des analyseurs lexicaux  
 L'exemple suivant répertorie tous les analyseurs lexicaux enregistrés sur l'instance du service.  
  
```  
EXEC sp_help_fulltext_system_components 'wordbreaker';  
GO  
```  
  
### <a name="c-determining-whether-a-specific-word-breaker-is-registered"></a>C. Détermination de si un analyseur lexical spécifique est inscrit  
 L'exemple suivant répertorie l'analyseur lexical pour la langue turque (LCID = 1055) si celle-ci a été installée sur le système et enregistrée sur l'instance du service. Cet exemple spécifie les noms de paramètres, **@component_type** et **@param**.  
  
```  
EXEC sp_help_fulltext_system_components @component_type = 'wordbreaker', @param = 1055;  
GO  
```  
  
 Par défaut, cet analyseur lexical n'est pas installé, de sorte que le jeu de résultats est vide.  
  
### <a name="d-determining-whether-a-specific-filter-has-been-registered"></a>D. Détermination de si un filtre spécifique est inscrit  
 L'exemple suivant répertorie le filtre pour le composant .xdoc si celui-ci a été installé manuellement sur le système et enregistré sur l'instance de serveur.  
  
```  
EXEC sp_help_fulltext_system_components 'filter', '.xdoc';  
GO  
```  
  
 Par défaut, ce filtre n'est pas installé, de sorte que le jeu de résultats est vide.  
  
### <a name="e-listing-a-specific-dll-file"></a>E. Affichage d'un fichier .dll spécifique  
 L'exemple suivant affiche un fichier .ddl spécifique, `nlhtml.dll`, installé par défaut.  
  
```  
EXEC sp_help_fulltext_system_components 'fullpath',   
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\nlhtml.dll';  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher ou modifier des filtres et des analyseurs lexicaux inscrits](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md)   
 [Configurer et gérer les analyseurs lexicaux et générateurs de formes dérivées pour la recherche](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Configurer et gérer des filtres pour la recherche](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [Procédures stockées de recherche en texte intégral et la recherche sémantique &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
