---
title: sp_OASetProperty (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OASetProperty
- sp_OASetProperty_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OASetProperty
ms.assetid: 0fe7d554-6b67-4d55-9d3e-4096802c47f8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d2d3cc319a99c9e1b157e5b6bc06cabea2dd19a7
ms.sourcegitcommit: 603d5ef9b45c2f111d36d11864dc032917e4a321
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65450061"
---
# <a name="spoasetproperty-transact-sql"></a>sp_OASetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affecte une nouvelle valeur à une propriété d'un objet OLE.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_OASetProperty objecttoken , propertyname , newvalue [ , index... ]  
```  
  
## <a name="arguments"></a>Arguments  
 *objecttoken*  
 Jeton d’objet d’un objet OLE précédemment créé par **sp_OACreate**.  
  
 *propertyname*  
 Nom de la propriété de l'objet OLE à laquelle une nouvelle valeur doit être affectée.  
  
 *newvalue*  
 Nouvelle valeur de la propriété, ce doit être une valeur du type de données approprié.  
  
 *index*  
 Paramètre d'index. Si spécifié, *index* doit être une valeur de type de données approprié.  
  
 Certaines propriétés possèdent des paramètres. Elles sont désignées sous le nom de propriétés indexées, et les paramètres s'appellent des paramètres d'index. Une propriété peut posséder plusieurs paramètres d'index.  
  
> [!NOTE]  
>  Les paramètres pour cette procédure stockée sont spécifiés par position et non pas par nom.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) ou un nombre différent de zéro (échec), qui représente la valeur entière de HRESULT renvoyée par l'objet OLE Automation.  
  
 Pour plus d’informations sur les Codes de retour HRESULT, consultez [OLE Automation Codes de retour et les informations d’erreur](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **sysadmin** rôle serveur fixe ou d’autorisation d’exécuter directement cette procédure stockée. `Ole Automation Procedures` configuration doit être **activé** à utiliser des procédures système liées à OLE Automation.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant définit la `HostName` propriété (de l’élément précédemment créé **SQLServer** objet) à une nouvelle valeur.  
  
```  
EXEC @hr = sp_OASetProperty @object, 'HostName', 'Gizmo';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées OLE Automation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Exemple de script OLE Automation](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
