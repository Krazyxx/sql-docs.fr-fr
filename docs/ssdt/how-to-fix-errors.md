---
title: 'Procédure : résoudre les erreurs | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 0d504e00-4ff0-4fdf-b874-85280bbd8668
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6ef6cb6bce9173a849dbe406971028e3f452767c
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65090247"
---
# <a name="how-to-fix-errors"></a>Procédure : Corriger les erreurs
La volet Liste d'erreurs affiche toutes les erreurs de déploiement ou de build. Les erreurs de syntaxe et sémantique dues à la modification dans l'Éditeur Transact\-SQL ou dans le Concepteur de tables s'affichent aussi dans la liste lorsque vous modifiez des entités de base de données et leurs définitions. La Liste d'erreurs est mise à jour dynamiquement au fur et à mesure que vous modifiez des scripts dans les différents onglets. Vous pouvez ensuite suivre les erreurs identifiées pour la résolution des problèmes.  
  
> [!WARNING]  
> Les procédures suivantes utilisent les entités créées dans les procédures des sections [Développement de base de données connectée](../ssdt/connected-database-development.md) et [Développement de base de données hors connexion orienté projet](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-fix-errors"></a>Pour résoudre les erreurs  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur la table **Product** (Product.sql) et sélectionnez **Concepteur de vues**.  
  
2.  Dans la Grille Colonnes du concepteur, cliquez avec le bouton droit sur la colonne **ShelflLife** et sélectionnez **Supprimer** pour supprimer cette colonne de la table.  
  
3.  Notez que dans le volet **Liste d'erreurs** au bas de l'écran, un avertissement et une erreur similaires aux suivants s'affichent immédiatement.  
  
**Avertissement SQL71502 : Fonction : [dbo].[GetProductsBySupplier] contient une référence non résolue à un objet. Soit l’objet n’existe pas, soit la référence est ambiguë car elle peut désigner l’un des objets suivants : [dbo].[Product].[p]::[ShelfLife] ou [dbo].[Product].[ShelfLife].Erreur SQL71501 : Contrainte de validation : [dbo]. [CK_Product_ShelfLife] contient une référence non résolue à l’objet [dbo].[Product].[ShelfLife].**  
  
4.  Vous pouvez cliquer avec le bouton droit sur la **Liste d'erreurs** et utiliser les menus contextuels pour trier les résultats, filtrer les entrées à afficher, ainsi que les colonnes d'information à afficher pour chaque entrée.  
  
    Double-cliquez sur le premier avertissement identifié et accédez au fichier de script qui a généré l'avertissement. La section de code problématique est mise en surbrillance. Dans l’exemple, la colonne `ShelfLife` est utilisée par les instructions `RETURN` et `SELECT` dans une table créée précédemment.  
  
5.  Dans l'Éditeur Transact\-SQL, supprimez `ShelfLife` de la fonction.  
  
6.  Corrigez la deuxième erreur de manière similaire en supprimant la contrainte de validation.  
  
7.  Notez que l'avertissement et l'erreur disparaissent de la **Liste d'erreurs** immédiatement après la résolution des problèmes.  
  
## <a name="see-also"></a> Voir aussi  
[Utiliser l'Éditeur Transact-SQL pour modifier et exécuter des scripts](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md)  
  
