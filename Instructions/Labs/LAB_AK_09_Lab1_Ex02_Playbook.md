---
lab:
  title: "Exercice\_2 : créer un playbook"
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Parcours d’apprentissage 9 - Labo 1 - Exercice 2 - Créer un guide opérationnel dans Microsoft Sentinel

## Scénario de labo

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez apprendre à détecter et à atténuer les menaces à l’aide de Microsoft Sentinel. À présent, vous souhaitez répondre à des actions, et corriger des actions, qui peuvent être exécutées à partir de Microsoft Sentinel en tant que routine.

Un playbook peut vous aider à automatiser et orchestrer votre réponse aux menaces. Il peut s’intégrer à d’autres systèmes, aussi bien internes qu’externes, et être configuré pour s’exécuter automatiquement en réponse à des alertes ou des incidents spécifiques, lorsqu’il est déclenché par une règle analytique ou une règle d’automatisation, respectivement.

>**Important :** les exercices de laboratoire du parcours d’apprentissage #9 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Tâche 1 : créer un guide opérationnel dans Microsoft Sentinel

Dans cette tâche, vous allez créer une application logique utilisée comme playbook dans Microsoft Sentinel.

>**Remarque :** Microsoft Sentinel a été prédéployé dans votre abonnement Azure avec le nom **defenderWorkspace** et les solutions *Content Hub* requises ont été installées.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu'administrateur avec le mot de passe suivant : **Pa55w.rd**.  

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

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

1. Supprimez **for** et les *traits de soulignement* en trop du nom du playbook (le nom dépasserait la limite de 64 caractères). Il doit s’intituler : **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**.

1. Sélectionnez **Connexions**.

1. Sélectionnez **Suivant : Réviser et créer**.

1. À présent, sélectionnez **Créer un guide opérationnel**.

    >**Remarque :** attendez que le déploiement se termine avant de passer à la tâche suivante.

### Tâche 2 : mettre à jour un guide opérationnel dans Microsoft Sentinel

Dans cette tâche, vous allez mettre à jour le nouveau playbook que vous avez créé avec les informations de connexion appropriées.

1. Une fois la tâche précédente terminée, vous devriez vous trouver sur la page *Defender_XDR_Ransomware_Playbook_SecOps-Tasks | Concepteur de logique d’application*. Si ce n’est pas le cas, effectuez les étapes 1 à 5 ci-dessous.

1. Dans la barre de recherche du portail Azure, tapez Sentinel, puis sélectionnez Microsoft Sentinel.

1. Sélectionnez votre espace de travail Microsoft Sentinel.

1. Sélectionnez Automatisation sous la zone Configuration, puis sélectionnez l’onglet *Playbooks actifs*.

1. Sélectionnez Actualiser dans la barre de commandes si vous ne voyez aucun guide opérationnel. Vous devez voir le playbook créé à l’étape précédente.

1. Sélectionnez le lien du nom du guide opérationnel **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**.

1. Dans le menu de commandes de la page Concepteur d’applications logiques de **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**, sélectionnez Modifier.

    >**Remarque :** il peut être nécessaire d’actualiser la page.

1. Sélectionnez le premier bloc, incident Microsoft Sentinel.

1. Sélectionnez le lien **Modifier la connexion***.

1. Sélectionnez **Ajouter** et sélectionnez **Se connecter**. Dans la nouvelle fenêtre, sélectionnez les informations d’identification d’administrateur de votre abonnement Azure lorsque vous y êtes invité. La dernière ligne du bloc doit maintenant indiquer « Connecté à votre-identifiant-d’administrateur ».

<!--- 1. Below within the logic split (+ sign), select Add an action to incident.--->

1. Sélectionnez **Enregistrer** sur la barre de commandes.

1. Sélectionnez le **X** pour fermer la fenêtre. L’application logique sera utilisée dans un prochain labo.

### Tâche 3 : créer une règle d’automatisation

1. Dans Microsoft Sentinel, développez *Configuration* dans le menu de navigation, puis sélectionnez *Automatisation*.

1. Sélectionnez **+ Créer**, puis choisissez **Règle d’automatisation**.

1. Nommez la règle.

1. Laissez le *déclencheur* sur **Lorsqu’un incident est créé**.

1. Sous *Conditions*, laissez le fournisseur d’incident sur *Tout*.

1. Laissez le *nom de la règle analytique* sur *Tout*.

1. Sélectionnez **+ Ajouter** et choisissez *Condition (Et)*.

1. Dans le menu déroulant, sélectionnez **Tactiques**.

1. Sélectionnez l’opérateur **Contient** dans la liste déroulante.

1. Sélectionnez les tactiques suivantes *Valeurs* :
    - Reconnaissance
    - Exécution
    - Persistance
    - Commande et contrôle
    - Exfiltration
    - PreAttack

1. Sous Actions, sélectionnez **Exécuter le playbook**.

1. Sélectionnez le lien **Gérer les autorisations du guide opérationnel**.

1. Sur la page *Gérer les autorisations* , sélectionnez le groupe de ressources **RG Playbooks** que vous avez créé dans le labo précédent, puis sélectionnez **Appliquer**.

1. Dans la liste déroulante, sélectionnez le playbook **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**.

1. Sélectionnez **Appliquer** en bas.

1. Sélectionnez le **X** dans la fenêtre *Créer une nouvelle règle d’automatisation* pour la fermer.

Vous avez maintenant créé un guide opérationnel et une règle d’automatisation dans Microsoft Sentinel.

## Passez à l’exercice 3
