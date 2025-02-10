---
lab:
  title: "Exercice\_3\_: créer une requête planifiée à partir d’un modèle"
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Parcours d’apprentissage 9 - Labo 1 - Exercice 3 - Créer une requête planifiée à partir d’un modèle

## Scénario de labo

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez apprendre à détecter et à atténuer les menaces à l’aide de Microsoft Sentinel. Une fois que vous avez connecté vos sources de données à Microsoft Sentinel, créez des règles d’analyse personnalisées pour faciliter la détection des menaces et comportements anormaux au sein de votre environnement.

Les règles analytiques recherchent des événements ou des ensembles d'événements spécifiques au sein de votre environnement, vous préviennent lorsque certains seuils ou conditions d’événements sont atteints, génèrent des incidents que votre centre des opérations de sécurité (SOC) doit trier et examiner, et répondent aux menaces grâce à des processus de suivi et de correction automatisés.

>**Important :** les exercices de laboratoire du parcours d’apprentissage #9 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Temps estimé pour terminer ce labo : 45 minutes

>**Remarque :** Microsoft Sentinel a été prédéployé dans votre abonnement Azure avec le nom **defenderWorkspace** et les solutions *Content Hub* requises ont été installées.

<!--- >>**Important:** To sucessfully complete this task you wil need to rerun Task 3 of **[Lab 08 Exercise 1](https://microsoftlearning.github.io/SC-200T00A-Microsoft-Security-Operations-Analyst/Instructions/Labs/LAB_AK_08_Lab1_Ex01_Connect_Services.html)** to connect the Azure Activity data connector. --->

Pour effectuer correctement cette tâche, vous devez effectuer les tâches préalables suivantes.

### Tâche préalable : connecter le connecteur de données Activité Azure

Dans cette tâche, vous allez connecter le connecteur de données *Activité Azure*.

1. Dans le menu de navigation de Microsoft Sentinel, faites défiler jusqu’à la section *Gestion du contenu*, puis sélectionnez **Hub de contenu**.

1. Dans le *Hub de contenu*, recherchez la solution **Activité Azure** et sélectionnez-la dans la liste.

1. Dans la page des détails de la solution *Activité Azure*, sélectionnez **Gérer**.

    >**Remarque :** la solution *Activité Azure* installe le connecteur de données *Activité Azure*, 12 règles analytiques, 14 requêtes de repérage, 1 classeur.

1. Sélectionnez le connecteur de données *Activité Azure*, puis **Ouvrir la page du connecteur**.

1. Dans la zone  *Configuration*, sous l’onglet *Instructions*, faites défiler jusqu'à « 2. Connecter vos abonnements… », sélectionnez **Lancer l’Assistant Attribution Azure Policy>**.

1. Dans l’onglet **Informations de base**, sélectionnez le bouton représentant des points de suspension (…) sous **Étendue**, puis choisissez votre abonnement *MOC Subscription-XXXXXXXXXXX* dans la liste déroulante et enfin, cliquez sur **Sélectionner**.

1. Sélectionnez l’onglet **Paramètres**, choisissez votre espace de travail *nomuniqueDefender* dans la liste déroulante **Espace de travail Log Analytics principal**. Cette action appliquera la configuration de l’abonnement pour envoyer les informations à l’espace de travail Log Analytics.

1. Sélectionnez l’onglet **Correction** et cochez la case **Créer une tâche de correction**. Cette action applique la stratégie aux ressources Azure existantes.

1. Sélectionnez le bouton **Vérifier + créer** pour passer en revue la configuration.

1. Sélectionnez **Créer** pour terminer.

1. Attendez que le connecteur de données *Activité Azure* affiche un état *Connecté* avant de continuer.

### Tâche 1 : créer une règle de requête planifiée

Dans cette tâche, vous créez une *règle de requête planifiée d’analytique Microsoft Sentinel*.

>**Note :** les tâches suivantes fonctionnent actuellement mieux dans le portail Azure en version préliminaire : <https://preview.portal.azure.com/>.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez le **defenderWorkspace** Microsoft Sentinel.

1. Dans la zone Configuration, sélectionnez **Analyses**.

1. Vérifiez que vous êtes dans l’onglet *Modèles de règle* dans la barre de commandes et recherchez la règle **Nouvel utilisateur CloudShell**.

1. Dans le panneau Résumé de la règle, vérifiez que vous recevez des données en examinant l’icône verte sous *Sources de données : activité Azure*.

    >**Note :** si vous ne le voyez pas dans un état connecté et que vous avez exécuté la *tâche préalable* ci-dessus, vous devrez peut-être attendre plus longtemps que le processus se termine.

1. Sélectionnez **Créer la règle** pour continuer.

1. Dans l’Assistant Règle d’analytique, sous l’onglet *Général*, définissez le niveau de *Gravité* sur **Moyen**.

1. Sélectionnez le bouton **Suivant : Définir la logique de règle >**  :

1. Pour la requête de règle, sélectionnez **Afficher les résultats de la requête**. Vous ne devriez plus recevoir de résultats ni d’erreurs.

1. Fermez la fenêtre *Journaux* en sélectionnant le bouton **X** en haut à droite, puis sélectionnez **OK** pour ignorer l’enregistrement des modifications et revenir à l’Assistant.

1. Faites défiler vers le bas et sous *Planification des requêtes*, spécifiez les paramètres suivants :

    |Paramètre|Valeur|
    |---|---|
    |Exécuter la requête toutes les|5 minutes|
    |Rechercher les données des dernières|1 jour|

    >**Remarque :** nous générons volontairement de nombreux incidents pour les mêmes données. Cela permet au labo d’utiliser ces alertes.

1. Dans la zone *Seuil d’alerte*, laissez la valeur inchangée, car nous voulons que l’alerte enregistre chaque événement.

1. Dans la zone *Regroupement d’événements*, laissez l’option **Regrouper tous les événements dans une seule alerte** sélectionnée, car nous voulons générer une alerte unique à chaque exécution, tant que la requête renvoie plus de résultats que le seuil d’alerte spécifié ci-dessus.

1. Sélectionnez le bouton **Suivant : Paramètres d’incident >**.

1. Sous l’onglet *Paramètres d’incident*, passez en revue les options par défaut.

1. Sélectionnez le bouton **Suivant : Réponse automatisée >** 

1. Sélectionnez le bouton **Suivant : Vérifier et créer >**.
  
1. Cliquez sur **Enregistrer**.

### Tâche 2 : modifier votre nouvelle règle

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez votre espace de travail Microsoft Sentinel.

1. Dans la zone Configuration, sélectionnez **Analyses**.

1. Vérifiez que vous êtes dans l’onglet *Règles actives* dans la barre de commandes et sélectionnez la règle **Nouvel utilisateur CloudShell**.

1. Cliquez avec le bouton droit sur la règle et sélectionnez **Modifier** dans le *menu contextuel*.

1. Sélectionnez le bouton **Suivant : définir la logique de la règle >**.

1. Sélectionnez le bouton **Suivant : Paramètres d’incident >**.

1. Sélectionnez le bouton **Suivant : Réponse automatisée >** 

1. Dans l’onglet *Réponse automatique*, sous *Règles d’automatisation*, sélectionnez **+Ajouter nouveau**.

1. Pour le *Nom de la règle d’automatisation*, saisissez **Niveau 2**.

1. Pour les *Actions*, sélectionnez **Attribuer un propriétaire**.

1. Sélectionnez ensuite **Attribuer à moi-même**.

1. Sélectionnez **Appliquer**

1. Sélectionnez le bouton **Suivant : Vérifier et créer >**.
  
1. Cliquez sur **Enregistrer**.

### Tâche 3 : tester votre nouvelle règle

Dans cette tâche, vous testez votre nouvelle règle de requête planifiée.

1. Dans la barre supérieure du Portail Azure, sélectionnez l’icône **>_** correspondant à Cloud Shell. Vous devrez peut-être d’abord sélectionenr l'icône représentant des points de suspension **(...)** si votre résolution d’affichage est trop faible.

1. Dans la fenêtre *Bienvenue dans Azure Cloud Shell*, sélectionnez **PowerShell**.

1. Sur la page *Prise en main*, sélectionnez **Monter un compte de stockage**, puis sélectionnez votre **abonnement MOC-XXXXXXXXXXX** à partir de l’élément de menu déroulant *Abonnement du compte de stockage* et sélectionnez le bouton **Appliquer**.

    >**Important :** Ne sélectionnez pas l'option de bouton radio *Aucun compte de stockage requis*. Cela entraîne l’échec de la création de l’incident.

1. Sur la page *Monter le compte de stockage*, sélectionnez **Nous allons créer un compte de stockage pour vous**, puis sélectionner **Suivant**.

1. Attendez que Cloud Shell soit provisionné, puis fermez la fenêtre Azure Cloud Shell.

1. Dans la barre de recherche du portail Azure, tapez *Activité*, puis sélectionnez **Journal d’activité**.

1. Vérifiez si les éléments *Nom de l’opération* s’affichent : **Répertorier les clés d’accès aux comptes de stockage**et  **Mettre à jour les comptes de stockage créés**. Il s’agit des opérations que la requête KQL que vous avez examinée précédemment mettra en correspondance pour générer l’alerte. **Conseil :** vous devrez peut-être sélectionner **Actualiser** pour mettre à jour la liste.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez votre espace de travail Microsoft Sentinel.

1. Sélectionnez l’option de menu **Incidents** sous *Gestion des  menaces*.

1. Sélectionnez le bouton bascule **Actualiser automatiquement les incidents**.

1. L’environnement venant d’être créé devrait s’afficher.

    >**Remarque :** l’événement qui déclenche l’incident peut prendre 5 minutes de plus. Continuez avec l’exercice suivant. Vous reviendrez à cette vue après.

1. Sélectionnez l’incident et passez en revue les informations dans le panneau droit.

## Passer à l’Exercice 4
