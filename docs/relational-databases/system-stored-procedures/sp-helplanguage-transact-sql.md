---
title: sp_helplanguage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d1b567b7d20f4d588fe0ca70f68be4318ce24398
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531671"
---
# <a name="sphelplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Affiche des informations sur une langue de remplacement particulière ou sur toutes les langues dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @language = ] 'language'` Est le nom de la langue de remplacement pour lequel afficher des informations. *langage* est **sysname**, avec NULL comme valeur par défaut. Si *langage* est spécifié, les informations sur le langage spécifié sont retournées. Si la langue n’est pas spécifiée, des informations sur toutes les langues dans le **sys.syslanguages** affichage de compatibilité est retournée.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**langid**|**smallint**|Numéro d'identification de la langue.|  
|**dateformat**|**nchar(3)**|Format de la date.|  
|**datefirst**|**tinyint**|Premier jour de la semaine : 1 pour lundi, 2 pour mardi, etc jusqu'à 7 pour dimanche.|  
|**upgrade**|**Int**|Version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la dernière mise à niveau pour cette langue.|  
|**nom**|**sysname**|Nom de la langue.|  
|**alias**|**sysname**|Nom de remplacement de la langue.|  
|**months**|**nvarchar(372)**|Noms des mois.|  
|**shortmonths**|**nvarchar(132)**|Abréviations des noms des mois.|  
|**days**|**nvarchar(217)**|Noms des jours.|  
|**lcid**|**Int**|ID de paramètres régionaux Windows pour la langue.|  
|**msglangid**|**smallint**|ID du groupe de messages du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-information-about-a-single-language"></a>A. Renvoi d’informations sur une langue  
 L'exemple suivant affiche des informations sur la langue de remplacement `French`.  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>B. Renvoi d’informations sur toutes les langues  
 L'exemple suivant vous renseigne sur toutes les langues de remplacement installées.  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du moteur de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [SET LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
