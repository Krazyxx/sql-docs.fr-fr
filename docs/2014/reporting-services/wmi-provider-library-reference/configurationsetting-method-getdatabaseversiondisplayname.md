---
title: GetDatabaseVersionDisplayName, méthode (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05f7e8818f5300ee1c7e391ad1345b696eb08154
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62647113"
---
# <a name="getdatabaseversiondisplayname-method-wmi"></a>Méthode GetDatabaseVersionDisplayName (WMI)
  Obtient le nom complet de la chaîne de version d'une base de données de serveur de rapports spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Version*  
 Chaîne qui contient la chaîne de version d'une base de données de serveur de rapports.  
  
 *DisplayName*  
 [out] Chaîne qui contient le nom complet correspondant à la version fournie.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant indique la correspondance entre la version de la base de données et la chaîne d'affichage.  
  
|**Release**|`Version`|**Nom complet**|  
|-----------------|-----------------|----------------------|  
|RS 2005 SP2|@DBVersion = 'C.0.8.54'|SQL Server 2005 SP2|  
|RS 2005 SP1|@DBVersion = 'C.0.8.43'|SQL Server 2005 SP1|  
|RS 2005 RTM|@DBVersion = 'C.0.8.40'|SQL Server 2005|  
|RS 2000 SP2|@DBVersion = 'C.0.6.54'|SQL Server 2000 SP2|  
|RS 2000 SP1|@DBVersion = 'C.0.6.51'|SQL Server 2000 SP1|  
|RS 2000 RTM|@DBVersion = 'C.0.6.43'|SQL Server 2000|  
|Correctif logiciel||Version applicable la plus proche|  
  
 Pour une *Version* antérieure à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000, le paramètre HRESULT ACT_E_BAD_VERSION est retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="requirements"></a>Configuration requise  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
