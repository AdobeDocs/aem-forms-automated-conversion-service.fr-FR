---
title: Configuration du service Automated forms conversion (AFCS)
description: Préparez votre instance AEM à utiliser le service Automated forms conversion (AFCS).
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer, User
level: Beginner, Intermediate
exl-id: 8f21560f-157f-41cb-ba6f-12a4d6e18555
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '2784'
ht-degree: 87%

---

# Configuration du service Automated forms conversion (AFCS) {#about-this-help}

Cette aide décrit comment un administrateur d’AEM peut configurer Automated forms conversion Service (AFCS) pour automatiser la conversion de ses PDF forms en formulaires adaptatifs. Cette aide est destinée aux administrateurs informatiques et AEM de votre entreprise. Cette aide s’adresse à un public familiarisé avec les technologies suivantes :

* installation, configuration et administration des packages Adobe Experience Manager et AEM ;

* utilisation des systèmes d’exploitation Linux® et Microsoft® Windows® ;

* configuration des serveurs de messagerie SMTP.

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service (AFCS)** -->

## Intégration {#onboarding}

Le service est disponible gratuitement pour les clients AEM 6.4 Forms et AEM 6.5 Forms On-Premise et les clients d’entreprise Adobe Managed Services. Vous pouvez contacter l’équipe de ventes d’Adobe ou votre représentant Adobe pour demander l’accès au service. Le service est également disponible gratuitement et préactivé pour les clients AEM Forms as a Cloud Service.

Adobe autorise l’accès de votre entreprise et fournit les privilèges requis à la personne désignée comme administrateur au sein de votre entreprise. L’administrateur peut autoriser les développeurs (utilisateurs) AEM Forms de votre entreprise à se connecter au service.

## Prérequis {#prerequisites}

Vous avez besoin des éléments suivants pour utiliser le service Automated forms conversion (AFCS) :

* Le service Automated forms conversion (AFCS) est activé pour votre organisation
* compte Adobe ID avec des privilèges d’administrateur pour le service de conversion ;
* Une version opérationnelle d’instance d’auteur AEM 6.4, AEM 6.5 ou AEM Forms as a Cloud Service avec les dernières mises à jour ou le Service Pack le plus récent d’AEM ;
* utilisateur AEM (sur votre instance AEM) membre du groupe d’utilisateurs de formulaires.

## Configuration de l’environnement {#setuptheservice}

Avant d’utiliser le service, préparez votre instance d’auteur AEM à la connexion au service exécuté sur Adobe Cloud. Pour préparer votre instance à la connexion au service, procédez aux étapes suivantes dans l’ordre indiqué :

1. [Télécharger et installer AEM 6.4 ou AEM 6.5, ou intégrer AEM Forms as a Cloud Service](#aemquickstart)
1. [Télécharger et installer le dernier Service Pack AEM](#servicepack)
1. [Télécharger et installer le dernier package complémentaire AEM Forms](#downloadaemformsaddon)
1. (Facultatif) [Télécharger et installer le dernier package connecteur](#installConnectorPackage)
1. [Créer des thèmes et des modèles personnalisés](#referencepackage)

### Téléchargement et installation d’AEM 6.4 ou AEM 6.5, ou intégration d’AEM Forms as a Cloud Service {#aemquickstart}


Le service Automated forms conversion (AFCS) s’exécute sur AEM instance d’auteur. Vous avez besoin d’AEM 6.4, d’AEM 6.5 ou d’AEM Forms as a Cloud Service pour configurer une instance d’auteur AEM.

* Si vous ne disposez pas d’une version opérationnelle d’AEM 6.4 ou d’AEM 6.5, téléchargez-la à partir des emplacements suivants. Après avoir téléchargé AEM, consultez la page [Déploiement et maintenance](https://helpx.adobe.com/fr/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall) pour obtenir des instructions sur la configuration d’une instance d’auteur AEM.

   * Si vous êtes déjà client AEM, téléchargez AEM 6.4 ou AEM 6.5 sur le site [Adobe Licensing](http://licensing.adobe.com).

   * Si vous êtes un partenaire Adobe, utilisez le [programme de formation des partenaires Adobe](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) pour demander AEM 6.4 ou AEM 6.5.

* Si vous utilisez AEM Forms as a Cloud Service, consultez les instructions d’intégration d’[AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-forms-cloud-service.html?lang=fr#setup-environment) et [configurez un environnement de développement local](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?lang=fr#setup-environment).

### (Pour AEM 6.4 et AEM 6.5 uniquement) Téléchargement et installation du Service Pack le plus récent {#servicepack}

Téléchargez et installez le dernier Service Pack AEM. Pour obtenir des instructions détaillées,  consultez [Notes de mise à jour du Service Pack AEM 6.4](https://helpx.adobe.com/fr/experience-manager/6-4/release-notes/sp-release-notes.html) ou [Notes de mise à jour du Service Pack AEM 6.5](https://helpx.adobe.com/fr/experience-manager/6-5/release-notes/sp-release-notes.html).

### (Pour AEM 6.4 et AEM 6.5 uniquement) Téléchargement et installation du package complémentaire AEM Forms  {#downloadaemformsaddon}

Une instance AEM contient des fonctionnalités de formulaires de base. Le service de conversion nécessite toutes les capacités d’AEM Forms. Téléchargez et installez le package complémentaire AEM Forms pour bénéficier de toutes les capacités d’AEM Forms. Le package est requis pour la configuration et l’exécution du service de conversion. Pour obtenir des instructions détaillées, consultez [Installer et configurer les fonctionnalités de capture de données](https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html).

>[!NOTE]
> Assurez-vous de procéder aux configurations nécessaires après l’installation du package complémentaire.
>

<!-- ### (Optional) Download and install connector package  {#installConnectorPackage}

The connector package provides early access to the [Auto-detect logical sections](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) features and improvements delivered in release AFC-2020.03.1. Do not install the package if you do not require feature and improvements delivered in AFC-2020.03.1.  You can [download the connector package from AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1). -->


### Créer des thèmes et des modèles personnalisés {#referencepackage}

Si vous lancez AEM 6.4 ou AEM 6.5 en [mode de production](https://helpx.adobe.com/fr/experience-manager/6-5/sites/administering/using/production-ready.html) (mode d’exécution nosamplecontent), les packages de référence ne sont pas installés. Les packages de référence contiennent des exemples de thèmes et de modèles. Le service Automated forms conversion (AFCS) nécessite au moins un thème et un modèle pour convertir un formulaire de PDF en formulaire adaptatif. Créez un thème et un modèle personnalisés et [configurez le service](#configure-the-cloud-service) de sorte à utiliser les modèles et thèmes personnalisés avant d’utiliser le service.

Vous pouvez également télécharger et installer le package [AEM Forms Reference Assets](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) sur votre instance d’auteur. Ce dernier crée des thèmes de référence et un modèle.

## Configurer le service {#configure-the-service}

Avant de procéder à la configuration du service et à la connexion de votre instance locale au service exécuté sur Adobe Cloud, découvrez les types de personnes et les privilèges requis pour la connexion au service. Le service nécessite deux types de personnes différentes : les administrateurs et les développeurs.

* **Administrateurs** : les administrateurs sont responsables de la gestion des logiciels et des services Adobe pour leur entreprise. Les administrateurs accordent l’accès aux développeurs de leur entreprise pour se connecter à Automated forms conversion Service (AFCS) s’exécutant sur Adobe Cloud. Lorsqu’un administrateur est nommé pour une entreprise, il reçoit un courrier électronique intitulé **[!UICONTROL « You now have administrator rights to manage Adobe software and services for your organization »]** (Vous disposez désormais des droits d’administrateur pour gérer les logiciels et services Adobe pour votre entreprise). Si vous êtes un administrateur, vérifiez si vous avez reçu le message mentionné ci-dessus et [accordez l’accès aux développeurs de votre entreprise](#adduseranddevs).

![Courrier électronique d’autorisation d’accès de l’administrateur](assets/admin-console-adobe-io-access-grantedx75.png)

* **Développeurs**: un développeur connecte une instance d’auteur AEM Forms locale au service Automated forms conversion (AFCS) en cours d’exécution sur Adobe Cloud. Lorsqu’un administrateur accorde des droits à un développeur pour se connecter à Automated forms conversion Service (AFCS), un e-mail intitulé You now have developer access to manage Adobe API integrations for your organization (Vous disposez désormais d’un accès en tant que développeur pour gérer les intégrations d’API d’ pour votre organisation) est envoyé au développeur. Si vous êtes un développeur, vérifiez si vous avez reçu le message mentionné ci-dessus et [connectez votre instance AEM locale au service de conversion automatisée de formulaires sur Adobe Cloud.](#connectafcadobeio)

![Courrier électronique d’autorisation d’accès du développeur](assets/email-developer-accessx94.png)

### (Pour les administrateurs d’AEM 6.4 et d’AEM 6.5 uniquement) Accorder l’accès aux développeurs de votre organisation {#adduseranddevs}

Une fois qu’Adobe a autorisé l’accès de votre entreprise et octroyé les privilèges requis à l’administrateur, ce dernier peut se connecter à l’Admin Console (voir les instructions détaillées ci-dessous), créer un profil et ajouter des développeurs au profil. Les développeurs peuvent connecter une instance locale d’AEM Forms au service Automated forms conversion (AFCS) sur Adobe Cloud.

Les développeurs sont des membres de votre entreprise désignés pour exécuter le service de conversion. Seuls les développeurs qui sont ajoutés au profil du service Adobe Automated forms conversion (AFCS) sont autorisés à utiliser le service Automated forms conversion (AFCS). Pour créer un profil et y ajouter des développeurs, procédez comme suit : Au moins un profil est nécessaire pour accorder l’accès requis aux développeurs de votre entreprise :

1. Connectez-vous à l’[Admin Console](https://adminconsole.adobe.com/). Utilisation **Adobe ID** de l’administrateur configuré pour utiliser Automated forms conversion service (AFCS) pour se connecter. N’utilisez aucun autre ID ou Federated ID pour vous connecter.
1. Cliquez sur l’option **[!UICONTROL Automated Forms Conversion]** (Conversion automatisée de formulaires).
1. Cliquez sur **[!UICONTROL New Profile]** (Nouveau profil) dans l’onglet **[!UICONTROL Products]** (Produits).
1. Renseignez les champs suivants dans le profil :**[!UICONTROL Name]** (Nom), **[!UICONTROL Display Name]** (Nom d’affichage) et **[!UICONTROL Description]**. Cliquez sur **[!UICONTROL Done]** (Terminé). Le profil est alors créé.

   ![Précisez les détails du nouveau profil.](assets/create-new-profile-details.png)

1. Ajoutez un développeur au profil. Pour ajouter les développeurs :
   1. Dans l’[Admin Console](https://adminconsole.adobe.com/enterprise), accédez à l’onglet de présentation.
   1. Cliquez sur **[!UICONTROL Assign Developers]** (Attribuer des développeurs) sur la carte de produit requise.
   1. Saisissez les adresses électroniques des développeurs et éventuellement leurs noms et prénoms.
   1. Sélectionnez les profils de produits. Appuyez sur **[!UICONTROL Save]** (Enregistrer).

Répétez les étapes ci-dessus pour tous les utilisateurs. Pour plus de détails sur l’ajout de développeurs, consultez la page [Gérer les développeurs](https://helpx.adobe.com/fr/enterprise/using/manage-developers.html).

Une fois qu’un administrateur ajoute des développeurs au profil Adobe I/O, ceux-ci en sont informés par courrier électronique. Après l’avoir reçu, les développeurs peuvent procéder à [la connexion d’une instance AEM Forms locale avec le service de conversion automatisée de formulaires sur Adobe Cloud](#connectafcadobeio).

### (Pour les développeurs uniquement) Connectez votre instance AEM Forms locale au service Automated forms conversion sur Adobe Cloud. {#connectafcadobeio}

Une fois qu’un administrateur vous a accordé un accès en tant que développeur, vous pouvez connecter votre instance AEM Forms locale au service Automated forms conversion (AFCS) exécuté sur Adobe Cloud. Pour connecter votre instance AEM Forms au service, procédez aux étapes suivantes dans l’ordre indiqué :

* [Configurer les notifications par courrier électronique](configure-service.md#configureemailnotification)
* [Ajouter un utilisateur au groupe forms-users](#adduserstousergroup)
* [Obtenir des certificats publics](#obtainpubliccertificates)
* [Configurer les API de service sur Adobe Developer Console](#createintegration)
* [Configurer le service cloud](configure-service.md#configure-the-cloud-service)

#### Configurer les notifications par e-mail {#configureemailnotification}

Le service Automated forms conversion (AFCS) utilise le service de messagerie Day CQ pour envoyer des notifications par courrier électronique. Ces notifications contiennent des informations sur les conversions ayant réussi ou échoué. Si vous choisissez de ne pas recevoir de notification, ignorez ces étapes. Pour configurer le service de messagerie Day CQ, procédez comme suit :

* Pour AEM 6.4 Forms ou AEM 6.5 Forms :

   1. Accédez au gestionnaire de configuration AEM à l’adresse `http://localhost:4502/system/console/configMgr`
   1. Ouvrez la configuration du Service de messagerie Day CQ. Spécifiez une valeur pour les champs **[!UICONTROL SMTP server host name]** (Nom d’hôte du serveur SMTP), **[!UICONTROL SMTP server port]** (Port du serveur SMTP) et **[!UICONTROL From address]** (Adresse de l’expéditeur). Cliquez sur **[!UICONTROL Save]** (Enregistrer).

      Vous pouvez contacter votre fournisseur de services de messagerie ou votre administrateur informatique pour obtenir des informations sur le nom d’hôte et le port du serveur SMTP. Vous pouvez utiliser n’importe quelle adresse électronique valide dans le champ d’adresse de l’expéditeur. Par exemple, notification@example.com ou donotreply@example.com.

   1. Ouvrez la configuration de **[!UICONTROL Day CQ Link Externalizer]**. Dans le champ **[!UICONTROL Domains]** (Domaines), spécifiez le nom de l’hôte ou l’adresse IP et le numéro de port réels pour les instances locales, de l’auteur et de publication. Cliquez sur **[!UICONTROL Save]** (Enregistrer).

* Pour AEM Forms as a Cloud Service, [soumettez un ticket de support pour activer le service de messagerie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#sending-email).

#### Ajouter un utilisateur au groupe forms-users {#adduserstousergroup}

Indiquez une adresse électronique dans le profil de l’utilisateur AEM désigné pour exécuter le service. Assurez-vous que l’utilisateur est membre du groupe d’[utilisateurs de formulaires](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/forms-groups-privileges-tasks.html?lang=fr). Les courriers électroniques sont envoyés à l’adresse de l’utilisateur qui procède à la conversion. Pour indiquer l’adresse de l’utilisateur et ajouter un utilisateur au groupe d’utilisateurs de formulaires :

1. Connectez-vous à votre instance d’auteur AEM Forms en tant qu’administrateur AEM. Utilisez vos informations d’identification AEM locales pour vous connecter. N’utilisez pas Adobe ID pour vous connecter. Appuyez sur **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** (Outils) > **[!UICONTROL Security]** (Sécurité) > **[!UICONTROL Users]** (Utilisateurs).

1. Sélectionnez un utilisateur désigné pour exécuter le service de conversion et appuyez sur **[!UICONTROL Properties]** (Propriétés). La page Edit User Settings (Modifier les paramètres utilisateur) s’affiche.
1. Indiquez une adresse électronique dans le champ **[!UICONTROL Email]** (Adresse électronique) et appuyez sur **[!UICONTROL Save]** (Enregistrer). Les courriers électroniques sont envoyés à l’adresse indiquée en cas de réussite ou d’échec de la conversion.
1. Cliquez sur l’onglet **Groups** (Groupes). Dans l’onglet de sélection de groupe, saisissez et sélectionnez le groupe **forms-users**. Appuyez sur **Save &amp; Close** (Enregistrer et fermer). L’utilisateur est maintenant membre du groupe forms-users.

#### (Pour AEM 6.4 et AEM 6.5 uniquement) Obtention de certificats publics {#obtainpubliccertificates}

Un certificat public permet d’authentifier votre profil sur Adobe I/O.

1. Connectez-vous à votre instance d’auteur AEM Forms. Accédez à **[!UICONTROL Tools]** (Outils) > **[!UICONTROL Security]** (Sécurité) > **[!UICONTROL Adobe IMS Configurations]** (Configurations Adobe IMS). Appuyez sur **[!UICONTROL Create]** (Créer). La page **[!UICONTROL Adobe IMS Technical Account Configuration]** (Configuration de compte technique Adobe IMS) s’affiche.

   ![La page Adobe IMS Technical Account Configuration (Configuration de compte technique Adobe IMS)](assets/adobe-ims-technical-account-configuration.png)

1. Sélectionnez **[!UICONTROL Automated Forms Conversion Service]** (Service de conversion automatisée de formulaires) dans Cloud Solution.

1. Cochez la case **[!UICONTROL Create new certificate]** (Créer un nouveau certificat) et indiquez un alias. L’alias sert de nom à la boîte de dialogue. Appuyez sur **[!UICONTROL Create certificate]** (Créer un certificat). Une boîte de dialogue s’affiche. Cliquez sur **[!UICONTROL OK]**. Le certificat est alors créé.

1. Appuyez sur **[!UICONTROL Download Public Key]** (Télécharger la clé publique) et enregistrez le fichier de certificat *AEM-Adobe-IMS.crt* sur votre ordinateur. Le fichier de certificat est utilisé pour la [Configuration des API de service sur Adobe Developer Console](#createintegration). Appuyez sur **[!UICONTROL Next]** (Suivant).

1. Indiquez les informations suivantes :

   * Titre : indiquez un titre.
   * Serveur d’autorisation : [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)\

   Laissez les autres champs vides pour l’instant (pour les remplir ultérieurement). Gardez la page ouverte.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### (Pour AEM 6.4 et AEM 6.5 uniquement) Configuration des API de service sur Adobe Developer Console {#createintegration}

Pour utiliser le service Automated forms conversion (AFCS), créez un projet et ajoutez l’API du service de configuration automatisée de Forms au projet sur la console Adobe Developer. L’intégration génère la clé API, le secret client, la charge utile (JWT).

1. Connectez-vous à [https://console.adobe.io/](https://console.adobe.io/). Utilisez votre Adobe ID et le compte de développeur que votre administrateur a mis à votre disposition pour vous connecter à la console Adobe I/O.
1. Sélectionnez votre entreprise dans le coin supérieur droit. Si vous ne connaissez pas le nom de votre entreprise, contactez votre administrateur.
1. Appuyez sur **[!UICONTROL Create new project]** (Créer un projet). Un écran pour démarrer votre nouveau projet apparaît. Appuyez sur **[!UICONTROL Add API]** (Ajouter une API). Un écran avec la liste de toutes les API activées pour votre compte apparaît.
1. Sélectionnez **[!UICONTROL Automated Forms Conversion service]** (Service de conversion automatisée de formulaires) et appuyez sur **[!UICONTROL Next]** (Suivant). Un écran de configuration de l’API apparaît.
1. Sélectionnez l’option [!UICONTROL Upload your public key] (Charger votre clé publique), chargez le fichier AEM-Adobe-IMS.crt téléchargé dans la section [Obtenir des certificats publics](#obtainpubliccertificates) et appuyez sur **[!UICONTROL Next]** (Suivant). L’option Create a new Service Account (JWT) credential (Créer un nouvel identifiant de compte de service (JWT)) apparaît. Appuyez sur **[!UICONTROL Next]** (Suivant).
1. Sélectionnez un profil de produit et appuyez sur **[!UICONTROL Save configured API]** (Enregistrer l’API configurée). Sélectionnez le profil créé tout en [accordant l’accès aux développeurs de votre entreprise](#adduseranddevs). Si vous ne savez pas quel profil sélectionner, contactez votre administrateur.
1. Appuyer **[!UICONTROL Compte de service (JWT)]** pour afficher la clé API, le secret client et d’autres informations nécessaires pour connecter votre instance d’AEM locale au service Automated forms conversion (AFCS). Les informations de la page sont utilisées pour créer la configuration IMS sur votre ordinateur local.

1. Ouvrez la page de configuration IMS sur votre instance locale. Vous avez gardé la page ouverte à la fin de la section [Obtenir des certificats publics](#obtainpubliccertificates).

   ![Spécifier le titre, la clé API, le secret client et la charge utile ](assets/ims-configuration-details.png)

1. Sur la page technique d’Adobe IMS, spécifiez la clé API et le secret client. Utilisez les valeurs spécifiées sur le compte de service (JWT) de la page de la console Adobe Developer.

   >[!NOTE]
   >
   >
   >Pour la charge utile, utilisez le code fourni dans l’onglet Générer JWT de la page Compte de service (JWT) de la console Adobe Developer.

1. Appuyez sur **[!UICONTROL Save]** (Enregistrer). La configuration IMS est alors créée.

   >[!CAUTION]
   >
   >Créez une seule configuration IMS. Ne créez pas plusieurs configurations IMS.

1. Sélectionnez la configuration IMS et appuyez sur **[!UICONTROL Check Health]** (Vérifier l’intégrité). Une boîte de dialogue s’affiche. Appuyez sur **[!UICONTROL Check]** (Vérifier). Une fois la connexion établie, le message *Token retrieved successfully* (Jeton récupéré) s’affiche.

   ![Une fois la connexion établie, le message Token retrieved successfully (Jeton récupéré) s’affiche. ](assets/health-check.png)

   <br/> <br/>

#### Configurer le service cloud {#configure-the-cloud-service}

Créez une configuration de service cloud pour connecter votre instance AEM au service de conversion. Cela vous permet également de spécifier un modèle, un thème et des fragments de formulaire pour une conversion. Vous pouvez créer plusieurs configurations de service cloud distinctes pour chaque ensemble de formulaires. Par exemple, vous pouvez avoir une configuration donnée pour les formulaires du service commercial et une autre pour les formulaires de support client. Pour créer une configuration de service cloud, procédez comme suit :

1. Sur votre instance AEM Forms, appuyez sur **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** (Outils) > **[!UICONTROL Cloud Services]** (Services cloud) > **[!UICONTROL Automate Forms Conversion Configuration]** (Automatiser la configuration de conversion de formulaires).
1. Appuyez sur le dossier **[!UICONTROL Global]**, puis sur **[!UICONTROL Create]** (Créer). La page de création de la configuration de conversion automatisée de formulaires apparaît. La configuration est créée dans le dossier Global. Vous pouvez également créer la configuration dans un dossier différent qui existe déjà ou créer un dossier pour vos configurations.

1. Sur la page **[!UICONTROL Create Automated Forms Conversion Configuration]** (Créer une configuration de conversion automatisée de formulaires), spécifiez la valeur des champs suivants et appuyez sur **[!UICONTROL Next]** (Suivant).

   | Field (Champ) | Description |
   |--- |--- |
   | Title (Titre) | Titre unique pour la configuration. Le titre s’affiche dans l’interface utilisateur utilisée pour démarrer la conversion. |
   | Name (Nom) | Nom unique pour la configuration. La configuration est enregistrée dans le référentiel crx-repository sous le nom indiqué. Le nom peut être identique au titre. |
   | Thumbnail location (Emplacement de la miniature) | Emplacement de la miniature de la configuration. |
   | Service URL (URL du service) | URL du service Automated forms conversion (AFCS) sur Adobe Cloud. Utilisez l’URL suivante : `https://aemformsconversion.adobe.io/`. |
   | Template (Modèle) | Modèle par défaut à appliquer aux formulaires convertis. Vous pouvez toujours indiquer un modèle différent avant de démarrer la conversion. Un modèle contient une structure de base et un contenu initial pour un formulaire adaptatif. Vous pouvez choisir un modèle parmi les modèles prêts à l’emploi. Vous pouvez également créer un modèle personnalisé. |
   | Theme (Thème) | Thème par défaut à appliquer aux formulaires convertis. Vous pouvez toujours indiquer un thème différent avant de démarrer la conversion.  Vous pouvez cliquer sur l’icône pour choisir un thème prêt à l’emploi. Vous pouvez également créer un thème personnalisé. |
   | Existing Fragments (Fragments existants) | Emplacement des fragments existants, le cas échéant. |
   | Custom Meta-model (Métamodèle personnalisé) | Chemin d’accès du fichier .schema.json du métamodèle personnalisé. Vous pouvez créer des métamodèles distincts pour l’anglais, le français, l’allemand, l’espagnol, l’italien et le portugais. |

1. Dans l’onglet **[!UICONTROL Advanced]** (Avancé) de la page **[!UICONTROL Create Automated Forms Conversion Configuration]** (Créer une configuration de conversion automatisée de formulaires), spécifiez la valeur des champs suivants :

   <table>
   <thead>
   <tr>
   <th>Field (Champ)</th>
   <th>Description</th>
   </tr>
   </thead>
   <tbody>
   <tr>
   <td >Generate Document of Record (Générer un document d’enregistrement)</td>
   <td>Sélectionnez l’option pour générer automatiquement un document d’enregistrement pour les formulaires convertis. L’option est uniquement destinée aux formulaires basés sur XFA (formulaires XDP et PDF). Lorsque vous activez l’option, après l’envoi d’un formulaire, vous pouvez autoriser vos clients à conserver un enregistrement, sous forme imprimée ou en tant que document, des informations qu’ils ont intégrées au formulaire à des fins de référence ultérieure. On parle ici de document d’enregistrement.</td>
   </tr>
   <tr>
   <td>Enable Analytics (Activer Adobe Analytics)</td>
   <td>(Pour AEM 6.4 et AEM 6.5 uniquement) Sélectionnez l’option permettant d’activer Adobe Analytics pour tous les formulaires convertis. Avant d’utiliser cette option, assurez-vous qu’Adobe Analytics est activé pour votre instance AEM Forms.</td>
   </tr>
   </tbody>
   </table>

   * Lorsque la source est un formulaire basé sur XFA avec l’extension .XDP, le document d’enregistrement de sortie conserve la disposition XFA. Sinon, le service de conversion utilise un modèle prêt à l’emploi pour générer un document d’enregistrement pour d’autres formulaires basés sur XFA.
   * Lors de l’envoi d’un formulaire XFA, les données d’envoi du formulaire sont enregistrées en tant qu’attribut ou élément XML. Par exemple, `<Amount currency="USD"> 10.00 </Amount>`. La devise est enregistrée en tant qu’attribut et le montant de la devise, 10.00, est enregistré en tant qu’élément. L’envoi de données d’un formulaire adaptatif n’a pas d’attributs, simplement des éléments. Ainsi, lorsqu’un formulaire basé sur XFA est converti en formulaire adaptatif, les données d’envoi de formulaire adaptatif contiennent un élément pour chacun de ces attributs. Par exemple :

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Appuyez sur **[!UICONTROL Create]** (Créer). La configuration cloud est alors créée. Votre instance AEM Forms est prête à commencer la conversion des formulaires hérités en formulaires adaptatifs.
