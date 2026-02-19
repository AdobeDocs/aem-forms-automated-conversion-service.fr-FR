---
title: Présentation de Automated Forms Conversion Service (AFCS)
description: Accélérer la conversion des formulaires imprimés en formulaires adaptatifs
solution: Experience Manager Forms
feature: Adaptive Forms, Foundation Components
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: edabeac8-cd66-48ca-a99f-9643a1c184cf
source-git-commit: 23d441d19dea63382f0a0024b4682d5bd0eaa63c
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 87%

---

# Automated Forms Conversion service (AFCS) {#introduction-to-automated-forms-conversion-service}

Le service AFCS (Automated Forms Conversion Service) permet d’accélérer la numérisation et la modernisation des expériences de capture de données grâce à la conversion automatisée de PDF forms en formulaires adaptatifs. Ce service, optimisé par Adobe Sensei, convertit automatiquement vos formulaires PDF en formulaires adaptatifs réactifs, basés sur HTML5 et compatibles avec divers appareils. Tout en tirant parti des investissements existants dans les formulaires PDF et XFA, le service applique également les validations, le style et la mise en page appropriés aux champs de formulaires adaptatifs lors de la conversion. Le service aide à :

* réduire les efforts manuels requis pour la conversion de formulaires imprimés en formulaires adaptatifs ;
* appliquer des modèles et des validations adaptés lors de la conversion ;
* générer un document d’enregistrement au cours de la conversion ;
* regrouper les champs récurrents en fragments de formulaire réutilisables ;
* activer Adobe Analytics pendant la conversion.

![C’est simple. Il vous suffit de nous fournir les formulaires sources. Nous nous occupons du reste. Vous obtiendrez des formulaires adaptatifs de qualité. Vous aurez de plus la possibilité de les personnaliser à votre envie. ](assets/pdf-to-adaptive-form-gitx50.gif)

## Intégration  {#onboarding}

Le service est disponible gratuitement pour les clients et clientes à terme AEM 6.5 Forms et AEM 6.5 LTS Forms On-Premise et les clients et clientes d’entreprise Adobe-Managed Service. Vous pouvez contacter l’équipe de ventes d’Adobe ou votre représentant Adobe pour demander l’accès au service. Le service est également disponible gratuitement et préactivé pour les clients AEM Forms as a Cloud Service.

Adobe autorise l’accès de votre entreprise et fournit les privilèges requis à la personne désignée comme administrateur au sein de votre entreprise. L’administrateur peut autoriser les développeurs (utilisateurs) AEM Forms de votre entreprise à se connecter au service. Pour en savoir plus, consultez la page [Configurer le service de conversion automatisée de formulaires](configure-service.md).

## Formulaires PDF et langues pris en charge {#supported-languages-and-pdf-forms}

Le service prend en charge les formulaires PDF non interactifs, les formulaires créés avec Adobe Acrobat (AcroForms) et les formulaires basés sur XFA créés à l’aide d’AEM Forms ou d’Adobe LiveCycle.

Le service prend également en charge les formulaires PDF compatibles avec Adobe Sign. Si le formulaire PDF source contient des balises de texte Adobe Sign, le service conserve toutes les informations liées à Adobe Sign pendant la conversion et associe les informations du signataire présentes dans le PDF source aux champs de formulaire adaptatif correspondants. Cette fonction est disponible uniquement pour AcroForms.

Le service peut convertir des formulaires en anglais, français, allemand, espagnol, italien et portugais en formulaires adaptatifs. Vous pouvez traduire des formulaires adaptatifs générés dans une autre langue à l’aide du [Processus de traduction AEM](https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).

## Processus de conversion  {#conversion-workflow}

Automated Forms Conversion service (AFCS) s’exécute sur Adobe Cloud. Connectez votre instance AEM au service, téléchargez des formulaires sur votre instance AEM et lancez la conversion. Le processus de conversion est détaillé ci-dessous :

![Processus](assets/conversion-workflow.png)

### &#x200B;1. Configurer l’environnement {#set-up-the-environment}

Automated Forms Conversion service (AFCS) s’exécute sur Adobe Cloud. [Configurez le compte Adobe I/O de votre organisation et connectez votre instance AEM locale](configure-service.md) au service de conversion s’exécutant sur Adobe Cloud. Pour AEM 6.5 et AEM 6.5 LTS, vous devez activer les composants principaux des formulaires adaptatifs si vous utilisez des modèles et des thèmes basés sur les composants principaux. Voir [Configurer le service](configure-service.md#referencepackage).

### &#x200B;2. Convertir les formulaires PDF en formulaires adaptatifs {#use-the-conversion-service}

Une fois votre environnement AEM Forms configuré, pour convertir vos formulaires PDF en formulaires adaptatifs, [téléchargez des formulaires PDF](convert-existing-forms-to-adaptive-forms.md) sur votre instance AEM et [démarrez la conversion](convert-existing-forms-to-adaptive-forms.md#run-the-conversion). Avant de télécharger les formulaires, tenez compte des éléments suivants :

* Ne téléchargez pas de formulaires sécurisés. Le service ne convertit pas les formulaires protégés par mot de passe et chiffrés.
* Ne téléchargez pas de formulaires numérisés, colorés et complétés dans une langue autre que l’anglais, le français, l’allemand, l’espagnol, l’italien et le portugais. Ces types de formulaires ne sont pas pris en charge.
* Ne téléchargez pas de formulaires PDF dont le nom comporte des espaces.
* Ne téléchargez pas de [portfolios PDF](https://helpx.adobe.com/fr/acrobat/using/overview-pdf-portfolios.html). Le service ne convertit pas un portfolio PDF en formulaire adaptatif.
* Apportez les modifications suggérées dans l’article [Bonnes pratiques et remarques](styles-and-pattern-considerations-and-best-practices.md) aux formulaires PDF.
* Pour éviter les pièges, reportez-vous à l’article [Problèmes connus](known-issues.md).

### &#x200B;3. Vérifier les formulaires convertis {#review-converted-forms}

Dans le monde réel, les formulaires peuvent présenter des exigences de capture de données complexes en termes de disposition de champs ou de dénomination, ou encore des suggestions implicites qui peuvent ne pas être capturées avec précision par la logique de détection basée sur l’intelligence artificielle et l’apprentissage automatique. Une fois la conversion automatisée terminée, vous pouvez utiliser l’[éditeur de vérification et de correction](review-correct-ui-edited.md) pour vérifier le formulaire converti et apporter les modifications nécessaires afin d’obtenir le résultat souhaité. Après avoir apporté les modifications requises, renvoyez le formulaire pour conversion.

Le temps nécessaire à la conversion automatisée dépend de divers facteurs tels que la taille du formulaire d’entrée, la complexité du formulaire, la place dans la file d’attente de traitement du service. L’utilisateur est régulièrement informé de la progression via un indicateur d’état sur le dossier/fichier. Une fois la conversion terminée, une notification est également envoyée par courrier électronique à l’adresse configurée.

