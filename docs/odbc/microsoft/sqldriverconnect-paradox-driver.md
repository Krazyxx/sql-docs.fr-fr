---
title: SQLDriverConnect (Paradox Driver) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bae4a842729c8d302731ebf5fec22abb817f4c75
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63238379"
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Paradox. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** vous permet de se connecter à un pilote sans création d’une source de données (DSN).  
  
 Les mots clés suivants sont pris en charge dans la chaîne de connexion pour tous les pilotes : **DSN**, **DBQ**, et **FIL**.  
  
 Le **PWD** mot-clé prend également en charge. Le mot clé PWD ne doit pas inclure les caractères spéciaux (voir SQL_SPECIAL_CHARACTERS dans **SQLGetInfo** valeurs retournées).  
  
 Après l’ouverture d’un fichier protégé par mot de passe par un utilisateur, les autres utilisateurs ne sont pas autorisés à ouvrir le même fichier.  
  
 Le tableau suivant montre les mots-clés minimales requis pour se connecter à chaque pilote et fournit un exemple de paires mot clé/valeur utilisées avec **SQLDriverConnect**. Pour obtenir une liste complète des valeurs DRIVERID, consultez [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).  
  
> [!NOTE]  
>  Si DBQ ou DefaultDir n’est pas spécifié pour le pilote Paradox, le pilote se connecte dans le répertoire actif.  
  
|Pilote|Mots clés requis|Exemple|  
|------------|-----------------------|-------------|  
|Paradox|Pilote, DriverID|Driver={Microsoft Paradox Driver (*.db )}; DBQ=c:\temp;DriverID=26|
