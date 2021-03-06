---
title: 'Procédure : ajouter des conditions de test à des tests unitaires SQL Server | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 85ba2e56-a0b2-489c-aea2-fb135cce0cfc
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3f4dc9a023b74c104e232546ec6c4f8c2bd93919
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65103245"
---
# <a name="how-to-add-test-conditions-to-sql-server-unit-tests"></a>Procédure : Ajouter des conditions de test à des tests unitaires SQL Server
Ajoutez d'autres conditions de test à un test unitaire SQL Server à l'aide du **Concepteur de test unitaire SQL Server**. Lorsque vous enregistrez la classe de test, les conditions de test sont automatiquement enregistrées dans votre projet de test en tant que code Visual C\# ou Visual Basic dans le fichier de code source contenant la classe de test. Après avoir enregistré une condition de test, modifiez-la dans le **Concepteur de test unitaire SQL Server** ou dans son fichier de code source.  
  
### <a name="to-add-test-conditions-to-a-sql-server-unit-test"></a>Pour ajouter des conditions de test à un test unitaire SQL Server  
  
1.  Ouvrez un test unitaire SQL Server dans le **Concepteur de test unitaire SQL Server**.  
  
    Le nom du test que vous avez ouvert s'affiche dans la barre de navigation située en haut du Concepteur de test unitaire SQL Server. À l'aide de la barre de navigation, sélectionnez les différentes méthodes de test qui figurent dans la classe de test.  
  
2.  Dans la barre de navigation, cliquez sur la méthode de test à laquelle vous souhaitez ajouter des conditions de test ou cliquez sur **Scripts courants**.  
  
    > [!NOTE]  
    > Les scripts courants n'appartiennent pas à un test unitaire particulier. En revanche, ils précèdent et suivent les tests unitaires dans la classe de test. Pour plus d'informations, consultez [Scripts des tests unitaires SQL Server](../ssdt/scripts-in-sql-server-unit-tests.md).  
  
3.  Dans la barre de navigation, cliquez sur le script Transact\-SQL auquel vous souhaitez ajouter des conditions de test. Ajoutez des conditions de test au script de prétest, de test ou de post-test.  
  
    Le script Transact\-SQL pour ce test apparaît dans l'éditeur Transact\-SQL et ses conditions de test s'affichent dans le volet **Conditions de test**.  
  
4.  Dans la liste de sélection **Conditions de test**, cliquez sur une condition de test, puis cliquez sur **Ajouter une condition de test** (+).  
  
    La condition de test est ajoutée à la méthode de test unitaire.  
  
    > [!NOTE]  
    > Pour réorganiser les conditions de test dans une méthode de test, cliquez sur une condition de test, puis cliquez sur les flèches haut et bas dans le volet **Conditions de test**.  
  
5.  Sélectionnez la condition de test que vous venez d'ajouter et affichez la fenêtre **Propriétés**.  
  
    Configurez la condition de test dans la fenêtre Propriétés. Par exemple, modifiez la propriété **Durée d'exécution** d'une condition de test Durée d'exécution. Si vous définissez cette propriété, vous provoquez l'échec du test si le script Transact\-SQL ne s'exécute pas dans le laps de temps spécifié.  
  
## <a name="see-also"></a> Voir aussi  
[Création et définition de tests unitaires SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Procédure : créer un test unitaire SQL Server vide](../ssdt/how-to-create-an-empty-sql-server-unit-test.md)  
[Procédure : créer des tests unitaires SQL Server pour des fonctions, des déclencheurs ou des procédures stockées](../ssdt/how-to-create-unit-tests-for-functions-triggers-stored-procedures.md)  
[Utilisation de conditions de test dans les tests unitaires SQL Server](../ssdt/using-test-conditions-in-sql-server-unit-tests.md)  
[Scripts des tests unitaires SQL Server](../ssdt/scripts-in-sql-server-unit-tests.md)  
[Interprétation des résultats des tests unitaires SQL Server](../ssdt/interpreting-sql-server-unit-test-results.md)  
[Procédure : exécuter des tests unitaires SQL Server](../ssdt/how-to-run-sql-server-unit-tests.md)  
  
