---
title: xp_loginconfig (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_loginconfig_TSQL
- xp_loginconfig
dev_langs:
- TSQL
helpviewer_keywords:
- xp_loginconfig
ms.assetid: d380e799-2857-408a-bcbf-5e73a8e6aa5a
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8590a33f870dc14ac34118ce5e655acc6e67f257
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62645101"
---
# <a name="xploginconfig-transact-sql"></a>xp_loginconfig (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Signale la configuration de la sécurité de connexion d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xp_loginconfig ['config_name']  
```  
  
## <a name="arguments"></a>Arguments  
 **'** *config_name* **'**  
 Valeur de configuration à afficher. Si *nom_de_config* est ne pas spécifié, toutes les valeurs de configuration sont indiquées. *nom_de_config* est **sysname**, avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**mode de connexion**|Mode de sécurité de connexion. Les valeurs possibles sont **mixte** et **l’authentification Windows**.<br /><br /> Remplacé par :<br /><br /> `SELECT SERVERPROPERTY('IsIntegratedSecurityOnly'); GO`|  
|**connexion par défaut**|Nom de l'ID de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par défaut pour les utilisateurs autorisés de connexions approuvées (les utilisateurs sans nom de connexion correspondant). La connexion par défaut est **invité**. Cette valeur est fournie pour des raisons de compatibilité descendante.|  
|**Domaine par défaut**|Nom du domaine Windows par défaut pour les utilisateurs réseau de connexions approuvées. Le domaine par défaut est le domaine de l'ordinateur exécutant Windows et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette valeur est fournie pour des raisons de compatibilité descendante.|  
|**niveau d’audit**|Niveau d'audit. Les valeurs possibles sont **aucun**, **réussite**, **échec**, et **tous les**. Les audits sont enregistrés dans le journal des erreurs et dans l'Observateur d'événements Windows.|  
|**nom d’hôte de l’ensemble**|Indique si le nom d'hôte de l'enregistrement de connexion client est remplacé par le nom d'utilisateur réseau Windows. Les valeurs possibles sont **true** ou **false**. S’il est défini, le nom d’utilisateur réseau s’affiche dans la sortie de **sp_who**.|  
|**carte _**|Indique les caractères spéciaux Windows mappés sur le caractère de soulignement (_) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide. Les valeurs possibles sont **séparateur de domaine** (valeur par défaut), **espace**, **null**, ou n’importe quel caractère unique. Cette valeur est fournie pour des raisons de compatibilité descendante.|  
|**carte $**|Indique les caractères spéciaux Windows mappés sur le caractère $ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide. Les valeurs possibles sont **séparateur de domaine**, **espace**, **null**, ou n’importe quel caractère unique. La valeur par défaut est **espace**. Cette valeur est fournie pour des raisons de compatibilité descendante.|  
|**mapper #**|Indique les caractères spéciaux Windows mappés sur le caractère # [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide. Les valeurs possibles sont **séparateur de domaine**, **espace**, **null**, ou n’importe quel caractère unique. La valeur par défaut est le trait d'union. Cette valeur est fournie pour des raisons de compatibilité descendante.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Valeur de configuration|  
|**config value**|**sysname**|Paramètre de la valeur de configuration|  
  
## <a name="remarks"></a>Notes  
 **xp_loginconfig** ne peut pas être utilisé pour définir les valeurs de configuration.  
  
 Pour définir le mode de connexion et le niveau d'audit, utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation CONTROL sur le **master** base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-how-to-report-all-configuration-values"></a>A. Comment signaler toutes les valeurs de configuration  
 Le code exemple suivant montre tous les paramètres actuellement configurés.  
  
```  
EXEC xp_loginconfig;  
GO  
```  
  
### <a name="b-how-to-report-a-specific-configuration-value"></a>B. Comment signaler une valeur de configuration spécifique  
 Le code exemple suivant montre la configuration uniquement pour le mode de connexion.  
  
```  
EXEC xp_loginconfig 'login mode';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
