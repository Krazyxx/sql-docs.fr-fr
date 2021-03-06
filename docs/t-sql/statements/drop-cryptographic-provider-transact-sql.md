---
title: DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP CRYPTOGRAPHIC PROVIDER
- DROP_CRYPTOGRAPHIC_PROVIDER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP CRYPTOGRAPHIC PROVIDER statement
ms.assetid: 71c55c20-439e-4897-aef5-f20e556d668f
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 403cef4e8c1e3336be9a2d7df8ae8c14a06f045b
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361444"
---
# <a name="drop-cryptographic-provider-transact-sql"></a>DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un fournisseur de chiffrement dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP CRYPTOGRAPHIC PROVIDER provider_name   
```  
  
## <a name="arguments"></a>Arguments  
 *provider_name*  
 Nom du fournisseur EKM (Extensible Key Management)  
  
## <a name="remarks"></a>Notes   
 Pour supprimer un fournisseur EKM (Extensible Key Management), toutes les sessions qui utilisent le fournisseur doivent être arrêtées.  
  
 Un fournisseur EKM ne peut être supprimé que si aucune information d'identification ne lui correspond.  
  
 Si des clés sont mappées à un fournisseur EKM lorsque celui-ci est supprimé, les GUID des clés restent stockées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si un fournisseur est créé ultérieurement avec les mêmes GUID de clé, les clés sont réutilisées.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL sur la clé symétrique.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime un fournisseur de chiffrement appelé `SecurityProvider`.  
  
```  
/* First, disable provider to perform the upgrade.  
This will terminate all open cryptographic sessions. */  
ALTER CRYPTOGRAPHIC PROVIDER SecurityProvider   
SET ENABLED = OFF;  
GO  
/* Drop the provider. */  
DROP CRYPTOGRAPHIC PROVIDER SecurityProvider;  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Gestion de clés extensible &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [ALTER CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-cryptographic-provider-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
  
