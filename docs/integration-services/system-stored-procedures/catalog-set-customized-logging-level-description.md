---
title: catalog.set_customized_logging_level_description | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 6ceaa39f-2439-457b-b99f-f12d88a1be32
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0fe0aff3fdf8a61a4c7d331c0123ed6486612b40
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58275142"
---
# <a name="catalogsetcustomizedloggingleveldescription"></a>catalog.set_customized_logging_level_description
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Change la description d’un niveau de journalisation personnalisée existant. Pour plus d’informations sur les niveaux de journalisation personnalisée, consultez [Journalisation Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.set_customized_logging_level_description [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
```  
  
## <a name="arguments"></a>Arguments  
 [ @level_name = ] *level_name*  
 Nom d’un niveau de journalisation personnalisée existant.  
  
 *level_name* est de type **nvarchar(128)**.  
  
 [ @level_description = ] *level_description*  
 Nouvelle description du niveau de journalisation personnalisée spécifié.  
  
 *level_description* est de type **nvarchar(1024)**.  
  
## <a name="remarks"></a>Notes   
  
## <a name="return-codes"></a>Codes de retour  
 0 (succès)  
  
 Lorsque la procédure stockée échoue, elle génère une erreur.  
  
## <a name="result-set"></a>Jeu de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   L’appartenance au rôle de base de données **ssis_admin**  
  
-   L’appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit les conditions provoquant l'échec de la procédure stockée.  
  
-   L’utilisateur ne dispose pas des autorisations requises.  
  
  
