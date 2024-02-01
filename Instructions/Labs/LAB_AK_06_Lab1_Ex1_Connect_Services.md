---
lab:
  title: "Exercice\_1\_-\_Connecter des données à Microsoft Sentinel via des connecteurs de données"
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Parcours d'apprentissage 6 - Labo  1 - Exercice 1 - Connecter des données à Microsoft Sentinel via des connecteurs de données

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex1.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez apprendre à connecter des données de journal provenant de nombreuses sources de données dans votre organisation. L’organisation a des données provenant de Microsoft 365, de Microsoft 365 Defender, des ressources Azure, des machines virtuelles non-Azure, etc. Vous commencez à connecter les sources Microsoft en premier.

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Connect%20data%20to%20Microsoft%20Sentinel%20using%20data%20connectors)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 


### Tâche 1 : Accéder à l’espace de travail Microsoft Sentinel

Dans cette tâche, vous allez accéder à votre espace de travail Microsoft Sentinel.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu'Admin avec le mot de passe suivant : **Pa55w.rd**.  

1. Ouvrez le navigateur Microsoft Edge.

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez l’espace de travail Microsoft Sentinel que vous avez créé dans l'atelier précédent.

1. Dans le menu de navigation principal, sélectionnez Analyse.

1. Sélectionnez *Créer des incidents en fonction de Microsoft Defender pour le cloud* dans les modèles de règles.

1. Sélectionnez **Créer une règle** dans le volet d’informations des règles, ou sélectionnez les points de suspension (...) et **+ Créer une règle**.

1. Dans l’Assistant Règle analytique, sélectionnez **Suivant : Réponse automatique**, puis **Suivant : Vérifier et créer**.

1. Sélectionnez **Enregistrer**.

### Tâche 2 : connecter le connecteur de données Microsoft Defender pour le cloud.

Dans cette tâche, vous allez connecter le connecteur de données Microsoft Defender pour le cloud.

1. Dans les menus de gauche de Microsoft Sentinel, faites défiler jusqu’à la section *Gestion de contenu*, puis sélectionnez **Hub de contenu**.

1. Dans le *hub de contenu*, recherchez la solution **Microsoft Defender pour le cloud**, puis sélectionnez-la dans la liste.

1. Dans la page de solution *Microsoft Defender pour le cloud*, sélectionnez **Installer**.

1. Une fois l’installation terminée, sélectionnez **Gérer**.

    >**Remarque :** la solution *Microsoft Defender pour le cloud* installe le connecteur de données *Microsoft Defender pour le cloud basé sur un abonnement (hérité)*, le connecteur de données *Microsoft Defender pour le cloud basé sur le locataire (préversion)* et une règle analytique.

1. Activez la case à cocher du connecteur de données *Microsoft Defender pour le cloud basé sur un abonnement (hérité)*, puis sélectionnez **Ouvrir la page du connecteur**.

1. Dans la section *Configuration*, sous l’onglet *Instructions*, **cochez** la case correspondant à l’abonnement « Pass Azure - Parrainage » et faites glisser l’option **État** vers la droite.

    >**Remarque :** s’il revient au statut Déconnecté, consultez le Parcours d’apprentissage 3, Exercice 1, Tâche 1 pour attribuer les autorisations appropriées sur votre compte.

1. Le *statut* doit maintenant être **Connecté** et la « Synchronisation bidirectionnelle » doit être *Activée*.

1. Faites défiler vers le bas et sous la zone *Créer des incidents - Recommandé !*, vérifiez que *Créer automatiquement des incidents à partir de toutes les alertes générées dans ce service connecté* est **Activé**.

### Tâche 3 : connecter le connecteur de données Activité Azure

Dans cette tâche, vous allez connecter le connecteur de données *Activité Azure*.

1. Dans les menus de gauche de Microsoft Sentinel, faites défiler jusqu’à la section *Gestion de contenu*, puis sélectionnez **Hub de contenu**.

1. Dans le *Hub de contenu*, recherchez la solution **Activité Azure** et sélectionnez-la dans la liste.

1. Dans la page de la solution *Activité Azure*, sélectionnez **Installer**.

1. Une fois l’installation terminée, sélectionnez **Gérer**.

    >**Remarque :** la solution *Activité Azure* installe le connecteur de données *Activité Azure*, 12 règles analytiques, 14 requêtes de repérage, 1 classeur.

1. Sélectionnez le connecteur de données *Activité Azure*, puis **Ouvrir la page du connecteur**.

1. Dans la zone  *Configuration*, sous l’onglet *Instructions*, faites défiler jusqu'à « 2. Connecter vos abonnements… », sélectionnez **Lancer l’Assistant Attribution Azure Policy>**.

1. Dans l’onglet **Informations de base**, sous **Étendue**, sélectionnez le bouton en forme de points de suspension (…), puis sélectionnez votre abonnement « Pass Azure - Parrainage » dans la liste déroulante et cliquez sur **Sélectionner**.

1. Sélectionnez l’onglet **Paramètres**, choisissez votre espace de travail *nomuniqueDefender* dans la liste déroulante **Espace de travail Log Analytics principal**. Cette action appliquera la configuration de l’abonnement pour envoyer les informations à l’espace de travail Log Analytics.

1. Sélectionnez l’onglet **Correction** et cochez la case **Créer une tâche de correction**. Cette action applique la stratégie aux ressources Azure existantes.

1. Sélectionnez le bouton **Vérifier + créer** pour passer en revue la configuration.

1. Sélectionnez **Créer** pour terminer.

## Passez à l’exercice 2
