---
title: catalog.restore_project (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 8adee525-579b-4d2f-b807-e2ecc07fb2e9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3cbcddc72eac1fbe8c5e4c7e2f2f831c3a1c799d
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58274735"
---
# <a name="catalogrestoreproject-ssisdb-database"></a>catalog.restore_project (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restaure un projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans une version précédente.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.restore_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project _name  
    , [ @object_version_lsn = ] object_version_lsn  
  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name = ] *folder_name*  
 Nom du dossier qui contient le projet. *folder_name* est de type **nvarchar(128)**.  
  
 [ @project _name = ] *project_name*  
 Nom du projet. *project_name* est de type **nvarchar(128)**.  
  
 [ @object_version_lsn = ] *object_version_lsn*  
 Version du projet. *object_version_lsn* est de type **bigint**.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Les détails du projet sont retournés sous forme de **varbinary(MAX)** dans le cadre du jeu de résultats si le *project_name* est trouvé.  
  
 **NO RESULT SET** est retourné si le projet ne peut pas être restauré dans le dossier spécifié.  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur le projet  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   La version du projet n'existe pas ou ne correspond pas au nom du projet  
  
-   Le projet n'existe pas  
  
-   L’utilisateur n’a pas les autorisations appropriées  
  
## <a name="remarks"></a>Notes   
 Lorsqu'un projet est restauré, tous les paramètres reçoivent les valeurs par défaut et toutes les références environnementales restent inchangées. Le nombre maximal de versions du projet conservées dans le catalogue est déterminé par le propriété de catalogue **MAX_VERSIONS_PER_PROJECT**, comme indiqué dans la vue [catalog_property](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md).  
  
> [!WARNING]  
>  Les références environnementales peuvent ne plus être valides une fois qu'un projet a été restauré.  
  
  
