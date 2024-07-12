---
title: Convertir des formulaires PDF en formulaires adaptatifs
seo-title: Convert PDF forms to adaptive forms
description: Exécuter Automated Forms Conversion service (AFCS) pour convertir des formulaires PDF en formulaires adaptatifs
seo-description: Run the Automated Forms Conversion service (AFCS) to convert PDF forms to adaptive forms
contentOwner: khsingh
topic-tags: forms
feature: Adaptive Forms, Foundation Components
exl-id: 415e05b5-5a90-490c-bf7c-d3365ce95e24
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '1725'
ht-degree: 100%

---

# Convertir des formulaires PDF en formulaires adaptatifs {#convert-print-forms-to-adaptive-forms}

Automated Forms Conversion service (AFCS) AEM Forms, optimisé par Adobe Sensei, convertit automatiquement vos formulaires PDF en formulaires adaptatifs réactifs et compatibles avec divers appareils. Que vous utilisiez des formulaires PDF non interactifs, des formulaires Acro ou des formulaires PDF basés sur XFA, Automated Forms Conversion service (AFCS) peut facilement convertir ces formulaires en formulaires adaptatifs. Pour plus d’informations sur les fonctionnalités, le processus de conversion et les informations d’intégration, consultez la page [Automated Forms Conversion service](introduction.md).

## Prérequis {#pre-requisites}

* [**Configuration du service de conversion**](configure-service.md)

* **Préparation des [modèles](https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/template-editor.html) à appliquer aux formulaires convertis :** l’utilisation d’un modèle vous permet d’harmoniser l’identité graphique de tous les formulaires adaptatifs. De plus, Automated Forms Conversion service (AFCS) n’extrait pas et n’utilise pas l’en-tête et le pied de page des documents PDF sources. Vous pouvez utiliser des modèles de formulaires adaptatifs pour spécifier l’en-tête et le pied de page. L’en-tête et le pied de page spécifiés dans le modèle sont appliqués au formulaire adaptatif lors de la conversion. Lorsque vous créez un dossier pour les modèles, sélectionnez l’option **[!UICONTROL Parcourir les configurations]** pour tous les utilisateurs.

* **Préparation des [thèmes](https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/themes.html) à appliquer aux formulaires convertis :** l’utilisation d’un thème vous permet d’harmoniser le style de tous les formulaires adaptatifs de votre entreprise.

* **(facultatif)** [**Convertir vos formulaires PDF sources en formulaire Adobe Sign**](frequently-asked-questions.md)

## Démarrer le processus de conversion {#start-the-conversion-process}

Après avoir connecté votre instance AEM au service de conversion AEM Forms, vous pouvez convertir vos formulaires PDF en formulaires adaptatifs. Pour convertir les formulaires, procédez aux étapes suivantes dans l’ordre indiqué :

* [Charger les formulaires PDF sur votre serveur AEM Forms](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [Exécuter la conversion](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [Vérifier et corriger les formulaires convertis](review-correct-ui-edited.md)

### Charger les formulaires PDF sur votre serveur AEM Forms {#upload-pdf-forms-to-your-aem-forms-server}

Le service de conversion convertit les formulaires PDF disponibles sur votre instance AEM Forms en formulaires adaptatifs. Vous pouvez télécharger tous les formulaires PDF en une seule ou en plusieurs fois, selon les besoins. Avant de télécharger les formulaires, tenez compte des éléments suivants :

* N’enregistrez pas plus de 15 formulaires dans un dossier et veillez à ce que le nombre total de pages dans un dossier ne dépasse pas 50.
* Veillez à ce que la taille du dossier ne dépasse pas 10 Mo. Ne conservez pas les formulaires dans un sous-dossier.
* Veillez à ce qu’un formulaire ne dépasse pas 15 pages.
* Ne téléchargez pas de formulaires protégés. Le service ne convertit pas les formulaires protégés par mot de passe et sécurisés.
* Ne téléchargez pas de formulaires PDF sources dont le nom comporte des espaces. Supprimez l’espace du nom du fichier avant de télécharger les formulaires.
* Ne téléchargez pas de [portfolios PDF](https://helpx.adobe.com/fr/acrobat/using/overview-pdf-portfolios.html). Le service ne convertit pas un portfolio PDF en formulaire adaptatif.
* Lisez les sections [Problèmes connus](known-issues.md) et [Bonnes pratiques et remarques](styles-and-pattern-considerations-and-best-practices.md), puis apportez les modifications suggérées aux formulaires.

Pour télécharger les formulaires à convertir dans un dossier sur votre instance AEM Forms, procédez comme suit :

1. Connectez-vous à l’instance AEM Forms.

1. Appuyez sur **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** (Formulaires) > **[!UICONTROL Forms &amp; Documents]** (Formulaires et documents).
1. Appuyez sur **[!UICONTROL Create]** (Créer) > **[!UICONTROL Folder]** (Dossier). Remplissez les champs **Title** (Titre) et **Name** (Nom) du dossier. Appuyez sur **[!UICONTROL Create]** (Créer). Un dossier est alors créé.
1. Appuyez sur le dossier nouvellement créé pour l’ouvrir.
1. Appuyez sur **[!UICONTROL Create]** (Créer) > **[!UICONTROL File Upload]** (Téléchargement de fichier). Sélectionnez les formulaires à télécharger et cliquez sur **[!UICONTROL Open]** (Ouvrir), puis sur **[!UICONTROL Upload]** (Télécharger). Les formulaires sont alors téléchargés.

### Exécuter la conversion {#run-the-conversion}

Après avoir téléchargé les formulaires et configuré le service, procédez comme suit pour démarrer la conversion :

1. Sur votre instance AEM Forms, appuyez sur **[!UICONTROL Adobe Experience Manager]** ![Boîte de dialogue de paramètres de conversion](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** (Formulaires) > **[!UICONTROL Forms &amp; Documents]** (Formulaires et documents).
1. Sélectionnez un formulaire ou le dossier contenant les formulaires PDF (formulaires à convertir) et appuyez sur **[!UICONTROL Start Automated Conversion]** (Démarrer la conversion automatisée). La boîte de dialogue **[!UICONTROL Conversion Settings]** (Paramètres de conversion) s’affiche.

   ![Spécifier les configurations](assets/conversion-settings-dialog.png)

1. Dans l’onglet **[!UICONTROL Basic]** (De base) de la boîte de dialogue Conversion Settings (Paramètres de conversion) :

   * **[!UICONTROL Sélectionnez une configuration cloud]**. Lorsque vous sélectionnez une configuration, le modèle et le thème par défaut sont déjà spécifiés. Vous pouvez indiquer un modèle ou un thème différent, si nécessaire.
   * Spécifiez un emplacement pour l’enregistrement des formulaires adaptatifs générés et du schéma correspondant. Vous pouvez utiliser des chemins par défaut ou indiquer des chemins personnalisés.
   * Utilisez l’option **Generate adaptive forms without data model bindings** (Générer des formulaires adaptatifs sans liaison de modèle de données) pour choisir de générer un formulaire adaptatif avec ou sans liaison de modèle de données.
Si vous ne sélectionnez pas cette option, le service de conversion associe automatiquement les formulaires adaptatifs à un schéma JSON et crée une liaison de données entre les champs disponibles dans le formulaire adaptatif et le schéma JSON. Le champ **[!UICONTROL Save generated data model schema at]** (Enregistrer le schéma de modèle de données généré sous) affiche l’emplacement par défaut pour l’enregistrement du schéma JSON généré. Vous pouvez également personnaliser l’emplacement pour l’enregistrement du schéma généré.
Si vous sélectionnez cette option, le service de conversion génère un formulaire adaptatif sans liaison de modèle de données. Après la conversion, vous pouvez associer un formulaire adaptatif à un modèle de données de formulaire, un schéma XML ou un schéma JSON. Pour en savoir plus, consultez la page [Créer un formulaire adaptatif](https://helpx.adobe.com/fr/experience-manager/6-5/forms/using/creating-adaptive-form.html).

   <!--

   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. Dans l’onglet **[!UICONTROL Additional]** (Plus) de la boîte de dialogue Conversion Settings (Paramètres de conversion),
   * sélectionnez l’option **[!UICONTROL Extract fragment from adaptive forms]** (Extraire les fragments des formulaires adaptatifs) pour permettre au service de conversion d’identifier, d’extraire et de télécharger des fragments de formulaires pour les formulaires convertis. Lorsque vous sélectionnez l’option **[!UICONTROL Extract fragment from adaptive forms]** (Extraire les fragments des formulaires adaptatifs), les options permettant d’indiquer des chemins pour l’enregistrement des fragments de formulaires extraits et des schémas correspondants sont activées.
   * Indiquez l’emplacement des **[!UICONTROL fragments de formulaires adaptatifs existants]**, si vous disposez de fragments de formulaires adaptatifs sans schéma ou basés sur des schémas JSON existants et que vous envisagez d’utiliser ces fragments dans des formulaires adaptatifs générés automatiquement. Le service de conversion met en correspondance les fragments de formulaires adaptatifs sans schéma ou basés sur des schémas JSON disponibles avec des formulaires PDF d’entrée (formulaires PDF non interactifs uniquement). En cas de correspondance, le fragment de formulaire adaptatif concerné est utilisé dans les formulaires adaptatifs correspondants.

   >[!NOTE]
   >
   >
   > * Vous ne pouvez utiliser que l’une des deux options suivantes à la fois : **[!UICONTROL Extract Fragment]** (Extraire les fragments) ou **[!UICONTROL Use existing adaptive form fragments]** (Utiliser des fragments de formulaires adaptatifs existants). Vous ne pouvez pas utiliser les deux options en même temps.
   > * Vous ne pouvez utiliser l’option **[!UICONTROL Use existing adaptive form fragments]** (Utiliser des fragments de formulaires adaptatifs existants) qu’avec des formulaires PDF non interactifs. Les autres types de formulaires ne sont pas encore pris en charge.
   > * Vous ne pouvez utiliser que des fragments non liés ou des fragments liés à un schéma JSON avec le service de conversion automatisée. N’utilisez pas de fragments XFA. Les fragments XFA ne sont pas pris en charge.
   >

   * Sélectionnez l’option **[!UICONTROL Auto-detect multi-column layout of input forms]** (Détection automatique d’une mise en page à plusieurs colonnes dans les formulaires d’entrée) afin de conserver la mise en page du formulaire source pour les grands écrans (par exemple, ordinateurs de bureau et ordinateurs portables). Cette option permet de préserver la mise en page à plusieurs colonnes des formulaires sources. Par exemple, lorsqu’un PDF source a une mise en page à deux colonnes, le service génère un formulaire adaptatif de sortie avec une mise en page à deux colonnes pour les grands écrans et une mise en page à une seule colonne pour les appareils à petit écran, tels que les téléphones mobiles. La fonctionnalité présente certains problèmes connus par rapport à la structure du schéma de la source de données. Pour en savoir plus, consultez l’article [Problèmes connus](known-issues.md).
   * Par défaut, le service crée un panneau de niveau supérieur distinct pour chaque page d’un formulaire PDF. Vous pouvez désormais utiliser l’option **[!UICONTROL Auto-detect logical sections]** (Détection automatique de sections logiques) pour ne pas créer de panneaux au niveau de la page (panneaux basés sur le numéro de page), mais uniquement des panneaux logiques. Il regroupe également les champs qui n’appartiennent à aucune section avec la section logique précédente et les champs d’une section logique répartis sur deux pages adjacentes en une seule section logique. Par exemple, si certains champs d’une section logique se trouvent à la fin de la première page et d’autres au début de la deuxième page, tous ces champs sont regroupés en une seule section logique.

     >[!NOTE]
     > Le package connecteur 1.1.38 ou version ultérieure est nécessaire pour utiliser la fonctionnalité  **[!UICONTROL Auto-detect logical sections]** (Détection automatique de sections logiques).

* (AEM Forms as a Cloud Service uniquement) Lʼoption [Conversion automatique des sections en fragments] s’applique aux formulaires PDF qui contiennent plus de 15 pages. Cette option permet de convertir en fragments les sections de niveau supérieur détectées. Elle permet également le chargement différé de tous les fragments créés. Cette option accélère le rendu des formulaires convertis et facilite le chargement de formulaires volumineux dans l’éditeur de formulaires adaptatifs.

  >[!NOTE]
  > N’utilisez pas de modèle de disposition réactive lorsque vous utilisez l’option Conversion automatique des sections en fragments.
  > Utilisez l’éditeur de vérification et de correction pour fusionner de petits panneaux en un grand. Cela permet de réduire le nombre de fragments dans le formulaire adaptatif converti.
  > Si vous rencontrez l’exception « nombre d’appels trop élevé » :
  >
  > * Restructurez le formulaire afin de créer une hiérarchie simplifiée.
  > * [Augmentez la valeur du paramètre sling.max.calls] à un nombre suffisamment élevé jusquʼà ce que lʼexception disparaisse.
  > * [Augmentez la taille du cache](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/configure-aem-forms/configure-adaptive-forms-cache.html?lang=fr). Lʼerreur se produit dans les cas suivants : un formulaire trop complexe, un nombre élevé de tableaux et une structure hiérarchique à plusieurs niveaux.

1. Appuyez sur **[!UICONTROL Start Conversion]** (Démarrer la conversion). La conversion est alors lancée. La progression de la conversion s’affiche sur le dossier ou le formulaire tout au long de la conversion. Une fois la conversion terminée, le message est remplacé par un autre message d’état : Converted (Converti), Partially Converted (Partiellement converti) ou Conversion Failed (Échec de la conversion). À la fin de la conversion, un message est également envoyé à l’adresse électronique configurée :

   * En cas de conversion réussie, le formulaire adaptatif converti et le schéma associé sont téléchargés vers le chemin spécifié dans l’onglet **[!UICONTROL Basic]** (De base) de la boîte de dialogue de conversion. Les fragments de formulaire et le schéma correspondant ne sont téléchargés que si l’option Extract Fragment (Extraire les fragments) est sélectionnée avant le démarrage de la conversion.
   * En cas d’échec de la conversion, le message **[!UICONTROL Conversion Failed]** (Échec de la conversion) s’affiche si aucun formulaire d’entrée n’est converti et le message **[!UICONTROL Partially Failed]** (Échec partiel) apparaît lorsque seuls quelques formulaires d’entrée ne sont pas parvenus à être convertis. Un message électronique est alors envoyé à l’[adresse de messagerie configurée](configure-service.md#configureemailnotification) et une erreur est signalée dans le fichier error.log.

   Si vous convertissez un formulaire PDF basé sur XFA en un formulaire adaptatif, le service de conversion associe automatiquement le formulaire PDF au formulaire adaptatif converti en tant que modèle de document d’enregistrement. Après la conversion, vous pouvez ouvrir les propriétés du formulaire adaptatif pour afficher le modèle de document d’enregistrement dans la section **[!UICONTROL Document of Record Template Configuration]** (Configuration du modèle de document d’enregistrement) de l’onglet **[!UICONTROL Form Model]** (Modèle de formulaire). </br>

   Le service de conversion ne télécharge automatiquement le formulaire PDF vers le formulaire adaptatif converti en tant que modèle de document d’enregistrement que si vous activez l’option **[!UICONTROL Tools]** (Outils) > **[!UICONTROL Cloud Services]** (Services cloud) > **[!UICONTROL Automated Forms Conversion Configuration]** (Configuration de la conversion automatisée de formulaires) > **[!UICONTROL Properties of selected configuration]** (Propriétés de la configuration sélectionnée) > **[!UICONTROL Advanced]** (Avancé) > **[!UICONTROL Generate Document of Record]** (Générer un document d’enregistrement).

   <!--

   Comment Type: draft

   <note type="note">
   <p>By default, the adaptive form produces a JSON schema instead of XML schema on submission. JSON schema of a converted adaptive form is complaint with XML schema of an XFA-based form. You can use the <a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString">org.apache.sling.commons.json.xml API</a> to convert a JSON schema to XML schema. You can also use the following sample code for conversion:</p>
   <p><code class="code">import org.apache.sling.commons.json.JSONException;
   <discoiqbr /> import org.apache.sling.commons.json.JSONObject;
   <discoiqbr /> import org.apache.sling.commons.json.xml.XML;
   <discoiqbr />
   <discoiqbr /> public class ConversionUtils {
   <discoiqbr />
   <discoiqbr /> public static String jsonToXML(String jsonString) throws JSONException {
   <discoiqbr /> //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
   <discoiqbr /> //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
   <discoiqbr /> //Note: Need to extract boundData part before converting to XML
   <discoiqbr /> return XML.toString(new JSONObject(jsonString));
   <discoiqbr /> }
   <discoiqbr /> }</code><br /> </p>
   </note>
   -->

   >[!NOTE]
   >
   >Si le processus de conversion prend plus de 60 minutes et que le formulaire PDF n’est toujours pas converti en formulaire adaptatif, créez un dossier sur l’instance AEM Forms, téléchargez le formulaire PDF dans le dossier nouvellement créé et redémarrez la conversion.

## Vérifier et corriger les formulaires convertis {#review-and-correct-the-converted-forms}

Les formulaires réels ont des exigences de capture de données complexes. Une fois la conversion automatisée terminée, les clients peuvent vérifier la qualité de conversion du formulaire et apporter les modifications nécessaires. AEM Forms fournit un éditeur de [vérification et de correction](review-correct-ui-edited.md) pour procéder aux changements nécessaires. Il vous permet d’améliorer l’identification automatisée des champs de formulaire et de convertir les champs identifiés d’un type à un autre. Par exemple, il peut vous aider à identifier la mise en page à deux colonnes d’un formulaire et modifier un champ identifié automatiquement comme un bouton radio en un champ à choix multiples.
