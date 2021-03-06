---
title: 'Tutoriel : Bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS | Microsoft Docs'
ms.custom: ''
ms.date: 04/05/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 051123efd5c58048635bb83e43eaff73218c463e
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59241537"
---
# <a name="tutorial-getting-started-with-always-encrypted-with-secure-enclaves-using-ssms"></a>Tutoriel : Bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce tutoriel vous apprend à bien démarrer avec [Always Encrypted avec enclaves sécurisées](encryption/always-encrypted-enclaves.md). Il vous montre comment :
- Créer un environnement de base pour tester et évaluer Always Encrypted avec enclaves sécurisées.
- Chiffrer des données sur place et émettre des requêtes complexes sur des colonnes chiffrées en utilisant SQL Server Management Studio (SSMS).

## <a name="prerequisites"></a>Conditions préalables requises

Pour bien démarrer avec Always Encrypted avec enclaves sécurisées, vous avez besoin d’au moins deux ordinateurs (qui peuvent être des machines virtuelles) :

- L’ordinateur SQL Server pour héberger SQL Server et SSMS.
- L’ordinateur SGH pour exécuter le Service Guardian hôte, qui est nécessaire pour l’attestation d’enclave.

### <a name="sql-server-computer-requirements"></a>Configuration requise de l’ordinateur SQL Server

- [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] ou version ultérieure.
- Windows 10 Entreprise version 1809 ou Windows Server 2019 Datacenter.
- Si votre ordinateur SQL Server est une machine physique, il doit respecter la [Configuration matérielle Hyper-V requise](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/reference/hyper-v-requirements#hardware-requirements) :
   - Processeur 64 bits avec traduction d’adresses de deuxième niveau (SLAT)
   - Prise en charge du processeur pour l’extension Mode moniteur de machine virtuelle (VT-c sur processeurs Intel)
   - Prise en charge de la virtualisation activée (Intel VT-x ou AMD-V)
- Si votre ordinateur SQL Server est une machine virtuelle, il doit être configuré de façon à autoriser la virtualisation imbriquée.
   - Sur Hyper-V 2016 et les versions ultérieures, [activez les extensions de virtualisation imbriquée](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/user-guide/nested-virtualization#configure-nested-virtualization) sur le processeur de la machine virtuelle.
   - Dans Azure, vérifiez que vous utilisez une taille de machine virtuelle qui prend en charge la virtualisation imbriquée, comme les machines virtuelles des séries Dv3 et Ev3. Voir [Créer une machine virtuelle Azure compatible avec l’imbrication](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/nested-virtualization#create-a-nesting-capable-azure-vm).
   - Sur VMware vSphere 6.7 et les versions ultérieures, activez la prise en charge de la sécurité basée sur la virtualisation pour la machine virtuelle, comme le décrit la [documentation VMware](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-C2E78F3E-9DE2-44DB-9B0A-11440800AADD.html).
   - D’autres hyperviseurs et clouds publics peuvent prendre en charge la virtualisation à l’aide d’Always Encrypted avec des enclaves sécurisées dans une machine virtuelle tant que les extensions de virtualisation (parfois appelées virtualisation imbriquée) sont exposées à la machine virtuelle. Consultez la documentation de votre solution de virtualisation, qui contient des instructions relatives à la compatibilité et à la configuration.
- [SQL Server Management Studio (SSMS) version 18.0 ou ultérieure](../../ssms/download-sql-server-management-studio-ssms.md).

Vous pouvez aussi installer SSMS sur un autre ordinateur.

>[!WARNING] 
>Dans les environnements de production, vous ne devez jamais utiliser SSMS ou d’autres outils pour gérer les clés Always Encrypted ni exécuter des requêtes sur des données chiffrées sur l’ordinateur SQL Server, au risque d’atténuer voire de neutraliser complètement l’intérêt d’utiliser Always Encrypted.

### <a name="hgs-computer-requirements"></a>Configuration requise de l’ordinateur SGH

- Windows Server 2019 Édition Standard ou Datacenter
- 2 UC
- 8 Go de RAM
- Stockage de 100 Go

>[!NOTE]
>L’ordinateur SGH ne doit pas être joint à un domaine avant de commencer.

## <a name="step-1-configure-the-hgs-computer"></a>Étape 1 : Configurer l’ordinateur SGH

Dans cette étape, vous allez configurer l’ordinateur SGH pour exécuter le Service Guardian hôte qui prend en charge l’attestation de clé d’hôte.

1. Connectez-vous à l’ordinateur SGH en tant qu’administrateur (administrateur local), ouvrez une console Windows PowerShell avec élévation de privilèges et ajoutez le rôle de Service Guardian hôte en exécutant la commande suivante :

   ```powershell
   Install-WindowsFeature -Name HostGuardianServiceRole -IncludeManagementTools -Restart
   ```

2. Une fois que l’ordinateur SGH a redémarré, reconnectez-vous avec votre compte d’administrateur, ouvrez une console Windows PowerShell avec élévation de privilèges, puis exécutez les commandes suivantes pour installer le Service Guardian hôte et configurer son domaine. Le mot de passe que vous spécifiez ici s’applique uniquement au mode de réparation des services d’annuaire pour Active Directory ; il ne modifie pas le mot de passe de connexion de votre compte d’administrateur. Vous pouvez spécifier le nom de domaine de votre choix pour - HgsDomainName.

   ```powershell
   $adminPassword = ConvertTo-SecureString -AsPlainText '<password>' -Force
   Install-HgsServer -HgsDomainName 'bastion.local' -SafeModeAdministratorPassword $adminPassword -Restart
   ```

3. Une fois que l’ordinateur a de nouveau redémarré, connectez-vous avec votre compte d’administrateur (qui est aussi désormais administrateur de domaine), ouvrez une console Windows PowerShell avec élévation de privilèges et configurez l’attestation de clé d’hôte pour votre instance SGH. 

   ```powershell
   Initialize-HgsAttestation -HgsServiceName 'hgs' -TrustHostKey  
   ```

4. Recherchez l’adresse IP de l’ordinateur SGH en exécutant la commande suivante. Enregistrez cette adresse IP pour les étapes suivantes.

   ```powershell
   Get-NetIPAddress  
   ```

>[!NOTE]
>Sinon, si vous préférez référencer votre ordinateur SGH avec un nom DNS, vous pouvez configurer un redirecteur sur les serveurs DNS de votre entreprise vers le nouveau contrôleur de domaine SGH.  

## <a name="step-2-configure-the-sql-server-computer-as-a-guarded-host"></a>Étape 2 : Configurer l’ordinateur SQL Server comme hôte Service Guardian
Dans cette étape, vous allez configurer l’ordinateur SQL Server comme hôte Service Guardian inscrit auprès de SGH à l’aide de l’attestation de clé d’hôte.
>[!NOTE]
>L’utilisation de l’attestation de clé d’hôte n’est recommandée que dans les environnements de test. Pour les environnements de production, vous devez utiliser l’attestation du module de plateforme sécurisée (TPM).

1. Connectez-vous à votre ordinateur SQL Server en tant qu’administrateur, ouvrez une console Windows PowerShell avec élévation de privilèges et récupérez le nom de votre ordinateur en accédant à la variable computername.

   ```powershell
   $env:computername 
   ```

2. Installez la fonctionnalité de l’hôte Service Guardian, qui va également installer Hyper-V (si ce n’est pas déjà fait).

   ```powershell
   Enable-WindowsOptionalFeature -Online -FeatureName HostGuardian -All
   ```

3. Quand vous y êtes invité, redémarrez votre ordinateur SQL Server pour terminer l’installation d’Hyper-V.

4. Si votre ordinateur SQL Server est une machine virtuelle, ou bien une machine physique ancienne génération qui ne prend pas en charge le démarrage sécurisé UEFI ou n’est pas équipée d’IOMMU, vous devez supprimer la condition VBS pour les fonctionnalités de sécurité de la plateforme.
    1. Supprimez la condition dans le Registre Windows.

        ```powershell
       Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Control\DeviceGuard -Name RequirePlatformSecurityFeatures -Value 0
       ```

    1. Redémarrez l’ordinateur pour que VBS présente les conditions réduites en ligne.

        ```powershell
       Restart-Computer
       ```



4. Reconnectez-vous à l’ordinateur SQL Server en tant qu’administrateur, ouvrez une console Windows PowerShell avec élévation de privilèges, générez une clé d’hôte unique, puis exportez la clé publique qui en résulte dans un fichier.

   ```powershell
   Set-HgsClientHostKey 
   Get-HgsClientHostKey -Path $HOME\Desktop\hostkey.cer
   ```

5. Copiez manuellement le fichier de clé d’hôte généré à l’étape précédente sur l’ordinateur SGH. Les instructions ci-dessous considèrent que votre nom de fichier est hostkey.cer et que vous l’avez copié sur le bureau de l’ordinateur SGH.

6. Sur l’ordinateur SGH, ouvrez une console Windows PowerShell avec élévation de privilèges et inscrivez la clé d’hôte de votre ordinateur SQL Server auprès de SGH :

   ```powershell
   Add-HgsAttestationHostKey -Name <your SQL Server computer name> -Path $HOME\Desktop\hostkey.cer
   ```

7. Sur l’ordinateur SQL Server, exécutez la commande suivante dans une console Windows PowerShell avec élévation de privilèges pour indiquer à l’ordinateur SQL Server où attester. Veillez à spécifier l’adresse IP ou le nom DNS de votre ordinateur SGH aux deux emplacements d’adresse. 

   ```powershell
   # use http, and not https
   Set-HgsClientConfiguration -AttestationServerUrl http://<IP address or DNS name>/Attestation -KeyProtectionServerUrl http://<IP address or DNS name>/KeyProtection/  
   ```

Le résultat de la commande ci-dessus doit indiquer AttestationStatus = Passed.

Si vous obtenez l’erreur HostUnreachable, cela signifie que votre ordinateur SQL Server ne peut pas communiquer avec SGH. Vérifiez que vous pouvez effectuer un test ping sur l’ordinateur SGH.

L’erreur UnauthorizedHost indique que la clé publique n’a pas été inscrite sur le serveur SGH. Répétez les étapes 5 et 6 pour résoudre l’erreur.

Si le problème persiste, exécutez Clear-HgsClientHostKey et répétez les étapes 4 à 7.

## <a name="step-3-enable-always-encrypted-with-secure-enclaves-in-sql-server"></a>Étape 3 : Activer Always Encrypted avec enclaves sécurisées dans SQL Server

Dans cette étape, vous allez activer la fonctionnalité Always Encrypted avec enclaves dans votre instance SQL Server.

1. Ouvrez SSMS, connectez-vous à votre instance SQL Server en tant que sysadmin et ouvrez une nouvelle fenêtre de requête.
2. Définissez le type d’enclave sécurisée sur la sécurité basée sur la virtualisation (VBS).

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1;
   RECONFIGURE;
   ```

3. Redémarrez votre instance SQL Server pour que la modification précédente prenne effet. Vous pouvez redémarrer l’instance dans SSMS en cliquant dessus avec le bouton droit dans l’Explorateur d’objets et en sélectionnant Redémarrer. Une fois que l’instance a redémarré, connectez-vous à nouveau.

4. Vérifiez que l’enclave sécurisée est maintenant chargée en exécutant la requête suivante :

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type';
   ```

    La requête doit retourner le résultat suivant :  

    | NAME                           | valeur | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | column encryption enclave type | 1     | 1              |

5. Pour activer les calculs complexes dans les colonnes chiffrées, exécutez la requête suivante :

   ```sql
   DBCC traceon(127,-1);
   ```

    > [!NOTE]
    > Les calculs complexes sont désactivés par défaut dans [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)]. Ils doivent être activés à l’aide de l’instruction ci-dessus après chaque redémarrage de votre instance SQL Server.

## <a name="step-4-create-a-sample-database"></a>Étape 4 : Créer un exemple de base de données
Dans cette étape, vous allez créer une base de données avec des exemples de données, qui vous chiffrerez par la suite.

1. Connectez-vous à votre instance SQL Server à l’aide de SSMS.
2. Créez une base de données sous le nom ContosoHR.

    ```sql
    CREATE DATABASE [ContosoHR];
    ```

3. Vérifiez que vous êtes bien connecté à la base de données nouvellement créée. Créez une table nommée Employees.

    ```sql
    USE [ContosoHR];
    GO
    
    CREATE TABLE [dbo].[Employees]
    (
        [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
        [SSN] [char](11) NOT NULL,
        [FirstName] [nvarchar](50) NOT NULL,
        [LastName] [nvarchar](50) NOT NULL,
        [Salary] [money] NOT NULL
    ) ON [PRIMARY];
    ```

4. Ajoutez quelques enregistrements d’employés à la table Employees.

    ```sql
    INSERT INTO [dbo].[Employees]
            ([SSN]
            ,[FirstName]
            ,[LastName]
            ,[Salary])
        VALUES
            ('795-73-9838'
            , N'Catherine'
            , N'Abel'
            , $31692);
 
    INSERT INTO [dbo].[Employees]
            ([SSN]
            ,[FirstName]
            ,[LastName]
            ,[Salary])
        VALUES
            ('990-00-6818'
            , N'Kim'
            , N'Abercrombie'
            , $55415);
    ```

## <a name="step-5-provision-enclave-enabled-keys"></a>Étape 5 : Approvisionner des clés prenant en charge les enclaves

Dans cette étape, vous allez créer une clé principale de colonne et une clé de chiffrement de colonne qui permettent les calculs d’enclave.

1. Connectez-vous à votre base de données à l’aide de SSMS.
2. Dans l’**Explorateur d’objets**, développez votre base de données et accédez à **Sécurité** > **Clés Always Encrypted**.
3. Provisionnez une nouvelle clé principale de colonne prenant en charge les enclaves :
    1. Cliquez avec le bouton droit sur **Clés Always Encrypted** et sélectionnez **Nouvelle clé principale de colonne...**.
    2. Sélectionnez le nom de votre clé principale de colonne : CMK1.
    3. Veillez à sélectionnez **Magasin de certificats Windows (utilisateur actuel ou ordinateur local)** ou **Azure Key Vault**.
    4. Sélectionnez **Autoriser les calculs d’enclave**.
    5. Si vous avez sélectionné Azure Key Vault, connectez-vous à Azure et sélectionnez votre coffre de clés. Pour plus d’informations sur la création d’un coffre de clés pour Always Encrypted, consultez [Gérer vos coffres de clés à partir du portail Azure](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/).
    6. Sélectionnez votre certificat ou votre clé Valeur de clé Azure, ou cliquez sur le bouton **Générer un certificat** pour en créer.
    7. Sélectionnez **OK**.

        ![Autoriser les calculs d’enclave](encryption/media/always-encrypted-enclaves/allow-enclave-computations.png)
    
4. Créez une clé de chiffrement de colonne prenant en charge les enclaves :

    1. Cliquez avec le bouton droit sur **Clés Always Encrypted** et sélectionnez **Nouvelle clé de chiffrement de colonne**.
    2. Entrez un nom pour la nouvelle clé de chiffrement de colonne : CEK1.
    3. Dans le menu déroulant **Clé principale de colonne**, sélectionnez la clé principale de colonne que vous avez créée aux étapes précédentes.
    4. Sélectionnez **OK**.

## <a name="step-6-encrypt-some-columns-in-place"></a>Étape 6 : Chiffrer des colonnes sur place

Dans cette étape, vous allez chiffrer les données stockées dans les colonnes SSN et Salary à l’intérieur de l’enclave côté serveur, puis vous testerez ensuite une requête SELECT sur les données.

1. Dans SSMS, configurez une nouvelle fenêtre de requête en activant Always Encrypted pour la connexion de base de données.
    1. Dans SSMS, ouvrez une nouvelle fenêtre de requête.
    2. Cliquez avec le bouton droit n’importe où dans la nouvelle fenêtre de requête.
    3. Sélectionnez Connexion \> Changer la connexion.
    4. Sélectionnez **Options**. Accédez à l’onglet **Always Encrypted**, sélectionnez **Activer Always Encrypted**, puis spécifiez l’URL d’attestation d’enclave (par exemple, <span>http://</span>hgs.bastion.local/Attestation).
    5. Sélectionnez **Se connecter**.
    6. S’il vous est demandé d’activer le paramétrage des requêtes Always Encrypted, cliquez sur **Activer**.
2. Dans SSMS, configurez une autre fenêtre de requête en désactivant Always Encrypted pour la connexion de base de données.
    1. Dans SSMS, ouvrez une nouvelle fenêtre de requête.
    2. Cliquez avec le bouton droit n’importe où dans la nouvelle fenêtre de requête.
    3. Sélectionnez Connexion \> Changer la connexion.
    4. Sélectionnez **Options**. Accédez à l’onglet **Always Encrypted**, vérifiez que **Activer Always Encrypted** n’est pas sélectionné.
    5. Sélectionnez **Se connecter**.
    6. Changez le contexte de base de données en spécifiant la base de données ContosoHR.
1. Chiffrez les colonnes SSN et Salary. Dans la fenêtre de requête avec Always Encrypted activé, collez et exécutez le script ci-dessous :

    ```sql
    ALTER TABLE [dbo].[Employees]
    ALTER COLUMN [SSN] [char] (11) COLLATE Latin1_General_BIN2
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
    WITH
    (ONLINE = ON);
     
    ALTER TABLE [dbo].[Employees]
    ALTER COLUMN [Salary] [money]
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
    WITH
    (ONLINE = ON);
 
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```
    > [!NOTE]
    > Notez l’instruction ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE destinée à effacer le cache du plan de requête de la base de données dans le script ci-dessus. Une fois que vous avez modifié la table, vous devez effacer les plans pour l’ensemble des lots et des procédures stockées qui accèdent à la table, afin d’actualiser les informations de chiffrement des paramètres. 

4. Pour vérifier que les colonnes SSN et Salary sont maintenant chiffrées, collez et exécutez l’instruction ci-dessous dans la fenêtre de requête avec Always Encrypted désactivé. La fenêtre de requête doit retourner des valeurs chiffrées dans les colonnes SSN et Salary. Dans la fenêtre de requête avec Always Encrypted activé, essayez d’exécuter la même requête pour afficher les données déchiffrées.

    ```sql
    SELECT * FROM [dbo].[Employees];
    ```

## <a name="step-7-run-rich-queries-against-encrypted-columns"></a>Étape 7 : Exécuter des requêtes complexes sur les colonnes chiffrées

À présent, vous pouvez exécuter des requêtes complexes sur les colonnes chiffrées. Un traitement de requête se produit à l’intérieur de votre enclave côté serveur. 

1. Vérifiez que le paramétrage Always Encrypted est activé.
    1. Sélectionnez **Requête** dans le menu principal de SSMS.
    2. Sélectionnez **Options de requête…**.
    3. Accédez à **Exécution** > **Avancé**.
    4. Vérifiez que la case Activer le paramétrage Always Encrypted est cochée.
    5. Sélectionnez OK.
2. Dans la fenêtre de requête avec Always Encrypted activé, collez et exécutez la requête ci-dessous. La requête doit retourner des valeurs de texte en clair et des lignes correspondant aux critères de recherche spécifiés.

    ```sql
    DECLARE @SSNPattern [char](11) = '%6818';
    DECLARE @MinSalary [money] = $1000;
    SELECT * FROM [dbo].[Employees]
    WHERE SSN LIKE @SSNPattern AND [Salary] >= @MinSalary;
    ```
3. Essayez à nouveau la même requête dans la fenêtre de requête où Always Encrypted n’est pas activé et notez qu’elle échoue.

## <a name="next-steps"></a>Next Steps
Consultez [Configurer Always Encrypted avec enclaves sécurisées](encryption/configure-always-encrypted-enclaves.md) pour voir d’autres cas d’utilisation. Vous pouvez aussi essayer ce qui suit :

- [Configurer l’attestation TPM.](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode)
- [Configurer HTTPS pour votre instance SGH.](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-https)
- Développer des applications qui émettent des requêtes complexes sur des colonnes chiffrées.
