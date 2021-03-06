---
title: Projet (synchronisation) (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e223fb7d-05ec-4fa5-8973-d845c33a23dd
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: fe71e5b301c016e25bb179e0104831285dab3ce1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62628685"
---
# <a name="project-settingssynchronization-oracletosql"></a>Paramètres du projet (Synchronisation) (OracleToSQL)
La page de synchronisation de la **paramètres du projet** boîte de dialogue contient des paramètres qui personnalisent le SSMA charge et les actualisations de la base de données objets, tels que les tables et procédures stockées, dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Les options d’actions par défaut spécifient les paramètres par défaut de l’actualisation des objets à partir de la base de données Oracle et pour la synchronisation des objets avec la base de données SQL Server. Pour plus d’informations, consultez [Actualiser à partir de la base de données - Oracle](../../ssma/oracle/refresh-from-database-oracletosql.md).  
  
Vous pouvez accéder à deux différentes pages de synchronisation qui contiennent les mêmes paramètres :  
  
-   Pour spécifier les paramètres pour tous les futurs projets SSMA, sur le **outils** menu, cliquez sur **par défaut des paramètres de projet**, puis cliquez sur **synchronisation** en bas du volet gauche.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, cliquez sur **paramètres du projet**, puis cliquez sur **synchronisation** en bas du volet gauche.  
  
## <a name="miscellaneous-options"></a>Options diverses  
**Tentatives**  
Spécifie le nombre de tentatives de SSMA doit lors du chargement d’objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les objets qui ne sont pas chargés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lors de la tentative actuelle sera tentée à nouveau jusqu'à ce que SSMA atteigne le nombre maximal de tentatives défini dans le processus de synchronisation en cours. Ensemble de valeur par défaut est **2**  
  
## <a name="synchronization-for-oracle-options"></a>Synchronisation pour les Options d’Oracle  
**Action sur la modification de l’objet locaux et distants**  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque la définition d’objet est modifié dans SSMA et sur le serveur de base de données. Ensemble de valeur par défaut est **Actualiser à partir de la base de données**.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
**Action sur la modification de l’objet local**  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque l’objet est modifié dans SSMA. Ensemble de valeur par défaut est **Skip**.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
**Action sur la modification de l’objet distant**  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque les objets sont modifiées sur le serveur de base de données. Ensemble de valeur par défaut est **Actualiser à partir de la base de données**.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
**Action lorsque les métadonnées de l’objet local sont manquantes**  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque les métadonnées locales sont manquante. Ensemble de valeur par défaut est **Actualiser à partir de la base de données**.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
## <a name="synchronization-for-sql-server-options"></a>Synchronisation pour les Options de SQL Server  
**Action sur la modification de l’objet locaux et distants**  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque la définition d’objet est modifié dans SSMA et sur le serveur de base de données. Ensemble de valeur par défaut est **écriture à la base de données**.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour les objets dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
**Action sur la modification de l’objet local**  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque l’objet est modifié dans SSMA. Ensemble de valeur par défaut est **écriture à la base de données**.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour l’objet dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
**Action sur la modification de l’objet distant**  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque les objets sont modifiées sur le serveur de base de données.  Ensemble de valeur par défaut est **Actualiser à partir de la base de données**.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour l’objet dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
**Action lorsque les métadonnées de l’objet local sont manquantes**  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque les métadonnées locales sont manquante. Ensemble de valeur par défaut est **Actualiser à partir de la base de données**.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA sélectionne le **Actualiser à partir de la base de données** option lorsque la condition est remplie.  
  
-   Si vous sélectionnez **écrire dans la base de données**, SSMA supprimera l’objet à partir de la base de données lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
