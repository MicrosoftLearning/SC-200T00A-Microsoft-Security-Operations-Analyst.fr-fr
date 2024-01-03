---
lab:
  title: "Exercice\_11\_: utiliser des référentiels dans Microsoft\_Sentinel"
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Chemin d’apprentissage 7 - Labo 1 - Exercice 1 - Utiliser des référentiels dans Microsoft Sentinel

## Scénario de l’exercice

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous avez déjà créé des règles planifiées et analytiques de sécurité Microsoft.  Vous devez centraliser les règles analytiques dans un référentiel Azure DevOps.  Connectez Ensuite Sentinel au référentiel Azure DevOps et importez le contenu. 

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Use%20repositories%20in%20Microsoft%20Sentinel)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 


### Tâche 1 : créer et exporter une règle analytique

Dans cette tâche, vous allez activer l’analyse comportementale des entités dans Microsoft Sentinel.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez votre espace de travail Microsoft Sentinel.

1. Sélectionnez **Analyses** dans la zone *Configuration* du panneau gauche.

1. Sélectionnez la règle **Démarrage de RegKey** que vous avez créée précédemment.

1. Dans la barre d’outils, sélectionnez **Exporter**. **Conseil :** vous devrez peut-être sélectionner l’icône de points de suspension **(...)** pour voir l’option.

1. La règle est exportée vers un fichier texte nommé *Azure_Sentinel_analytic_rule.json*.

1. Sélectionnez **Ouvrir le fichier** sous le nom du fichier téléchargé, puis **Pus d’applications**.

1. Sélectionnez le **Bloc-notes**, puis cliquez sur **OK**.

1. Passez en revue le modèle Azure Resource Manager et fermez-le lorsque vous avez terminé.


### Tâche 2 : créer l’environnement Azure DevOps

Dans cette tâche, vous allez créer un référentiel Azure DevOps.

1. Ouvrez un autre onglet de navigateur et accédez à l’adresse (https://aexprodcus1.vsaex.visualstudio.com/me?mkt=en-US).

1. Dans la page *Nous avons besoin de quelques détails supplémentaires*, sélectionnez **Continuer**.

1. Dans la page *Prise en main d’Azure DevOps*, sélectionnez **Créer une organisation**, puis **Continuer**.

1. Dans la page *Presque terminé...*, entrez un nom pour votre organisation DevOps que vous ne souhaitez pas utiliser à l’avenir, par exemple, votre préfixe de locataire. **Conseil :** vous le trouverez sous l’onglet Ressources du labo (WWLx...).

1. *Entrez les caractères que vous voyez*, puis sélectionnez **Continuer**.

1. Sur la page *Pour commencer, créez un projet*, entrez **Mon contenu Sentinel**, puis sélectionnez **Créer un projet**.

1. Accédez à **Repos** dans le volet gauche.

1. En bas de la page, dans la zone *Initialiser la branche principale avec un fichier README ou gitignore*, sélectionnez **Initialiser**.

1. La page doit afficher les fichiers du référentiel.  le seul fichier présent est README.me.

1. Dans le panneau Fichiers (côté droit de la page), la barre d’outils inclut les options *Configurer la build*, *Cloner*, etc. Sélectionnez l’icône de deux-points **(:)** pour afficher d’autres options.

1. Sélectionnez **Charger des fichiers**.

1. Sélectionnez **Parcourir**, puis le fichier **Azure_Sentinel_analytic_rule.json** dans votre répertoire *Téléchargements*.

1. Sélectionner **Valider**.

1. Sélectionnez ensuite **Azure DevOps** dans le coin supérieur gauche de la page.  Votre organisation et vos projets s’affichent.

1. Sélectionnez **Paramètres de l’organisation** dans le coin inférieur gauche de la page.

1. Sélectionnez **Stratégies** dans la zone *Sécurité* du volet gauche.

1. **Activez***l’accès aux applications tierces via OAuth* dans la zone *Stratégies de connexion des applications*.


### Tâche 3 : connecter Sentinel à Azure DevOps

1. Sélectionnez l’onglet *Portail Azure*/*Microsoft Sentinel* dans votre navigateur.

1. Dans Microsoft Sentinel, dans la section *Gestion de contenu*, sélectionnez **Référentiels (préversion)**.

1. Sélectionnez le bouton **+ Ajouter nouveau** dans la barre d’outils.

1. Entrez **Mon contenu** pour le nom.

1. Pour Contrôle de code source, sélectionnez **Azure DevOps**.

1. Sélectionnez **Autoriser**. Faites défiler la demande d’autorisations vers le bas, puis sélectionnez **Accepter**.

1. Sélectionnez l’organisation que vous avez créée précédemment (par exemple, WWLx…).

1. Sélectionnez le projet que vous avez créé précédemment, *Mon contenu Sentinel*.

1. Sélectionnez le référentiel que vous avez créé précédemment, *Mon contenu Sentinel*. **Conseil :** vous devrez peut-être faire défiler la liste déroulante vers le bas pour afficher le référentiel.

1. Pour la branche, sélectionnez **Principal**. **Conseil :** vous devrez peut-être faire défiler la liste déroulante vers le bas pour afficher la branche.

1. Sélectionnez tous les types de contenu.

1. Sélectionnez ensuite **Créer**.

1. Revenez à l’espace de travail Microsoft Sentinel si nécessaire.

1. Accédez à la page *Référentiels (préversion),* et sélectionnez **Actualiser**. Patientez jusqu’à ce que l’*état du dernier déploiement* soit *Échec*.  

    >**Remarque :** L’état *Échec* est dû à des limitations dans l’environnement de labo hébergé. Vous verrez normalement *Réussi*. Vous pouvez ensuite voir dans *Analytics* la règle importée *Règle à partir d’AzureDevOps*.


## Vous avez terminé le labo.
