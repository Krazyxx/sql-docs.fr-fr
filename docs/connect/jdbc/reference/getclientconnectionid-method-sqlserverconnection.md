---
title: getclientconnectionid, méthode (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bee39c11-733a-461f-92cc-33efcb2af87d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb6e81dc3968677571fea444fc83a4b999a74b5c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52544372"
---
# <a name="getclientconnectionid-method-sqlserverconnection"></a>getClientConnectionID, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtient l'ID de la tentative de connexion la plus récente, que cette tentative ait réussi ou non.  
  
## <a name="syntax"></a>Syntaxe  
  
``` 
public Java.util.UUID SQLServerConnection.getClientConnectionID();  
```  
  
## <a name="return-value"></a>Valeur retournée  
 GUID de 16 octets représentant l'ID de connexion de la dernière tentative de connexion. Ou NULL, s'il y a un échec après le lancement de la demande de connexion et après la négociation de préconnexion.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Pour plus d’informations sur l’accès aux informations de diagnostic dans le journal des événements étendus, consultez [l’accès à des informations de Diagnostic dans le journal des événements étendus](../../../connect/jdbc/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
 L'exemple suivant montre comment obtenir l'ID de connexion :  
  
```  
Connection con = DriverManager.getConnection(connectionUrl);  
UUID id = ((ISQLServerConnection)con).getClientConnectionId();  
```  
  
 L'exemple suivant montre une autre façon d'obtenir l'ID de connexion :  
  
```  
SQLServerConnectionPoolDataSource ds = new SQLServerConnectionPoolDataSource();  
ds.setUser("...");  
ds.setPassword("...");  
ds.setServerName("...");  
PooledConnection pcon= ds.getPooledConnection();  
Connection cn = pcon.getConnection();  
UUID conid = ((ISQLServerConnection)cn).getClientConnectionId();  
```  
  
 **getClientConnectionID** fonctionne quel que soit la version du serveur que vous vous connectez à, mais les journaux des événements étendus et écriture sur les erreurs de mémoire tampon en anneau de connectivité ne seront pas présents dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2008 R2 et versions antérieures.  
  
 Vous pouvez également localiser l'ID de connexion dans le journal des événements étendus si l'échec concerne le serveur et si l'événement étendu permet l'enregistrement de l'ID de connexion. Vous pouvez également trouver l’ID de connexion dans la mémoire tampon de l’anneau de connectivité ([Résolution des problèmes de connectivité dans SQL Server 2008 avec la mémoire tampon de l’anneau de connectivité](https://go.microsoft.com/fwlink/?LinkId=207752)) pour certaines erreurs de connexion. Si l'ID de connexion n'est pas dans la mémoire tampon de l'anneau de connexion, vous pouvez supposer qu'il s'agit d'une erreur réseau.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
