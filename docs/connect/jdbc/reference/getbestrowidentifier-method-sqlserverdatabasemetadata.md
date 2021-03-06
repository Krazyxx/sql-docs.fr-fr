---
title: Méthode getBestRowIdentifier (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getBestRowIdentifier
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c19e9ca6-2a53-4a0c-91ab-80090c3f7229
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 462de181aca55cce38d1e26f7932fe0003a0c323
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730319"
---
# <a name="getbestrowidentifier-method-sqlserverdatabasemetadata"></a>Méthode getBestRowIdentifier (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description du jeu optimal de colonnes d'une table qui identifie une ligne de façon unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getBestRowIdentifier(java.lang.String catalog,  
                                               java.lang.String schema,  
                                               java.lang.String table,  
                                               int scope,  
                                               boolean nullable)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 Un **chaîne** qui contient le nom du catalogue.  
  
 *schema*  
  
 **Chaîne** contenant le nom du schéma.  
  
 *table*  
  
 **Chaîne** qui contient le nom de la table.  
  
 *portée*  
  
 Un **int** qui indique la portée d’intérêt. Quelques valeurs possibles :  
  
 bestRowTemporary (0)  
  
 bestRowTransaction (1)  
  
 bestRowSession (2)  
  
 *nullable*  
  
 **true** pour inclure des colonnes de type nullable. Dans le cas contraire, la valeur est **false**.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getBestRowIdentifier est spécifiée par la méthode getBestRowIdentifier dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getBestRowIdentifier contient les informations suivantes :  
  
|Nom   |Type|Description|  
|----------|----------|-----------------|  
|SCOPE|short|Étendue des résultats retournés. Il peut avoir une des valeurs suivantes :<br /><br /> bestRowTemporary (0)<br /><br /> bestRowTransaction (1)<br /><br /> bestRowSession (2)|  
|COLUMN_NAME|String|Nom de la colonne.|  
|DATA_TYPE|short|Type de données SQL de java.sql.Types.|  
|TYPE_NAME|String|Nom du type de données.|  
|COLUMN_SIZE|INT|Précision de la colonne.|  
|BUFFER_LENGTH|INT|Longueur du tampon.|  
|DECIMAL_DIGITS|short|Échelle de la colonne.|  
|PSEUDO_COLUMN|short|Indique si la colonne est une pseudo-colonne. Il peut avoir une des valeurs suivantes :<br /><br /> bestRowUnknown (0)<br /><br /> bestRowNotPseudo (1)<br /><br /> bestRowPseudo (2)|  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser la méthode getBestRowIdentifier pour retourner des informations sur le meilleur identificateur de ligne pour la table Person.Contact dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetBestRowIdentifier(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getBestRowIdentifier(null, "Person", "Contact", 0, true);  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }  
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
