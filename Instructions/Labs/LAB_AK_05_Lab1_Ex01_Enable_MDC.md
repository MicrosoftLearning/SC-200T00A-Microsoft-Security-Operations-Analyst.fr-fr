---
lab:
  title: "Exercice\_1\_: activer Microsoft\_Defender pour le cloud"
  module: Learning Path 5 - Mitigate threats using Microsoft Defender for Cloud
---

# Parcours d’apprentissage 5 - Labo 1 - Exercice 1 - Activer Microsoft Defender pour le cloud

## Scénario de labo

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise qui met en œuvre la protection des charges de travail en cloud avec Microsoft Defender pour le cloud. Dans ce labo, vous allez activer Microsoft Defender pour le cloud.

>**Important :** les exercices de laboratoire du parcours d’apprentissage #5 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Temps estimé pour terminer ce labo : 25 minutes

### Tâche 1 : connexion à un serveur local

Dans cette tâche, vous allez connecter un serveur local à votre abonnement Azure. Azure Arc a été préinstallé sur ce serveur. Le serveur sera utilisé dans les exercices suivants pour fournir une ressource permettant d’appliquer des normes de conformité et des protections de charge de travail.

>**Important :** les étapes suivantes sont effectuées sur une machine différente de celle que vous utilisiez précédemment. Recherchez le nom de l’ordinateur virtuel dans l’onglet des références.

1. Connectez-vous à la machine virtuelle **WINServer** en tant qu'Administrateur avec le mot de passe suivant : **Passw0rd!** si nécessaire.  

Comme décrit ci-dessus, Azure Arc a été préinstallé sur la machine **WINServer**. Vous allez maintenant connecter cette machine à votre abonnement Azure.

1. Sur la machine *WINServer*, sélectionnez l’icône de *recherche* et entrez **cmd**.

1. Dans les résultats de la recherche, cliquez sur *Invite de commandes* avec le bouton droit, puis sélectionnez **Exécuter en tant qu’administrateur**.

1. Dans la fenêtre d’invite de commandes, tapez la commande suivante : *N’appuyez pas sur Entrée* :

    ```cmd
    azcmagent connect -g "defender-RG" -l "EastUS" -s "Subscription ID string"
    ```

1. Remplacez la **chaîne d’ID d’abonnement** par l’*ID d’abonnement* fourni par votre hébergeur de labo (*onglet Ressources). Veillez à conserver les guillemets.

1. Appuyez sur **Entrée** pour exécuter la commande (cela peut prendre quelques minutes).

    >**Remarque** : si vous voyez la fenêtre de sélection de navigateur *Comment voulez-vous ouvrir ceci ?*, sélectionnez **Microsoft Edge**. 

1. Dans la boîte de dialogue *Connexion*, entrez l’**e-mail du locataire** et le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**. Attendez le message *Authentification terminée*, fermez l’onglet du navigateur et revenez à la fenêtre *Invite de commandes*.

1. Une fois les commandes exécutées, laissez la fenêtre *Invite de commandes* ouverte et entrez la commande suivante pour vérifier que la connexion a réussi :

    ```cmd
    azcmagent show
    ```

1. Dans la sortie de la commande, vérifiez que l’*état de l’agent* est **Connecté**.

### Tâche 2 : activer Microsoft Defender pour le cloud

Dans cette tâche, vous allez activer et configurer Microsoft Defender pour le cloud.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu'Admin avec le mot de passe suivant : **Pa55w.rd**.

1. Dans le navigateur Microsoft Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.
  
1. Dans la boîte de dialogue **Se connecter** , copiez et collez le compte de messagerie du locataire pour le nom d’utilisateur administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le mot de passe du locataire de l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Se connecter**.

1. Dans la barre de recherche du portail Microsoft Azure, saisissez *Defender*, puis sélectionnez **Microsoft Defender pour le cloud**.

1. Dans le menu de navigation de gauche de Microsoft Defender pour le cloud, développez la section *Gestion*, puis sélectionnez **Paramètres d’environnement**.

1. Sélectionnez le **bouton Développer tout** pour afficher tous les abonnements et toutes les ressources.

1. Sélectionnez l’abonnement **MOC Subscription-lodxxxxxxxx** (ou le nom équivalent dans votre langue).

1. Passez en revue les ressources Azure qui sont désormais protégées avec les plans de Defender pour le cloud.

    >**Important :** Si tous les plans Defender sont dans un état *Désactivé*, sélectionnez **Activer tous les plans**. Sélectionnez le *plan 1 à 200 $/mois de Microsoft Defender pour API*, puis **Enregistrer**. Sélectionnez **Enregistrer** en haut de la page et attendez que les notifications « *Les plans Defender (pour vos ressources) dans votre abonnement ont été enregistrés* » s’affichent.

1. Dans la zone Paramètres (en regard d’Enregistrer), sélectionnez l’onglet **Paramètres et surveillance**.

1. Passez en revue les extensions de surveillance. Elles comprennent des configurations pour les machines virtuelles, les conteneurs et les comptes de stockage.

1. Sélectionnez le bouton **Continuer** ou fermez la page « Paramètres et surveillance » en cliquant sur le bouton X dans le coin supérieur droit de la page.

1. Fermez la page Paramètres en sélectionnant le X en haut à droite de la page pour revenir aux **Paramètres d’environnement**.

<!---1. Select the Log analytics workspace you created earlier *uniquenameDefender* to review the available options and pricing.

1. Select **Enable all plans** (to the right of Select Defender plan) and then select **Save**. Wait for the *"Microsoft Defender plan for workspace uniquenameDefender were saved successfully!"* notification to appear.

    >**Note:** If the page is not being displayed, refresh your Edge browser and try again.

1. Close the Defender plans page by selecting the 'X' on the upper right of the page to go back to the **Environment settings**. --->

### Tâche 3 : comprendre le tableau de bord de Microsoft Defender pour le cloud

1. Dans la barre de recherche du portail Microsoft Azure, saisissez *Defender*, puis sélectionnez **Microsoft Defender pour le cloud**.

1. Dans le menu de navigation de gauche de Microsoft Defender pour le cloud, dans la section *Général*, sélectionnez **Vue d’ensemble**.

1. Le panneau Vue d’ensemble fournit une vue unifiée de la posture de sécurité et inclut plusieurs piliers de sécurité cloud indépendants tels que la posture de sécurité, la conformité réglementaire, les protections de charges de travail, Firewall Manager, l’Inventaire, et la Protection des données (version préliminaire). Chacun de ces piliers possède également son tableau de bord dédié permettant d’obtenir des informations approfondies et de réaliser des actions plus précises sur cette branche, offrant un accès facile et une meilleure visibilité pour les professionnels de la sécurité.

    >**Note :** la barre de menus supérieure vous permet d’afficher et de filtrer les abonnements en sélectionnant le bouton Abonnements. Dans ce labo, nous n’utiliserons qu’un seul abonnement, mais la sélection d’abonnements différents/supplémentaires ajuste l’interface pour refléter la posture de sécurité des abonnements sélectionnés.

1. Cliquez sur l’icône **Nouvelles** : un nouvel onglet s’ouvre avec les dernières notes de publication où vous pouvez vous tenir informé des nouvelles fonctionnalités, des correctifs de bogues, etc.

    >**Note :** les nombres apparaissant dans le menu supérieur vous permettent de consulter le récapitulatif de vos abonnements, recommandations actives et alertes de sécurité, ainsi que les comptes cloud connectés.

1. Dans la barre de menu supérieure, sélectionnez **Abonnements Azure**. Vous accédez alors aux paramètres d’environnement dans lesquels vous pouvez choisir parmi les abonnements disponibles.

1. Revenez à la page **Vue d’ensemble** et examinez la vignette **Posture de sécurité**. Vous pouvez voir votre *Niveau de sécurité* actuel, ainsi que le nombre de recommandations et de contrôles terminés. Sélectionner cette vignette vous redirige vers une vue d’exploration détaillée des abonnements.

1. Dans la vignette **Conformité réglementaire**, vous pouvez obtenir des informations sur votre posture de conformité en fonction de l’évaluation continue des environnements cloud Azure et cloud hybride. Cette vignette présente les normes suivantes : le benchmark de sécurité du cloud Microsoft et la norme de conformité réglementaire la plus basse. Pour afficher les données, nous devons d’abord ajouter des stratégies de sécurité.

1. La sélection de cette vignette vous redirige vers le tableau de bord de la **Conformité réglementaire**, où vous pouvez ajouter des normes supplémentaires et explorer les normes actuelles.

1. Nous allons continuer à explorer la **Posture de sécurité** et la **Conformité réglementaire** de *Microsoft Defender pour le cloud* au cours de l’exercice suivant.

## Passez à l’exercice 2
