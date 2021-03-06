---
title: Propriétés de Protocoles pour MSSQLSERVER (onglet Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 01/24/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: abd5ca68-825f-4c07-b27c-3b3a79d03d74
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: bc5ee796addb8c77170de2e3166aefb74d046ad1
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044615"
---
# <a name="protocols-for-mssqlserver-properties-advanced-tab"></a>Propriétés de Protocoles pour MSSQLSERVER (onglet Avancé)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Utilisez l'onglet **Avancé** dans la boîte de dialogue **Propriétés de Protocoles pour MSSQLSERVER** pour configurer la **protection étendue de l'authentification** du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. La**Protection étendue** est une fonctionnalité des composants réseau implémentée par le système d'exploitation. La**protection étendue** est disponible dans Windows 7 et Windows Server 2008 R2 et est incluse dans les Service Packs pour les précédents systèmes d'exploitation. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est plus sécurisé lorsque les connexions sont établies à l'aide de la **protection étendue**. Certains avantages de la **Protection étendue** requièrent de sélectionner l'option **Forcer le chiffrement** sous l'onglet **Indicateurs** .

> [!IMPORTANT]  
> Windows n'active pas la **protection étendue** par défaut. Pour plus d’informations sur l’activation **Protection étendue**, consultez les rubriques suivantes :
> - [La Protection étendue Windows \<extendedProtection\>](https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/windowsauthentication/extendedprotection/)
> - [Vue d’ensemble de la protection étendue de l'authentification](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/extended-protection-for-authentication-overview)

Pour plus d’informations sur la configuration d’autres services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et pour obtenir une description complète de la **protection étendue**, consultez les informations plus récentes sur [Microsoft.com](https://go.microsoft.com/fwlink/?LinkId=177752).

La**protection étendue** est totalement prise en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client à partir de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. La prise en charge de la **protection étendue** pour d'autres fournisseurs du client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est actuellement pas prise en charge.

## <a name="options"></a>Options

### <a name="extended-protection"></a>protection étendue

Il existe trois valeurs possibles :  

- **Off** : Signifie **Protection étendue** est désactivé. L'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] acceptera les connexions de tous les clients, qu'ils soient protégés ou non. La valeur**Off** est compatible avec les anciens systèmes d'exploitation non corrigés, mais elle est moins sécurisée. Utilisez ce paramètre uniquement lorsque vous savez que les systèmes d'exploitation clients ne prennent pas en charge la Protection étendue.

- **Autorisée** : la **protection étendue** est requise pour les connexions établies à partir de systèmes d'exploitation qui la prennent en charge**protection étendue**. Les connexions provenant d'applications clientes non protégées qui s'exécutent sur des systèmes d'exploitation clients protégés sont rejetées. La**Protection étendue** est ignorée pour les connexions provenant de systèmes d'exploitation non protégés. Ce paramètre offre une meilleure protection que la valeur **Off**, mais ce n'est pas la configuration la plus sécurisée. Utilisez ce paramètre dans des environnements mixtes, dans lesquels certains systèmes d'exploitation ou applications prennent en charge la **protection étendue** et d'autres non.

- **Requis**: signifie que pour une connexion soit acceptée, elle doit provenir d’une application protégée sur un système d’exploitation protégé. Ce paramètre est le plus sécurisé des trois options. Mais les connexions provenant des systèmes d’exploitation ne prenant pas en charge **Protection étendue** ne sera pas en mesure de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

### <a name="accepted-ntlm-spns"></a>SPN NTLM acceptés

Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être identifié par plusieurs NTLM nom principal de service (SPN). Vous répertoriez les noms SPN en tant que série de chaînes séparées par des points-virgules. Par exemple, la valeur **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com** indique que les clients qui essaient de se connecter au nom SPN **MSSQLSvc/HOST1.Contoso.com** ou **MSSQLSvc/HOST2.Contoso.com** sont autorisés. La variable a une longueur maximale de 2048 caractères.

## <a name="see-also"></a> Voir aussi

[Protection étendue de l'authentification avec Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)

