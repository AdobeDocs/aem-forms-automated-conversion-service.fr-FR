---
title: Envoyer des formulaires adaptatifs à la base de données à l’aide du portail Formulaires
description: Étendez le métamodèle par défaut pour ajouter un modèle, des validations et des entités spécifiques à votre organisation et appliquer des configurations aux champs de formulaire adaptatif lors de l’exécution de Automated Forms Conversion service (AFCS).
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '1221'
ht-degree: 100%

---


# Intégrer des formulaires adaptatifs à une base de données à l’aide du portail Formulaires {#submit-forms-to-database-using-forms-portal}

Automated Forms Conversion service (AFCS) vous permet de convertir un formulaire PDF non interactif, un formulaire Acro ou un formulaire PDF basé sur XFA en un formulaire adaptatif. Lors du lancement du processus de conversion, vous avez la possibilité de générer un formulaire adaptatif avec ou sans liaison de données.

Si vous choisissez de générer un formulaire adaptatif sans liaison de données, vous pouvez incorporer le formulaire adaptatif converti à un modèle de données de formulaire, un schéma XML ou un schéma JSON après la conversion. Toutefois, si vous générez un formulaire adaptatif avec des liaisons de données, le service de conversion associe automatiquement les formulaires adaptatifs à un schéma JSON et crée une liaison de données entre les champs disponibles dans le formulaire adaptatif et le schéma JSON. Vous pouvez ensuite intégrer le formulaire adaptatif à une base de données de votre choix, remplir les données du formulaire et les envoyer à la base de données à l’aide du portail Forms.

Le schéma suivant illustre différentes étapes de l’intégration d’un formulaire adaptatif converti à une base de données à l’aide du portail Forms :

![intégration à une base de données](assets/database_integration.gif)

Cet article décrit les instructions détaillées pour réussir à exécuter toutes ces étapes d’intégration.

L’exemple présenté dans cet article est une implémentation de référence des services de données et de métadonnées personnalisés pour intégrer une page Portail Forms à une base de données. La base de données utilisée dans l’exemple d’implémentation est MySQL 5.6.24. Cependant, vous pouvez intégrer la page Portail Forms à n’importe quelle base de données de votre choix.

## Prérequis {#pre-requisites}

* Configuration d’une instance d’auteur AEM 6.4 ou 6.5
* Installation du [dernier Service Pack](https://helpx.adobe.com/fr/experience-manager/aem-releases-updates.html) pour votre instance AEM
* Dernière version du package de module complémentaire AEM Forms
* Configurer [Automated Forms Conversion service (AFCS)](configure-service.md)
* Configuration d’une base de données. La base de données utilisée dans l’exemple d’implémentation est MySQL 5.6.24. Cependant, vous pouvez intégrer le formulaire adaptatif converti à n’importe quelle base de données de votre choix.

## Configurer la connexion entre l’instance AEM et la base de données {#set-up-connection-aem-instance-database}

L’établissement d’une connexion entre une instance AEM et une base de données MYSQL consiste à :

* [Installer un package connecteur MYSQL](#install-mysql-connector-java-file)

* [Créer des schémas et des tableaux dans la base de données](#create-schema-and-tables-in-database)

* [Configurer des paramètres de connexion](#configure-connection-between-aem-instance-and-database)

* [Installer et configurer l’exemple de package pour l’intégration au portail Formulaires](#set-up-and-configure-sample)

### Installer le fichier mysql-connector-java-5.1.39-bin.jar {#install-mysql-connector-java-file}

Effectuez les étapes suivantes, sur toutes les instances d’auteur et de publication, pour installer le fichier mysql-connector-java-5.1.39-bin.jar :

1. Accédez à http://[server]:[port]/system/console/depfinder et recherchez le package com.mysql.jdbc.
1. Dans la colonne Exported by (Exporté par), vérifiez si le package est exporté par un groupe. Continuez si le package n’est pas exporté par un groupe.
1. Accédez à http://[server]:[port]/system/console/bundles et cliquez sur **[!UICONTROL Install/Update]** (Installer/Mettre à jour).
1. Cliquez sur **[!UICONTROL Choose File]** (Choisir un fichier) et accédez au chemin permettant de sélectionner le fichier mysql-connector-java-5.1.39-bin.jar. Cochez également les cases **[!UICONTROL Start Bundle]** (Démarrer le groupe) et **[!UICONTROL Refresh Packages]** (Actualiser les packages).
1. Cliquez sur **[!UICONTROL Install]** (Installer) ou **[!UICONTROL Update]** (Mettre à jour). Une fois cette opération effectuée, redémarrez le serveur.
1. (Windows uniquement) Désactivez le pare-feu système pour votre système d’exploitation.

### Créer des schémas et des tableaux dans la base de données {#create-schema-and-tables-in-database}

Pour créer des schémas et des tableaux dans la base de données, procédez comme suit :

1. Créez un schéma dans la base de données à l’aide de l’instruction SQL suivante :

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   où **formsportal** fait référence au nom du schéma.

1. Créez un tableau **data** dans le schéma de base de données à l’aide de l’instruction SQL suivante :

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Créez un tableau **metadata** dans le schéma de base de données à l’aide de l’instruction SQL suivante :

   ```sql
   CREATE TABLE `metadata` (
       `formPath` varchar(1000) DEFAULT NULL,
       `formType` varchar(100) DEFAULT NULL,
       `description` text,
       `formName` varchar(255) DEFAULT NULL,
       `owner` varchar(255) DEFAULT NULL,
       `enableAnonymousSave` varchar(45) DEFAULT NULL,
       `renderPath` varchar(1000) DEFAULT NULL,
       `nodeType` varchar(45) DEFAULT NULL,
       `charset` varchar(45) DEFAULT NULL,
       `userdataID` varchar(45) DEFAULT NULL,
       `status` varchar(45) DEFAULT NULL,
       `formmodel` varchar(45) DEFAULT NULL,
       `markedForDeletion` varchar(45) DEFAULT NULL,
       `showDorClass` varchar(255) DEFAULT NULL,
       `sling:resourceType` varchar(1000) DEFAULT NULL,
       `attachmentList` longtext,
       `draftID` varchar(45) DEFAULT NULL,
       `submitID` varchar(45) DEFAULT NULL,
       `id` varchar(60) NOT NULL,
       `profile` varchar(255) DEFAULT NULL,
       `submitUrl` varchar(1000) DEFAULT NULL,
       `xdpRef` varchar(1000) DEFAULT NULL,
       `agreementId` varchar(255) DEFAULT NULL,
       `nextSigners` varchar(255) DEFAULT NULL,
       `eSignStatus` varchar(45) DEFAULT NULL,
       `pendingSignID` varchar(45) DEFAULT NULL,
       `agreementDataId` varchar(255) DEFAULT NULL,
       `enablePortalSubmit` varchar(45) DEFAULT NULL,
       `submitType` varchar(45) DEFAULT NULL,
       `dataType` varchar(45) DEFAULT NULL,
       `jcr:lastModified` varchar(45) DEFAULT NULL,
       PRIMARY KEY (`id`),
       UNIQUE KEY `ID_UNIQUE` (`id`)
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Créez un tableau **additionalmetadatatable** dans le schéma de base de données à l’aide de l’instruction SQL suivante :

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Créez un tableau **commenttable** dans le schéma de base de données à l’aide de l’instruction SQL suivante :

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### Configurer la connexion entre l’instance AEM et la base de données {#configure-connection-between-aem-instance-and-database}

Procédez aux étapes de configuration suivantes pour créer une connexion entre l’instance AEM et la base de données MYSQL :

1. Accédez à la page de configuration de la console Web AEM à l’adresse *http://[host]:[port]/system/console/configMgr*.
1. Cliquez pour ouvrir **[!UICONTROL Forms Portal Draft and Submission Configuration]** (Configuration des brouillons et des envois du portail Forms) en mode d’édition.
1. Spécifiez les valeurs des propriétés comme décrit dans le tableau suivant :

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propriété</strong></th> 
    <th><strong>Description</strong></th>
    <th><strong>Valeur</strong></th> 
    </tr> 
    <tr> 
    <td><p>Service de données de brouillon du portail Formulaires</p></td> 
    <td><p>Identifiant du service de données de brouillon</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Service de métadonnées de brouillon du portail Formulaires</p></td> 
    <td><p>Identifiant du service de métadonnées de brouillon</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Service de données d’envoi du portail Formulaires</p></td> 
    <td><p>Identifiant du service de données d’envoi</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Service de métadonnées d’envoi du portail Formulaires</p></td> 
    <td><p>Identifiant du service de métadonnées d’envoi</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Service de données de signature en attente du portail Formulaires</p></td> 
    <td><p>Identificateur du service de données de signature en attente</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Service de métadonnées de signature en attente du portail Formulaires</p></td> 
    <td><p>Identificateur du service de métadonnées de signature en attente</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. Laissez les autres configurations inchangées et cliquez sur **[!UICONTROL Save]** (Enregistrer).
1. Recherchez **[!UICONTROL Apache Sling Connection Pooled DataSource]** et cliquez dessus pour l’ouvrir en mode d’édition dans la configuration de la console Web. Spécifiez les valeurs des propriétés comme décrit dans le tableau suivant :

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propriétés</strong></th> 
    <th><strong>Valeur</strong></th> 
    </tr> 
    <tr> 
    <td><p>Nom de la source de données</p></td> 
    <td><p>Un nom de source de données pour filtrer les pilotes du pool de la source de données. L’exemple d’implémentation utilise FormsPortal comme nom de la source de données.</p></td>
    </tr>
    <tr> 
    <td><p>Classe de pilote JDBC</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>URI de connexion JDBC</p></td> 
    <td><p>jdbc:mysql://[host]:[port]/[schema_name]</p></td>
    </tr>
    <tr> 
    <td><p>Nom d’utilisateur</p></td> 
    <td><p>Nom d’utilisateur pour l’authentification et l’exécution d’actions sur les tables de base de données</p></td>
    </tr>
    <tr> 
    <td><p>Mot de passe</p></td> 
    <td><p>Mot de passe associé au nom d’utilisateur</p></td>
    </tr>
    <tr> 
    <td><p>Isolation des transactions</p></td> 
    <td><p>READ_COMMITTED</p></td>
    </tr>
    <tr> 
    <td><p>Nombre max. de connexions actives</p></td> 
    <td><p>1 000</p></td>
    </tr>
    <tr> 
    <td><p>Nombre max. de connexions inactives</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>Nombre min. de connexions inactives</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Taille initiale</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Attente max.</p></td> 
    <td><p>100 000</p></td>
    </tr>
     <tr> 
    <td><p>Test lors de l’emprunt</p></td> 
    <td><p>Cochée</p></td>
    </tr>
     <tr> 
    <td><p>Test en mode inactif</p></td> 
    <td><p>Cochée</p></td>
    </tr>
     <tr> 
    <td><p>Requête de validation</p></td> 
    <td><p>Exemples de valeurs : SELECT 1(mysql), select 1 from dual (oracle), SELECT 1 (MS Sql Server) (validationQuery).</p></td>
    </tr>
     <tr> 
    <td><p>Délai d’expiration des requêtes de validation</p></td> 
    <td><p>10 000</p></td>
    </tr>
    </tbody> 
    </table>

### Installer et configurer l’exemple {#set-up-and-configure-sample}

Effectuez les étapes suivantes, sur toutes les instances d’auteur et de publication, pour installer et configurer l’exemple :

1. Téléchargez le package suivant **aem-fp-db-integration-sample-pkg-6.1.2.zip** vers votre système de fichiers.

[Obtenir le fichier](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Accédez au gestionnaire de packages AEM à l’adresse *http://[host]:[port]/crx/packmgr/*.
1. Cliquez sur **[!UICONTROL Upload Package]** (Télécharger le package).
1. Parcourez l’arborescence pour sélectionner le package **aem-fp-db-integration-sample-pkg-6.1.2.zip** et cliquez sur **[!UICONTROL OK]**.
1. Cliquez sur **[!UICONTROL Install]** (Installer) en regard du package pour l’installer.

## Configurer le formulaire adaptatif converti pour l’intégration au portail Formulaires {#configure-converted-adaptive-form-for-forms-portal-integration}

Pour activer l’envoi de formulaires adaptatifs à l’aide de la page Portail Forms, procédez comme suit :
1. [Exécutez la conversion](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) pour convertir un formulaire source en un formulaire adaptatif.
1. Ouvrez le formulaire adaptatif en mode d’édition.
1. Appuyez sur Form Container (Conteneur de formulaires) et sélectionnez ![Configurer le formulaire adaptatif](assets/configure-adaptive-form.png).
1. Dans la section **[!UICONTROL Submission]** (Envoi), sélectionnez **[!UICONTROL Forms Portal Submit Action]** (Action d’envoi vers le portail Forms) dans la liste déroulante **[!UICONTROL Submit Action]** (Action d’envoi).
1. Appuyez sur ![Enregistrer la politique de modèle](assets/edit_template_done.png) pour enregistrer les paramètres.

## Créer et configurer la page Portail Formulaires {#create-configure-forms-portal-page}

Pour créer une page Portail Forms et la configurer afin de pouvoir envoyer des formulaires adaptatifs via cette page, procédez comme suit :

1. Connectez-vous à l’instance d’auteur AEM et appuyez sur **[!UICONTROL Adobe Experience Manager]** >  **[!UICONTROL Sites]**.
1. Sélectionnez l’emplacement où vous souhaitez enregistrer la nouvelle page Portail Forms et appuyez sur **[!UICONTROL Create]** (Créer) > **[!UICONTROL Page]**.
1. Sélectionnez le modèle de la page, appuyez sur **[!UICONTROL Next]** (Suivant), indiquez un titre pour la page et appuyez sur **[!UICONTROL Create]** (Créer).
1. Appuyez sur **[!UICONTROL Edit]** (Modifier) pour configurer la page.
1. Dans l’en-tête de la page, appuyez sur ![Modifier le modèle](assets/edit_template_sites.png)  > **[!UICONTROL Edit Template]** (Modifier le modèle) pour ouvrir le modèle de la page.
1. Appuyez sur Layout Container (Conteneur de dispositions), puis sur ![Modifier la politique de modèle](assets/edit_template_policy.png). Dans l’onglet **[!UICONTROL Allowed Components]** (Composants autorisés), activez les options **[!UICONTROL Document Services]** (Services de document) et **[!UICONTROL Document Services Predicates]** (Prédicats de services de document), puis sur ![Enregistrer la politique de modèle](assets/edit_template_done.png).
1. Insérez le composant **[!UICONTROL Search &amp; Lister]** dans la page. Tous les formulaires adaptatifs existants disponibles sur votre instance AEM sont alors répertoriés sur la page.
1. Insérez le composant **[!UICONTROL Drafts &amp; Submissions]** (Brouillons et envois) dans la page. Deux onglets **[!UICONTROL Draft Forms]** (Brouillons de formulaires) et **[!UICONTROL Submitted Forms]** (Formulaires envoyés) s’affichent sur la page Portail Forms. L’onglet **[!UICONTROL Draft Forms]** (Brouillons de formulaires) affiche également le formulaire adaptatif converti généré à l’aide des étapes mentionnées dans [Configurer le formulaire adaptatif converti pour l’intégration au portail Forms](#configure-converted-adaptive-form-for-forms-portal-integration).

1. Appuyez sur **[!UICONTROL Preview]** (Aperçu), puis, sur le formulaire adaptatif converti, spécifiez les valeurs des champs du formulaire adaptatif et envoyez-le. Les valeurs que vous spécifiez pour les champs de formulaire adaptatif sont envoyées à la base de données intégrée.
