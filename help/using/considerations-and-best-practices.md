---
title: Bonnes pratiques et remarques
description: NE PAS PUBLIER
seo-description: DO NOT PUBLISH
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: false
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 97%

---


# Bonnes pratiques et remarques {#do-not-publish-best-practices-and-considerations}

<!--
[DO NOT PUBLISH]
-->

Le service de conversion automatisée AEM Forms convertit un formulaire PDF en un formulaire adaptatif. Le service utilise des algorithmes d’intelligence artificielle et de machine learning pour comprendre la disposition et les champs du formulaire source. Chaque service de machine learning tire sans cesse des enseignements des données sources et enregistre ainsi des résultats de plus en plus concluants. Tout comme les humains, ces services apprennent par l’expérience.

Le service Automated forms conversion (AFCS) est formé sur un grand ensemble de formulaires. Il identifie facilement les champs d’un formulaire source et génère des formulaires adaptatifs. Cependant, certains champs et styles des formulaires PDF, pourtant facilement visibles par l’œil humain, restent difficiles à comprendre pour le service. Le service peut affecter des types de champs ou des panneaux différents de ceux applicables à certains champs ou styles. Tous ces modèles de champ et de style sont répertoriés ci-dessous.

Le service commencerait à identifier et à attribuer à ces modèles des champs ou des panneaux adaptés tout en continuant à apprendre des données sources. Pour le moment, vous pouvez utiliser l’éditeur [de vérification et de correction](review-correct-ui-edited.md) pour résoudre ces problèmes. Avant de commencer à résoudre les problèmes ou de poursuivre votre lecture, familiarisez-vous avec les [composants de formulaires adaptatifs](https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/introduction-forms-authoring.html).

## Général {#general}

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Modèles connus et résolution</td> 
   <td width="70%">Exemple</td> 
  </tr>
   <td><p><strong>Modèle</strong></p> <p>Le service ne convertit pas les formulaires PDF remplis en formulaires adaptatifs.</p> <p> </p> <p><strong>Résolution</strong></p> <p>Utilisez des formulaires adaptatifs vides.</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Le service peut ne pas reconnaître le texte et les champs denses.</p> <p> </p> <p><strong>Résolution</strong></p> <p>Laissez davantage d’espace entre le texte et les champs denses avant de débuter la conversion.</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Le service ne prend pas en charge les formulaires numérisés.</p> <p> </p> <p><strong>Résolution</strong></p> <p>N’utilisez pas de formulaires numérisés. </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Le service n’extrait pas d’images et de texte figurant dans les images. </p> <p> </p> <p><strong>Résolution</strong></p> <p>Ajoutez manuellement des images ou du texte aux formulaires convertis.</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Les tableaux dont les bordures sont en pointillés ou ne sont pas clairement définies ne sont pas convertis.</p> <p><strong>Résolution</strong></p> <p>Utilisez des tableaux dont les bordures sont clairement définies.  </p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## Groupe de choix  {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Modèle</td> 
   <td width="70%">Exemple</td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Les options de groupe de choix sous d’autres formes que des cases ou des cercles ne sont pas converties en composants de formulaires adaptatifs correspondants. </p> <p> </p> <p><strong>Résolution</strong></p> <p>Donnez aux options de choix la forme de cases ou de cercles ou utilisez l’éditeur de vérification et de correction pour identifier les formes.</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## Champs de formulaire {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Modèle</td> 
   <td width="70%">Exemple</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>Modèle</strong></p> <p>Le service n’identifie pas les champs dont les bordures ne sont pas clairement définies.</p> <p> </p> <p><strong>Résolution</strong></p> <p>Utilisez l’éditeur de vérification et de correction pour identifier ces champs.</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Le service n’identifie pas certains champs de formulaire avec des légendes en bas ou à droite.</p> <p> </p> <p><strong>Résolution</strong></p> <p>Utilisez l’éditeur de vérification et de correction pour identifier ces champs.</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Le service fusionne ou attribue un type incorrect à certains champs de formulaire placés très près les uns des autres ou dont les bordures ne sont pas clairement définies. </p> <p> </p> <p><strong>Résolution</strong></p> <p>Utilisez l’éditeur de vérification et de correction pour identifier ces champs.</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Le service peut ne pas reconnaître les champs dont les légendes sont éloignées ou avec une ligne pointillée entre la légende et le champ d’entrée.</p> <p> </p> <p><strong>Résolution</strong></p> <p>Utilisez des champs de formulaire avec des bordures clairement définies ou utilisez l’éditeur de vérification et de correction pour corriger ces problèmes.</p> </td> 
   <td><img src="assets/form-fields-with-far-away-captions.png" /></td> 
  </tr>
 </tbody>
</table>

## Listes {#lists}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Modèle</td> 
   <td width="70%">Exemple</td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Les listes contenant des champs de formulaire sont fusionnées ou ne sont pas converties en composants de formulaires adaptatifs correspondants.</p> <p><strong>Résolution</strong></p> <p>Utilisez des champs de formulaire avec des bordures clairement définies ou utilisez l’éditeur de vérification et de correction pour corriger ces problèmes.</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Le service peut ne pas identifier quelques listes imbriquées</p> <p> </p> <p><strong>Résolution</strong></p> <p>Utilisez l’éditeur de vérification et de correction pour résoudre ces problèmes.</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>Modèle</strong></p> <p>Le service fusionne certaines listes contenant des groupes de choix.</p> <p><strong>Résolution</strong></p> <p>Utilisez l’éditeur de vérification et de correction pour résoudre ces problèmes.</p> </td> 
   <td><img src="assets/lists-containing-choice-groups.png" /> </td> 
  </tr>
 </tbody>
</table>

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fiields without bordes are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->

