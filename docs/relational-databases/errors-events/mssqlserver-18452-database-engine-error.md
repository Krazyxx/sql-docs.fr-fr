---
title: MSSQLSERVER_18452 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6fe60468ef23188e3ff832857dddd43060af00d0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751147"
---
# <a name="mssqlserver18452"></a>MSSQLSERVER_18452
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|18452|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOGON_INVALID_CONNECT|  
|Texte du message|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Il s’agit d’un compte de connexion SQL Server, qui ne peut pas être utilisé avec l’authentification Windows.%.\*ls.|  
  
## <a name="explanation"></a>Explication  
L'utilisateur a essayé de se connecter à l'aide d'informations d'identification qui ne peuvent pas être validées. Les causes possibles sont :  
  
-   La connexion peut être une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais le serveur accepte uniquement l'authentification Windows.  
  
-   Vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais la connexion utilisée n'existe pas sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   La connexion peut utiliser l'authentification Windows mais elle constitue un principal Windows non reconnu. Un principal Windows non reconnu signifie que la connexion ne peut pas être vérifiée par Windows. Cela peut être dû au fait que la connexion Windows s'effectue à partir d'un domaine non approuvé.  
  
Des problèmes similaires peuvent provoquer l'erreur 18456 moins spécifique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Si vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vérifiez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré en mode Authentification mixte.  
  
Si vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vérifiez que la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] existe.  
  
Si vous essayez de vous connecter à l'aide de l'authentification Windows, vérifiez que vous êtes correctement connecté au domaine approprié.  
  
