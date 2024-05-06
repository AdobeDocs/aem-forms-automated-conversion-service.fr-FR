---
title: Questions fréquentes
description: Requêtes courantes ou questions fréquemment posées
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: introduction
role: Admin, Developer
level: Beginner, Intermediate
exl-id: 3a29f8d4-8ea0-49eb-bfe0-0eab5f0c52c7
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: ht
source-wordcount: '1791'
ht-degree: 100%

---

# Questions fréquentes{#frequently-asked-questions}

1. **Quelle version d’AEM Forms Automated Forms Conversion service (AFCS) prend-il en charge ?**
   <p>Automated Forms Conversion service (AFCS) prend en charge AEM 6.4 Forms et AEM 6.5 Forms. Il fonctionne avec AEM Forms sur OSGi et AEM Forms sur JEE. En plus de l’instance d’auteur AEM, vous avez besoin du dernier package complémentaire AEM Forms pour utiliser le service. Pour obtenir des instructions détaillées, consultez la page <a href="configure-service.md">Configurer le service de conversion automatisée de formulaires</a>.</p> 
    <br>

1. **Le service peut-il être installé sur site ?**
   <p>Adobe forme régulièrement les algorithmes d’intelligence artificielle et de machine learning de Automated Forms Conversion service (AFCS) avec de nouveaux ensembles de données pour améliorer la précision de la conversion. Les algorithmes mis à jour sont périodiquement déployés sur le service de conversion exécuté sur Adobe Cloud. Tous les clients du service bénéficient des algorithmes mis à jour. Ainsi, le déploiement central hébergé dans le cloud est le mieux adapté à Automated Forms Conversion service (AFCS) afin d’améliorer l’apprentissage et, par extension, les services proposés à la clientèle.</p> 
    <p>Le service convertit les formulaires vierges en formulaires adaptatifs. Le service ne prend pas en charge les formulaires remplis et l’extraction de données à partir de formulaires remplis. Supprimez les données des formulaires remplis et supprimez ou mettez sur liste d’autorisation les informations confidentielles des formulaires avant de les envoyer au service de conversion.</p> <br>

1. **Le service prend-il en charge tous les formats de formulaires PDF ? Quelles sont toutes les langues prises en charge ?**
   <p>Le service peut convertir des formulaires PDF non interactifs, des formulaires XDP et PDF basés sur XFA et des AcroForms en formulaires adaptatifs. Le service ne prend pas en charge les formulaires numérisés ou remplis. Pour connaître les autres restrictions, consultez l’article <a href="known-issues.md">Problèmes connus</a>.<br /> </p> 
    <p>Nous ajoutons régulièrement la prise en charge d’autres types de sources. Reportez-vous régulièrement à la section <a href="introduction.md">Formulaires PDF pris en charge</a> pour vous tenir au courant des dernières caractéristiques et fonctionnalités ajoutées.</p>

   Le service peut convertir en formulaires adaptatifs uniquement des formulaires en anglais, français, allemand, espagnol, italien et portugais. Vous pouvez traduire des formulaires adaptatifs générés dans une autre langue à l’aide du [Processus de traduction AEM.](https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **Le service peut-il produire un formulaire XDP au lieu d’un formulaire adaptatif ?**
   <p>Le service ne produit pas de sortie XDP. Nous ajoutons régulièrement de nouvelles fonctionnalités au service. Reportez-vous régulièrement à la section <a href="introduction.md">Langues et formulaires PDF pris en charge</a> pour vous tenir au courant des dernières caractéristiques et fonctionnalités ajoutées.</p> <br>

1. **Quel est le type de schéma généré ?**
   <p>Vous pouvez utiliser le service pour générer : </p>

   * un formulaire adaptatif lié à un schéma JSON ; et
   * un formulaire adaptatif qui n’est lié à aucun schéma. <br><br>

1. **Le service peut-il convertir un formulaire Microsoft Word en formulaire adaptatif ?**
   <p>Non, le service ne peut pas convertir de formulaire Microsoft Word en formulaire adaptatif. Vous pouvez enregistrer un formulaire Microsoft Word au format PDF, puis convertir le formulaire PDF en un formulaire adaptatif. Le processus complet est le suivant : </p> <br>

   1. Utilisez Adobe Acrobat pour [convertir un document Word en PDF non interactif](https://helpx.adobe.com/fr/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. Utilisez Adobe Acrobat pour [convertir les formulaires PDF produits en formulaires PDF à remplir](https://helpx.adobe.com/fr/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
   1. Utilisez Adobe Acrobat pour mettre à jour et corriger manuellement les champs de formulaire.
   1. Enregistrez le formulaire PDF. Vous pouvez désormais utiliser le formulaire avec le service de conversion pour générer un formulaire adaptatif. Vous pouvez également utiliser le formulaire comme modèle de document d’enregistrement.


1. **Le service peut-il convertir des formulaires papier numérisés et des formulaires en couleurs en formulaires adaptatifs ?**
   <p>Le service peut convertir les formulaires PDF colorés en formulaires adaptatifs. Le service ne prend pas en charge les formulaires numérisés ou remplis. Pour connaître les autres restrictions, consultez l’article <a href="known-issues.md">Problèmes connus</a>.</p> <br>

1. **Le service peut-il convertir un formulaire numérisé ou uniquement l’image d’un formulaire en un formulaire adaptatif ?**
   <p>Le service ne prend pas en charge la conversion de formulaires numérisés ou d’une image d’un formulaire en un formulaire adaptatif prêt à l’emploi. Cependant, vous pouvez utiliser Adobe Acrobat pour convertir l’image d’un formulaire en un formulaire PDF. Ensuite, utilisez le service pour convertir le formulaire PDF en un formulaire adaptatif. Utilisez toujours une image de qualité pour la conversion du formulaire dans Acrobat. Cela améliore la qualité de la conversion.</p> <br>

1. **Certains formulaires basés sur XDP utilisent des fragments de formulaire. Où ces fragments doivent-ils être téléchargés ?**
   <p class="MsoNormal">Téléchargez des fragments de formulaire dans le dossier de conversion et conservez la structure du dossier d’origine. Cela permet de conserver les chemins d’accès relatifs utilisés dans les formulaires et fragments de formulaire basés sur XDP.</p> <br>

1. **Le service prend-il en charge les formulaires XDP liés à des schémas ? Si je dispose d’un formulaire XDP lié à un schéma, dois-je intégrer le schéma au formulaire XDP ?**
   <p>Oui, le service prend en charge les formulaires XDP liés à des schémas et nécessite l’intégration du schéma au formulaire XDP source. Lorsque vous convertissez un formulaire XDP lié à un schéma, le service génère un schéma JSON. La structure du schéma JSON est similaire à celle du schéma XSD des formulaires XDP sources.</p> <br>

1. **Le service n’est pas parvenu à convertir les formulaires. Quelle en est la raison et comment résoudre le problème?**
Les raisons les plus courantes de l’échec de la conversion sont les suivantes :</p>
   * Des formulaires PDF sécurisés sont fournis pour conversion. N’utilisez pas de formulaires PDF protégés par mot de passe ou sécurisés pour la conversion.
   * La connexion Internet est interrompue. Assurez-vous d’être connecté à Internet pendant la conversion.
   * Le PDF source a une image du formulaire au lieu du formulaire réel.
   * Le service n’est pas configuré correctement, l’URL du service n’est pas fournie ou l’URL du service fournie est incorrecte. Vérifiez la [configuration du service](configure-service.md#configure-the-cloud-service) dans **[!UICONTROL AEM]** > **[!UICONTROL Tools]** (Outils) > **[!UICONTROL Cloud Services]** (Services cloud) > **[!UICONTROL Automated Forms Conversion configuration]** (Configuration de conversion automatisée de formulaires).
   * La configuration IMS n’est pas configurée correctement. Vérifiez l’intégrité de la configuration IMS pour vous assurer de son bon fonctionnement. Pour vérifier si la configuration IMS est correcte ou non :
      1. Accédez à `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Sélectionnez la configuration. Dans l’en-tête, cliquez sur **[!UICONTROL Check Health]** (Vérifier l’intégrité), puis sur **[!UICONTROL Check]** (Vérifier). En cas de réussite, le message **[!UICONTROL Token retrieved successfully!]** (Jeton récupéré) s’affiche. <br> <br>

1. **L’utilisation de polices personnalisées a-t-elle un impact sur la conversion ?**
   <p>Lorsqu’un formulaire PDF non interactif est converti en un formulaire adaptatif, les polices sont incorporées dans le formulaire PDF afin d’améliorer la qualité de la conversion. La prise en charge de l’incorporation de polices est limitée aux formulaires PDF non interactifs. Pour optimiser la conversion des formulaires PDF basés sur XFA et AcroForm, des polices de secours sont utilisées.</p> 
    <p>Seuls les formulaires disponibles dans le répertoire de polices personnalisées répertorié dans le champ <strong>Customer fonts directory</strong> (Répertoire de polices personnalisées) de la configuration <strong>CQ-DAM-Handler-Gibson Font Manager Service</strong> sont incorporés dans un formulaire PDF non interactif.</p> 
    <p> </p> <br>

1. **Le service identifie-t-il et utilise-t-il les polices du PDF source dans les formulaires adaptatifs de sortie ?**
   <p>Le style et la mise en page d’un formulaire HTML réactif sont généralement différents par rapport à un formulaire PDF ou papier. Pour assurer une mise en page et un style cohérents dans toutes les entreprises, les formulaires adaptatifs utilisent <a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/themes.html">des thèmes pour appliquer un style à un formulaire</a>. Le service de conversion utilise les polices et les styles de police spécifiés dans le thème appliqué lors de la conversion. Vous pouvez modifier les polices et les styles de police du thème pour donner un aspect unique aux composants d’un formulaire adaptatif.</p> <br>

1. **Le service extrait-il automatiquement JavaScript des formulaires basés sur XDP et l’applique-t-il aux formulaires adaptatifs correspondants ?**
   <p>Le service ne convertit pas automatiquement les scripts des formulaires basés sur XFA ou des formulaires Acro en règles de formulaires adaptatifs correspondants. Vous (les auteurs de formulaires) pouvez utiliser l’<a href="https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/rule-editor.html">éditeur de règles</a> pour ajouter de l’interactivité à un formulaire adaptatif.</p> <br>

1. **Certains objets de formulaire ne sont pas convertis correctement en composants de formulaires adaptatifs. Comment résoudre le problème ?**
   <p>Automated Forms Conversion service (AFCS) se base sur un large éventail de formulaires. Les applications basées sur l’intelligence artificielle et l’apprentissage automatique sont toutefois limitées par leurs données et modèles d’apprentissage. Plusieurs types de champs, dispositions, modèles et contextes visibles par l’œil humain restent toutefois difficiles à identifier automatiquement. Le service peut ne pas identifier ces objets ou les reconnaître de manière incorrecte. Vous pouvez utiliser l’éditeur <a href="review-correct-ui-edited.md" target="_blank">de vérification et de correction</a> pour apporter les modifications nécessaires à la mise en page familière basée sur le formulaire papier du formulaire d’entrée.</p> <br/>

1. **Certaines corrections sont répétées sur plusieurs formulaires. Le service peut-il identifier et corriger toutes ces instances lors de futures conversions ?**

   Le service est constamment formé d’après vos formulaires et modèles. Il apprend de nouveaux modèles chaque jour. Il reste encore à appliquer automatiquement les corrections répétées à l’ensemble des formulaires. Gardez un œil sur les nouvelles versions pour être au courant dès que cette fonctionnalité sera disponible. <br/><br/>

   Vous pouvez utiliser le métamodèle pour mapper les objets de formulaire au composant de formulaire adaptatif de votre choix et préconfigurer les validations, les règles, les modèles de données, le texte d’aide et les propriétés d’accessibilité des composants. Toutes les propriétés spécifiées sont appliquées lors de la conversion. Vous pouvez utiliser un métamodèle pour appliquer des propriétés communes aux champs. Cela peut vous aider à réduire le nombre de problèmes récurrents dans les formulaires.<br/><br/>

1. **Quelles sont les options disponibles pour les formulaires contenant des données sensibles, telles que des informations d’identification personnelles ?**
Le service ne prend en charge que les formulaires vierges ou non remplis. Ne téléchargez pas de formulaires remplis ou de formulaires contenant des informations d’identification personnelles. Supprimez également les données préremplies, les informations d’identification personnelles et les informations confidentielles des formulaires sources. <br/>

1. **Où placer les en-têtes et pieds de page ?**
   <p>Placez l’en-tête et le pied de page dans un modèle de formulaires adaptatifs. Si le formulaire PDF source a un en-tête et un pied de page, le service détecte et remplace l’en-tête et le pied de page détectés par un en-tête et un pied de page disponibles dans le modèle de formulaire adaptatif, pendant la conversion. Si un en-tête ou un pied de page supplémentaire est inclus dans le formulaire adaptatif, vous pouvez utiliser l’éditeur <a href="review-correct-ui-edited.md">de vérification et de correction</a> pour le corriger ou le supprimer.</p> <br />

1. **Combien de temps le service fait-il gagner par rapport au processus manuel de planification, de conception d’actifs (thèmes, modèles), de création et de publication d’un formulaire adaptatif ?**
   <p>La durée dépend de la taille et de la complexité des formulaires d’entrée, ainsi que du nombre de demandes. Le service a l’intention de réduire considérablement le délai de valorisation en convertissant les formulaires PDF en formulaires adaptatifs beaucoup plus rapidement par rapport au processus manuel de conversion des formulaires. </p> <br />

1. **Que faire si une erreur liée aux bibliothèques RSA se produit ? Le message d’erreur est similaire au message mentionné ci-dessous :** <br/>
   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
L’erreur ci-dessus se produit lorsque Boot Delegation n’est pas configurée pour les bibliothèques RSA/BouncyCastle. Pour résoudre le problème, procédez comme suit :
   <p> </p>

   1. Désactivez l’instance AEM. Accédez au dossier `[AEM installation directory]\crx-quickstart\conf\`. Ouvrez le fichier sling.properties pour le modifier. Si vous utilisez `[AEM installation directory]\crx-quickstart\bin\start.bat` pour démarrer une instance AEM, modifiez le fichier sling.properties situé à l’emplacement suivant :`[AEM_root]\crx-quickstart\`.
   1. Ajoutez les propriétés suivantes au fichier sling.properties :<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Enregistrez le fichier, puis fermez-le. <br/>
   1. Démarrez l’instance AEM.<br/>
   <br/>

1. **Comment modifier automatiquement la casse du texte du formulaire adaptatif ?**
   <p>Vous pouvez utiliser l’éditeur de thèmes ou de styles de formulaires adaptatifs pour modifier la casse d’un champ. Par exemple, vous pouvez ouvrir l’éditeur de thèmes et définir la valeur de la propriété Casse de l’ensemble du texte du formulaire sur majuscules, minuscules ou casse mixte. Vous pouvez également utiliser l’option de remplacement de CSS dans l’éditeur de thèmes pour créer différents types de styles.</p>

1. **Puis-je utiliser des balises de texte Adobe Sign avec Automated Forms Conversion service (AFCS) ?**
   <p> Lorsque vous utilisez Automated Forms Conversion service (AFCS) pour convertir un formulaire PDF en formulaire adaptatif et que le formulaire PDF comporte des balises de texte Adobe Sign, ces balises sont converties en champs de formulaire adaptatif correspondants et les détails de la personne signataire sont automatiquement renseignés.  Cette fonctionnalité est disponible uniquement pour les formulaires Acro. Les formulaires adaptatifs prennent en charge un nombre limité de champs Adobe Sign.</p>  </br>

1. **Comment créer un formulaire PDF compatible avec Adobe Sign ?**
   </p>Pour créer un formulaire PDF compatible avec Adobe Sign :</p>

   Ajoutez les [balises de texte Adobe Sign](https://helpx.adobe.com/fr/sign/using/text-tag.html) aux noms des champs ou utilisez l’option [Convertir en formulaire Adobe Sign](https://helpx.adobe.com/fr/sign/using/create-forms-with-acrobat.html).
