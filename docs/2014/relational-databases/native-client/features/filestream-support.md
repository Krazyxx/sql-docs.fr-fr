---
title: Prise en charge FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33e447048f7058ee81b0b144f0aa94a370f6d670
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046261"
---
# <a name="filestream-support"></a>Prise en charge de FILESTREAM
  FILESTREAM permet de stocker et d'accéder à de grandes valeurs binaires, soit par le biais de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], soit par accès direct au système de fichiers Windows. Une grande valeur binaire est une valeur supérieure à 2 gigaoctets (Go). Pour plus d’informations sur la prise en charge améliorée de FILESTREAM, consultez [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md).  
  
 Lorsqu'une connexion de base de données est ouverte, la valeur -1 (« illimité ») est affectée par défaut à `@@TEXTSIZE`.  
  
 Il est également possible d'accéder et de mettre à jour des colonnes FILESTREAM à l'aide d'API de système de fichiers Windows.  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Prise en charge FILESTREAM &#40;OLE DB&#41;](../ole-db/filestream-support-ole-db.md)  
  
-   [Prise en charge FILESTREAM &#40;ODBC&#41;](../odbc/filestream-support-odbc.md)  
  
-   [Accéder à des données FILESTREAM avec OpenSqlFilestream](../../blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Interrogation de colonnes FILESTREAM  
 Les ensembles de lignes de schéma dans OLE DB ne signalent pas si une colonne est une colonne FILESTREAM. ITableDefinition dans OLE DB ne peut pas être utilisé pour créer une colonne FILESTREAM.  
  
 Fonctions de catalogue, telles que SQLColumns dans ODBC ne signalent pas de si une colonne est une colonne FILESTREAM.  
  
 Pour créer des colonnes FILESTREAM ou détecter les colonnes existantes sont des colonnes FILESTREAM, vous pouvez utiliser la `is_filestream` colonne de la [sys.columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) vue de catalogue.  
  
 Par exemple :  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Compatibilité de bas niveau  
 Si votre client a été compilé à l’aide de la version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client fournie avec [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)], `varbinary(max)` comportement seront compatible avec [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Autrement dit, la taille maximale des données retournées est limitée à 2 Go. Pour les valeurs de résultat supérieures à 2 Go, une troncation se produit et un avertissement « Troncation à droite de la chaîne de données » est retourné.  
  
 Lorsque la compatibilité de type de données est définie à 80, le comportement client est cohérent avec le comportement client de bas niveau.  
  
 Pour les clients qui utilisent SQLOLEDB ou autres fournisseurs qui ont été publiées avant la [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] Native Client, `varbinary(max)` sera mappé à l’image.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)  
  
  
