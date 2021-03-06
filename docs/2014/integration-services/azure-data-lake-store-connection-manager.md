---
title: Gestionnaire de connexions Azure Data Lake Store | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSCM.F1
- SQL11.DTS.DESIGNER.AFPADLSCM.F1
ms.assetid: 7f1323f9-9dc3-4378-9c70-bbc65bfeabfd
author: yualan
ms.author: janinez
manager: craigg
ms.openlocfilehash: dc1918bec6dc8f0cfa242341b59fefd477854887
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62836889"
---
# <a name="azure-data-lake-store-connection-manager"></a>Gestionnaire de connexions Azure Data Lake Store
  Le **Gestionnaire de connexions Azure Data Lake Store** permet à un package SSIS pour vous connecter à un service Azure Data Lake Store via deux types d’authentification : Identité de l’utilisateur Azure AD et l’identité de Service Azure AD.  

## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Configurer le gestionnaire de connexions Azure Data Lake Store 
  
1.  Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS** , sélectionnez **AzureDataLake**, puis cliquez sur **Ajouter**.   
  
2.  Dans la boîte de dialogue Éditeur du gestionnaire de connexions Azure Data Lake Store, tapez l’URL de l’hôte Azure Data Lake Store dans le champ **Hôte ADLS** . Par exemple : https://test.azuredatalakestore.net ou test.azuredatalakestore.net.
  
3.  Choisissez le type d’authentification correspondant pour accéder aux données Azure Data Lake Store.

    1.  Si vous avez sélectionné l’option d’authentification **Identité de l’utilisateur Azure AD** , procédez comme suit :

        1. Spécifiez des valeurs pour les champs **Nom d’utilisateur** et **Mot de passe** . 
    
        2. Cliquez sur le bouton **Tester la connexion** pour tester la connexion. Si vous et votre administrateur locataire n’avez pas déjà autorisé SSIS à accéder à vos données Azure Data Lake Store, vous devez cliquer sur le bouton **Accepter** pour autoriser SSIS à accéder à vos données Azure Data Lake Store dans la boîte de dialogue indépendante. Pour plus d’informations sur cette procédure de consentement, consultez [Intégration d’applications dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        > [!NOTE] 
        > Pour l’option d’authentification Identité de l’utilisateur Azure AD, l’authentification multifacteur avec un compte Microsoft n’est PAS prise en charge.
    
    2.  Si vous avez sélectionné l’option d’authentification **Identité du service Azure AD** , procédez comme suit :
        1. Créez une application AAD et un principal du service qui peuvent accéder aux ressources Azure Data Lake.
    
        2. Affectez à cette application AAD les autorisations correspondantes pour accéder à vos ressources Azure Data Lake. Pour plus d’informations sur cette option d’authentification, consultez [Utiliser le portail pour créer une application Active Directory et un principal du service qui peuvent accéder aux ressources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Spécifiez des valeurs pour les champs **ID client**, **Clé secrète** et **Nom du locataire** .
    
        4. Cliquez sur le bouton **Tester la connexion** pour tester la connexion.  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
    Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .  
  
  
