---
title: ELSE (IF... ELSE) (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ELSE
- ELSE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ELSE (IF...ELSE) keyword
- ELSE keyword
- IF keyword
ms.assetid: 6f2b4278-0dea-4603-bbd3-7cbad602a645
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 18adc4f441fddecdb3cd96c2a253268a16daea46
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="else-ifelse-transact-sql"></a>ELSE (IF...ELSE) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Impose les conditions d'exécution d'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. Le [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction (*sql_statement*) suivant le *Boolean_expression*est exécutée si la *Boolean_expression* a la valeur TRUE. Le mot clé facultatif ELSE est un autre [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction est exécutée lorsque *Boolean_expression* prend la valeur FALSE ou NULL.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IF Boolean_expression   
     { sql_statement | statement_block }   
[ ELSE   
     { sql_statement | statement_block } ]   
```  
  
## <a name="arguments"></a>Arguments  
 *Expression_booléenne*  
 Expression qui renvoie TRUE ou FALSE. Si le *Boolean_expression* contient une instruction SELECT, l’instruction SELECT doit être placée entre parenthèses.  
  
 { *sql_statement* | *statement_block* }  
 Toute instruction ou tout groupe d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] valide tel que défini dans un bloc d'instructions. Pour définir un bloc (traitement) d'instructions, utilisez les mots clé BEGIN et END du langage de contrôle de flux. Bien que tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions sont valides dans un BEGIN... FIN bloquer certains [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions ne doivent pas être regroupées dans le même lot (bloc d’instructions).  
  
## <a name="result-types"></a>Types des résultats  
 **Booléen**  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-a-simple-boolean-expression"></a>A. Utilisation d'une expression booléenne simple  
 L'exemple suivant comprend une expression booléenne simple (`1=1`) ayant la valeur true. Par conséquent, il imprime la première instruction.  
  
```  
IF 1 = 1 PRINT 'Boolean_expression is true.'  
ELSE PRINT 'Boolean_expression is false.' ;  
```  
  
 L'exemple suivant comprend une expression booléenne simple (`1=2`) ayant la valeur false. Par conséquent, il imprime la seconde instruction.  
  
```  
IF 1 = 2 PRINT 'Boolean_expression is true.'  
ELSE PRINT 'Boolean_expression is false.' ;  
GO  
```  
  
### <a name="b-using-a-query-as-part-of-a-boolean-expression"></a>B. Utilisation d'une requête dans le cadre d'une expression booléenne  
 L'exemple suivant exécute une requête dans le cadre de l'expression booléenne. Étant donné que 10 vélos de la table `Product` répondent à la clause `WHERE`, la première instruction print s'exécute. Remplacez `> 5` par `> 15` pour voir comment la deuxième partie de l'instruction pourrait s'exécuter.  
  
```  
USE AdventureWorks2012;  
GO  
IF   
(SELECT COUNT(*) FROM Production.Product WHERE Name LIKE 'Touring-3000%' ) > 5  
PRINT 'There are more than 5 Touring-3000 bicycles.'  
ELSE PRINT 'There are 5 or less Touring-3000 bicycles.' ;  
GO  
```  
  
### <a name="c-using-a-statement-block"></a>C. Utilisation d'un bloc d'instructions  
 L'exemple suivant exécute une requête dans le cadre de l'expression booléenne, puis exécute des blocs d'instructions légèrement différents selon le résultat de l'expression booléenne. Chaque bloc d'instructions commence par `BEGIN` et se termine par `END`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @AvgWeight decimal(8,2), @BikeCount int  
IF   
(SELECT COUNT(*) FROM Production.Product WHERE Name LIKE 'Touring-3000%' ) > 5  
BEGIN  
   SET @BikeCount =   
        (SELECT COUNT(*)   
         FROM Production.Product   
         WHERE Name LIKE 'Touring-3000%');  
   SET @AvgWeight =   
        (SELECT AVG(Weight)   
         FROM Production.Product   
         WHERE Name LIKE 'Touring-3000%');  
   PRINT 'There are ' + CAST(@BikeCount AS varchar(3)) + ' Touring-3000 bikes.'  
   PRINT 'The average weight of the top 5 Touring-3000 bikes is ' + CAST(@AvgWeight AS varchar(8)) + '.';  
END  
ELSE   
BEGIN  
SET @AvgWeight =   
        (SELECT AVG(Weight)  
         FROM Production.Product   
         WHERE Name LIKE 'Touring-3000%' );  
   PRINT 'Average weight of the Touring-3000 bikes is ' + CAST(@AvgWeight AS varchar(8)) + '.' ;  
END ;  
GO  
```  
  
### <a name="d-using-nested-ifelse-statements"></a>D. Utilisation d'instructions IF...ELSE imbriquées  
 L’exemple suivant montre comment une instruction IF... Instruction ELSE peut être imbriquée dans une autre. Définissez la variable `@Number` à `5`, `50` et `500` pour tester chaque instruction.  
  
```  
DECLARE @Number int;  
SET @Number = 50;  
IF @Number > 100  
   PRINT 'The number is large.';  
ELSE   
   BEGIN  
      IF @Number < 10  
      PRINT 'The number is small.';  
   ELSE  
      PRINT 'The number is medium.';  
   END ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-a-query-as-part-of-a-boolean-expression"></a>E : utilisation d’une requête en tant que partie d’une expression booléenne  
 L’exemple suivant utilise `IF…ELSE` pour déterminer lequel des deux réponses permettant à l’utilisateur, en fonction du poids d’un élément dans le `DimProduct` table.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @maxWeight float, @productKey integer  
SET @maxWeight = 100.00  
SET @productKey = 424  
IF @maxWeight <= (SELECT Weight from DimProduct WHERE ProductKey=@productKey)   
    (SELECT @productKey, EnglishDescription, Weight, 'This product is too heavy to ship and is only available for pickup.' FROM DimProduct WHERE ProductKey=@productKey)  
ELSE  
    (SELECT @productKey, EnglishDescription, Weight, 'This product is available for shipping or pickup.' FROM DimProduct WHERE ProductKey=@productKey)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Langage de contrôle de flux &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [IF...ELSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)  
  
  


