---
lab:
  title: "Exercice\_2 : créer un playbook"
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Parcours d’apprentissage 9 - Labo 1 - Exercice 2 - Créer un guide opérationnel dans Microsoft Sentinel

## Scénario de labo

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez apprendre à détecter et à atténuer les menaces à l’aide de Microsoft Sentinel. À présent, vous souhaitez répondre et corriger des actions qui peuvent être exécutées à partir de Microsoft Sentinel en tant que routine.

Un playbook peut vous aider à automatiser et orchestrer votre réponse aux menaces. Il peut s’intégrer à d’autres systèmes, aussi bien internes qu’externes, et être configuré pour s’exécuter automatiquement en réponse à des alertes ou des incidents spécifiques, lorsqu’il est déclenché par une règle analytique ou une règle d’automatisation, respectivement.

>**Important :** les exercices de laboratoire du parcours d’apprentissage #9 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Tâche 1 : créer un guide opérationnel dans Microsoft Sentinel

Dans cette tâche, vous allez créer une application logique utilisée comme playbook dans Microsoft Sentinel.

>**Remarque :** Microsoft Sentinel a été prédéployé dans votre abonnement Azure avec le nom **defenderWorkspace** et les solutions *Content Hub* requises ont été installées.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez le **defenderWorkspace** Microsoft Sentinel.

1. Dans *Microsoft Sentinel*, accédez au **Hub de contenu**.

1. Dans la barre de recherche, recherchez **Sentinel SOAR Essentials**.

1. Sélectionnez la solution qui apparaît dans les résultats.

1. Dans les détails de la solution, sélectionnez **Gérer**.

1. Recherchez le guide opérationnel **Defender_XDR_Ransomware_Playbook_for_SecOps-Tasks** et sélectionnez-le.

1. Sélectionnez le modèle **Incident tasks - Microsoft Defender XDR Ransomware Playbook for SecOps**.

1. Sélectionnez **Créer un guide opérationnel** dans le volet Détails.

1. Pour le groupe de ressources, sélectionnez **Créer**, saisissez **RG-Playbooks** et sélectionnez OK.

1. Supprimez **for** du nom (la limite de 64 caractères est dépassée).

1. Sélectionnez **Connexions**.

1. Sélectionnez **Suivant : Réviser et créer**.

1. À présent, sélectionnez **Créer un guide opérationnel**.

    >**Remarque :** attendez que le déploiement se termine avant de passer à la tâche suivante.

### Tâche 2 : mettre à jour un guide opérationnel dans Microsoft Sentinel

Dans cette tâche, vous allez mettre à jour le nouveau guide opérationnel que vous avez créé avec les informations de connexion appropriées.

1. Dans la barre de recherche du portail Azure, tapez Sentinel, puis sélectionnez Microsoft Sentinel.

1. Sélectionnez votre espace de travail Microsoft Sentinel.

1. Sélectionnez Automatisation sous la zone Configuration, puis sélectionnez l’onglet Playbooks actifs.

1. Sélectionnez Actualiser dans la barre de commandes si vous ne voyez aucun guide opérationnel. Vous devez voir le playbook créé à l’étape précédente.

1. Sélectionnez le nom du guide opérationnel **Defender_XDR_Ransomware_Playbook_for_SecOps_Tasks**.

1. Dans la page Application logique pour **Defender_XDR_Ransomware_Playbook_for_SecOps_Tasks**, dans le menu de commandes, sélectionnez Modifier.

    >**Remarque :** il peut être nécessaire d’actualiser la page.

1. Sélectionnez le premier bloc, incident Microsoft Sentinel.

1. Sélectionnez le lien Modifier la connexion.

1. Sélectionnez Ajouter et sélectionnez Se connecter. Dans la nouvelle fenêtre, sélectionnez les informations d’identification d’administrateur de votre abonnement Azure lorsque vous y êtes invité. La dernière ligne du bloc doit maintenant indiquer « Connecté à votre-identifiant-d’administrateur ».

1. Dans le fractionnement logique, en bas, sélectionnez Ajouter une tâche à l’incident.

1. Sélectionnez Enregistrer sur la barre de commandes. L’application logique sera utilisée dans un prochain labo.

### Tâche 3 : créer une règle d’automatisation

1. Dans Microsoft Sentinel, accédez à Automatisation, dans Configuration.

1. Sélectionnez Créer, puis choisissez Règle d’automatisation.

1. Nommez la règle.

1. Laissez le fournisseur d’incidents sur Tous.

1. Laissez le nom de la règle analytique sur Tous.

1. Cliquez sur Ajouter, puis choisissez Et.

1. Sélectionnez Tactiques dans la liste déroulante.

1. Sélectionnez l’opérateur **Contient** dans la liste déroulante.

1. Sélectionnez les tactiques suivantes :
    - Reconnaissance
    - Exécution
    - Persistance
    - Commande et contrôle
    - Exfiltration
    - PreAttack

1. Dans Actions, sélectionnez Exécuter le guide opérationnel.

1. Sélectionnez le lien **Gérer les autorisations du guide opérationnel**.

1. Sur la page *Gérer les autorisations* , sélectionnez le groupe de ressources **RG Playbooks** que vous avez créé dans le labo précédent, puis sélectionnez **Appliquer**.

1. Dans la liste déroulante, sélectionnez le guide opérationnel **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**.

1. Sélectionnez **Appliquer** en bas.

À partir de là, en fonction de votre rôle, vous allez soit continuer à effectuer davantage d’exercices d’architecte, soit passer aux exercices d’analyste.

## Passez à l’exercice 3
