---
title: Méthode getVersionColumns (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getVersionColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6dd275d3-d9b2-4db7-938a-d4406c940a7a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 938cf980a4035684b2e77435d5ab4df9522b4407
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47604007"
---
# <a name="getversioncolumns-method-sqlserverdatabasemetadata"></a>Méthode getVersionColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des colonnes d'une table qui reflète automatiquement la mise à jour d'une valeur d'une ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getVersionColumns(java.lang.String catalog,  
                                            java.lang.String schema,  
                                            java.lang.String table)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 Un **chaîne** qui contient le nom du catalogue.  
  
 *schema*  
  
 **Chaîne** contenant le modèle de nom du schéma.  
  
 *table*  
  
 **Chaîne** qui contient le nom de la table.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getVersionColumns est spécifiée par la méthode getVersionColumns dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getVersionColumns contient les informations suivantes :  
  
|Nom   |Type|Description|  
|----------|----------|-----------------|  
|SCOPE|**short**|Non pris en charge par le pilote JDBC.|  
|COLUMN_NAME|**String**|Nom de la colonne.|  
|DATA_TYPE|**short**|Type de données SQL de java.sql.Types.|  
|TYPE_NAME|**String**|Nom du type de données.|  
|COLUMN_SIZE|**Int**|Précision de la colonne.|  
|BUFFER_LENGTH|**Int**|Longueur de la colonne en octets.|  
|DECIMAL_DIGITS|**short**|Échelle de la colonne.|  
|PSEUDO_COLUMN|**short**|Indique si la colonne est une pseudo-colonne. Il peut avoir une des valeurs suivantes :<br /><br /> versionColumnUnknown (0)<br /><br /> versionColumnNotPseudo (1)<br /><br /> versionColumnPseudo (2)|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getVersionColumns, consultez la rubrique « sp_datatype_info (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser la méthode getVersionColumns pour retourner des informations sur les colonnes qui sont mises à jour automatiquement dans la table Person.Contact de l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetVersionColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getVersionColumns("AdventureWorks", "Person", "Contact");  
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
  
  
