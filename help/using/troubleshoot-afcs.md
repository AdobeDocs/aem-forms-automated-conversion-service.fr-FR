---
title: Résoudre les problèmes de Automated Forms Conversion service (AFCS)
description: Problèmes courants de l’AFCS et leurs solutions
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
contentOwner: khsingh
exl-id: e8406ed9-37f5-4f26-be97-ad042f9ca57c
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 100%

---

# Résoudre les problèmes de Automated Forms Conversion service (AFCS)

Le document fournit des étapes de résolution de base pour les erreurs courantes.

<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. -->

## Erreurs courantes {#commonerrors}

| Erreur | Exemple |
|--- |--- |
| **Message d’erreur** <br> L’en-tête du jeton d’accès n’est pas disponible. <br><br> **Raison** <br> Un administrateur a créé plusieurs configurations IMS ou la configuration IMS n’est pas en mesure d’accéder au service AFCS sur Adobe Cloud. <br><br>**Résolution** <br> S’il existe plusieurs configurations, supprimez toutes les configurations et [créez une nouvelle configuration](configure-service.md#obtainpubliccertificates). <br> S’il existe une configuration unique, utilisez **Health Check** pour [vérifier la connectivité](configure-service.md#createintegrationoption). | ![L’en-tête du jeton d’accès n’est pas disponible](assets/invalid-ims-configurations.png) |
| **Message d’erreur** <br> Impossible de se connecter au service.  <br><br>**Motif** <br> URL du service incorrecte ou aucune URL du service mentionnée dans les services cloud de Automated Forms Conversion service (AFCS). <br><br>**Résolution** <br> Corrigez l’[URL du service](configure-service.md#configure-the-cloud-service) dans les services cloud de Automated Forms Conversion service (AFCS). | ![Impossible de se connecter au service.](assets/wrong-service-url-configured.png) |
| **Message d’erreur** <br> Le service n’est pas parvenu à convertir le formulaire.  <br><br>**Raison** <br> Problèmes de connectivité réseau de votre côté, le service est arrêté en raison d’une maintenance planifiée, ou interruption sur Adobe Cloud. <br><br>**Résolution** <br> Résolvez les problèmes de connectivité réseau de votre côté et vérifiez l’état du service sur https://status.adobe.com/ pour voir s’il existe une interruption planifiée ou non planifiée. | ![Impossible de se connecter au service.](assets/conversion-failure.png) |
| **Message d’erreur** <br> Le nombre de pages est supérieur à 15.  <br><br>**Raison** <br> Le formulaire source comporte plus de 15 pages.  <br><br>**Résolution** <br> Utilisez Adobe Acrobat pour scinder les formulaires de plus de 15 pages. Réduisez le nombre de pages pour obtenir un formulaire ne dépassant pas 15 pages. | ![Impossible de se connecter au service.](assets/number-of-pages.png) |
| **Message d’erreur** <br> Le nombre de fichiers est supérieur à 15.  <br><br>**Raison** <br>  Le dossier contient plus de 15 formulaires. <br><br>**Résolution** <br> Réduisez le nombre de formulaires dans un dossier pour en obtenir 15 ou moins. Réduisez le nombre total de pages pour obtenir un dossier comportant moins de 50 pages. Réduisez la taille du dossier pour qu’elle ne dépasse pas 10 Mo. Ne conservez pas les formulaires dans un sous-dossier. Organisez les formulaires sources en un lot de 8 à 15 formulaires. | ![Impossible de se connecter au service.](assets/number-of-pages.png) |
| **Message d’erreur** <br> Le format du fichier source n’est pas pris en charge.  <br><br>**Raison** <br> Le dossier contenant les formulaires sources contient des fichiers non pris en charge. <br><br>**Résolution** <br> Le service ne prend en charge que les fichiers .xdp et .pdf. Supprimez les fichiers avec toute autre extension du dossier et exécutez la conversion. | ![Impossible de se connecter au service.](assets/unsupported-file-formats.png) |
| **Message d’erreur** <br> Les formulaires analysés ne sont pas pris en charge.  <br><br>**Raison** <br> Le formulaire PDF contient uniquement des images numérisées du formulaire et ne contient aucune structure de contenu. <br><br>**Résolution** <br> Le service ne prend pas en charge la conversion de formulaires numérisés ou d’une image d’un formulaire en un formulaire adaptatif prêt à l’emploi. Cependant, vous pouvez utiliser Adobe Acrobat pour convertir l’image d’un formulaire en un formulaire PDF. Ensuite, utilisez le service pour convertir le formulaire PDF en un formulaire adaptatif. Utilisez toujours une image de qualité pour la conversion du formulaire dans Acrobat. Cela améliore la qualité de la conversion. | ![Impossible de se connecter au service.](assets/scanned-forms-error.png) |
| **Message d’erreur** <br> Le formulaire PDF chiffré n’est pas pris en charge.  <br><br>**Raison** <br> Le dossier contient des formulaires PDF chiffrés. <br><br>**Résolution** <br> Le service ne prend pas en charge la conversion d’un formulaire PDF chiffré en formulaire adaptatif. Supprimez le chiffrement, téléchargez le formulaire non chiffré et exécutez la conversion. | ![Impossible de se connecter au service.](assets/secured-pdf-form.png) |
| **Message d’erreur** <br> Impossible d’analyser le schéma JSON du métamodèle.  <br><br>**Raison** <br> Le schéma JSON fourni au service n’est pas correctement formaté, contient des caractères non valides ou utilise une syntaxe non valide pour mapper les composants.  <br><br>**Résolution** <br> Vérifiez le formatage du fichier JSON. Vous pouvez utiliser n’importe quel validateur JSON en ligne pour vérifier le formatage et la structure du schéma. Consultez l’article [Étendre le métamodèle par défaut](extending-the-default-meta-model.md) pour plus d’informations sur la syntaxe des métamodèles. | ![Impossible de se connecter au service.](assets/invalid-meta-model-schema.png) |
| **Erreur (environnements On-premise uniquement)** <br> L’option **[!UICONTROL Langue source]** ne répertorie pas la langue correcte d’un formulaire adaptatif. <br><br>**Raison** <br> La propriété jcr:language du formulaire adaptatif n’est pas définie correctement. <br><br>**Résolution** <br> Ouvrez CRX-DE Lite, accédez à `/content/forms/af/`, ouvrez le nœud `jcr:content` et définissez sa valeur sur la langue appropriée. Pour obtenir la liste des langues prises en charge, voir [Ajout de la prise en charge de la localisation pour les paramètres régionaux non pris en charge](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/supporting-new-language-localization.html?lang=fr#add-localization-support-for-non-supported-locales). | ![Impossible de se connecter au service.](assets/aem-forms-translation-project-language-unavailable.png) |

<!--

<table>
<thead>
<tr>
<th>Error</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Error Message</strong> <p> The access token header is not available. </p><br><strong>Reason</strong> <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br><strong>Resolution</strong> <br> If there are multiple configurations, delete all the configurations and <a href="configure-service.md#obtainpubliccertificates">create a new configuration</a>. <br> If there is a single configuration, use <strong> Health Check </strong> to <a href="configure-service.md#createintegrationoption">check connectivity</a>.</td>
<td><img alt="The access token header is not available" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to connect to the service.  <br><br><strong>Reason</strong> <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service (AFCS) cloud services. <br><br><strong>Resolution</strong> <br> Correct <a href="configure-service.md#configure-the-cloud-service">Service URL</a> in Automated Forms Conversion Service (AFCS) Cloud services.</td>
<td><img alt="Unable to connect to the service." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The service failed to convert the form.  <br><br><strong>Reason</strong> <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br><strong>Resolution</strong> <br> Resolve network connectivity issues at your end and check the status of the service on <a href="https://status.adobe.com/">https://status.adobe.com/</a> for a planned or unplanned outage.</td>
<td><img alt="The service failed to convert the form." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of pages is more than 15.  <br><br><strong>Reason</strong> <br> The source form is more than 15 pages long.  <br><br><strong>Resolution</strong> <br> Use Adobe Acrobat to split forms with more than 15 pages. Bring the number of pages in a form to less than 15.</td>
<td><img alt="The number of pages is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of files is more than 15.  <br><br><strong>Reason</strong> <br>  The folder contains more than 15 forms. <br><br><strong>Resolution</strong> <br> Bring the number of forms in a folder to less than or equal to 15. Bring the total number of pages in a folder less than 50. Bring the size of the folder to less than 10 MB. Do not keep forms in a sub-folder. Organize source forms into a batch of 8-15 forms.</td>
<td><img alt="The number of files is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The source file format is not supported.  <br><br><strong>Reason</strong> <br> The folder containing source forms have some unsupported files. <br><br><strong>Resolution</strong> <br> The service supports only .xdp and .pdf files. Remove files with any other extension from the folder and run the conversion.</td>
<td><img alt="The source file format is not supported." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Scanned forms are not supported.  <br><br><strong>Reason</strong> <br> The PDF form contains only scanned images of the form and contains no content structure. <br><br><strong>Resolution</strong> <br> The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion.</td>
<td><img alt="Scanned forms are not supported." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Encrypted PDF form is not supported.  <br><br><strong>Reason</strong> <br> The folder contains encrypted PDF forms. <br><br><strong>Resolution</strong> <br> The service does not support converting an encrypted PDF form to an adaptive form. Remove the encryption, upload the non-encrypted form, and run the conversion.</td>
<td><img alt="Encrypted PDF form is not supported." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to parse meta-model JSON schema.  <br><br><strong>Reason</strong> <br> The JSON schema supplied to the service is not properly formatted, contains invalid characters, or uses invalid syntax to map components.  <br><br><strong>Resolution</strong> <br> Check the formatting of the JSON file. You can use any online JSON validator to check the formatting and structure of the schema. See, <a href="extending-the-default-meta-model.md">Extend the default meta-model</a> article for information on meta-model syntax.</td>
<td><img alt="Unable to parse meta-model JSON schema" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
-->
