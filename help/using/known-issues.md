---
title: Problèmes connus
description: problèmes connus et limites d’Automated forms conversion Service (AFCS)
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: introduction
role: Admin, Developer
level: Beginner, Intermediate
exl-id: 35f59e02-e38e-473a-94c8-123e0a85ac8e
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 96%

---

# Problèmes connus et limites {#known-issues-limitations}

Avant de commencer à utiliser le service AEM Forms Automated forms conversion (AFCS), passez en revue les problèmes et limitations connus suivants :

## Problèmes connus {#known-issues}

* Le dossier contenant des formulaires à convertir ne doit pas comporter plus de 15 formulaires et 50 pages au total. La taille du dossier source ne doit pas dépasser 10 Mo. Ne créez pas de sous-dossiers dans le dossier source.
* Certains éléments des formulaires, pourtant facilement visibles par l’œil humain, restent [difficiles à identifier pour le service](styles-and-pattern-considerations-and-best-practices.md). Utilisez l’[éditeur de vérification et de correction](review-correct-ui-edited.md) pour identifier et convertir ces éléments.
* Éditeur de vérification et de correction :

   * Aucune action d’annulation. Le bouton Save (Enregistrer) enregistre définitivement les modifications.
   * Aucune prise en charge des panneaux répétables pour les formulaires basés sur XFA.
   * Si vous modifiez une liste dans un tableau à l’aide de l’éditeur de vérification et de correction, la largeur des rangées ne s’ajuste pas automatiquement et le texte risque de déborder sur la rangée suivante du tableau.
   * La fonctionnalité **[!UICONTROL Auto-detect multi-column layout from input forms]** (Détection automatique d’une mise en page à plusieurs colonnes dans les formulaires d’entrée) ne fonctionne pas avec l’éditeur de vérification et de correction et les fragments de formulaire.
   * La signature tactile créée avec l’éditeur de vérification et de correction ne se charge pas pour les formulaires adaptatifs publiés.


* Pour les formulaires basés sur XFA :
   * L’extraction de fragments d’un formulaire basé sur XFA n’est pas prise en charge.
   * Les scripts XFA (par exemple, les scripts permettant de générer automatiquement des valeurs pour un composant déroulant) ne sont pas pris en charge.
   * Le métamodèle ne fonctionne pas pour le groupe de choix.
   * Les options de groupes de choix qui ne comportent qu’un seul caractère ne sont pas identifiées.
   * Lorsque le document source est un fichier XFA dynamique (.XDP) et qu’il [définit le comportement des propriétés XFA dans un formulaire adaptatif](https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr), la propriété de présence du document source n’est pas respectée. Par exemple, un champ du document source est marqué comme masqué et un script le rend visible ; le champ reste alors visible dans le formulaire adaptatif de sortie.

* Lorsque vous utilisez l’option **Use input AcroForm as Document of Record (DoR) for generated adaptive forms** (Utiliser l’entrée AcroForm comme document d’enregistrement pour les formulaires adaptatifs générés), tenez compte des points suivants :

<table>
    <tr>
        <td>La liaison et les données sont perdues pour les champs de texte composites. Un champ de texte composite contient plusieurs zones de texte alignées les unes avec les autres. Par exemple, dans un AcroForm, un numéro de carte de crédit est divisé en plusieurs zones de texte ayant chacune une liaison distincte. Lorsque l’AcroForm est converti en formulaire adaptatif, celui-ci comporte une liaison unique pour toutes les zones de texte. Pour contourner le problème, avant de convertir un AcroForm en formulaire adaptatif, modifiez-le afin d’utiliser une seule zone de texte pour les numéros de carte de crédit.</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>La liaison et les données sont perdues pour les champs de date composites. Un champ de date composite est composé de trois champs différents. Par exemple, un champ de date de naissance dans un AcroForm est divisé en trois champs distincts. Le formulaire adaptatif fournit un composant de sélection de date prêt à l’emploi. Pour utiliser le composant de sélection de date du formulaire adaptatif tout en conservant la liaison de l’AcroForm, avant de convertir un AcroForm en formulaire adaptatif, modifiez-le afin d’utiliser un champ de date unique.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>Si la taille des cases à cocher est supérieure au texte d’accompagnement, celles-ci ne sont pas détectées et la liaison dans l’AcroForm est perdue. Modifiez l’AcroForm pour réduire la taille des cases à cocher par rapport au texte d’accompagnement.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>Si les champs de saisie ne s’alignent pas sur le champ de texte correspondant, le champ de saisie n’est pas détecté.  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>Le service convertit toutes les cases à cocher d’un AcroForm en groupes de choix distincts. Des groupes de choix distincts sont créés pour préserver les liaisons avec AcroForm. Ne fusionnez pas les groupes de choix dans le formulaire adaptatif. Cela entraînera la perte de liaisons. Si vous fusionnez les groupes de choix, convertissez à nouveau le formulaire pour rétablir les liaisons perdues. </td>
        <td></td>
    </tr>
    <tr >
        <td>Les bordures de certains tableaux sortent du cadre de la page dans un document d’enregistrement généré automatiquement. </td>
        <td></td>
    </tr>
</table>

## Restrictions {#limitations}

* Les formulaires PDF avec une mise en page dynamique complexe, des champs avec un contour en pointillés ou des champs remplis ne sont pas pris en charge.
* Les images et le texte dans les images ne sont pas identifiés. Ajoutez manuellement des images aux formulaires convertis.
* Les documents d’illustration XDP ne sont pas pris en charge.
* Les formulaires PDF de plus de 15 pages ne sont pas pris en charge.
* Les documents chiffrés, protégés par mot de passe et sécurisés ne sont pas convertis. Supprimez le chiffrement ou les mots de passe avant d’exécuter la conversion.
* Les tableaux complexes (par exemple, les tableaux sans bordure, les tableaux imbriqués et les tableaux avec des valeurs d’espace réservé) ne sont pas pris en charge. Utilisez l’éditeur de formulaire adaptatif pour ajouter ou modifier des tableaux complexes après la conversion. Seuls les tableaux simples, avec des champs vides, des en-têtes appropriés et des bordures clairement définies sont pris en charge.
* Le service convertit en formulaires adaptatifs uniquement des formulaires en anglais, français, allemand, espagnol, italien et portugais. Vous pouvez traduire des formulaires adaptatifs convertis dans une autre langue à l’aide du [Processus de traduction AEM](https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).
* AEM 6.4 Forms ne prend pas en charge la détection automatique de la mise en page à plusieurs colonnes des formulaires d’entrée.
* Les informations codées à l’aide de couleurs dans le formulaire PDF source ne sont pas transférées vers le formulaire adaptatif.
* Les couleurs du formulaire PDF source ne sont pas transférées vers les thèmes de formulaire adaptatif.
* Les formulaires PDF colorés sont traités comme des formulaires en niveaux de gris et les champs sont détectés en conséquence.
