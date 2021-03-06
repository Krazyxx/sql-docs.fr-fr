---
title: référence de modèle d’application mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de modèle d’application mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0b4cbae0ba35c0cef777b3535b2012ab78f8e6da
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473438"
---
# <a name="mssqlctl-app-template"></a>Modèle d’application mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **modèle d’application** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[mssqlctl app template list](#mssqlctl-app-template-list) | Extraire des modèles pris en charge.
[mssqlctl app template pull](#mssqlctl-app-template-pull) | Téléchargez les modèles pris en charge.
## <a name="mssqlctl-app-template-list"></a>mssqlctl app template list
Extraire des modèles pris en charge dans le référentiel github [URL] spécifié.
```bash
mssqlctl app template list [--url -u] 
                           
```
### <a name="examples"></a>Exemples
Extraire tous les modèles sous l’emplacement de dépôt de modèle par défaut.
```bash
mssqlctl app template list
```
Extraire tous les modèles dans un emplacement autre dépôt.
```bash
mssqlctl app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--url -u`
Spécifiez un emplacement de dépôt de modèle différent. Par défaut : https://github.com/Microsoft/SQLBDC-AppDeploy.git
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de journalisation pour afficher que tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et de sortie.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de journalisation. Utilisez--debug pour les journaux de débogage complets.
## <a name="mssqlctl-app-template-pull"></a>mssqlctl app template pull
Téléchargez les modèles pris en charge dans le référentiel github [URL] spécifié.
```bash
mssqlctl app template pull [--name -n] 
                           [--url -u]  
                           [--destination -d]
```
### <a name="examples"></a>Exemples
Télécharger tous les modèles sous l’emplacement de dépôt de modèle par défaut.
```bash
mssqlctl app template pull
```
Télécharger tous les modèles dans un emplacement autre dépôt.
```bash
mssqlctl app template list --url https://github.com/diffrent/templates.git
```
Téléchargez le modèle individuel par nom.
```bash
mssqlctl app template pull --name ssis            
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom du modèle. Pour obtenir une liste complète de namesrun de modèle pris en charge `mssqlctl app template list`
#### `--url -u`
Spécifiez un emplacement de dépôt de modèle différent. Par défaut : https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Où placer le modèle d’application squelette.
`./templates`
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de journalisation pour afficher que tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et de sortie.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de journalisation. Utilisez--debug pour les journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).