---
lab:
  title: "Exercice\_1\_-\_Connecter des données à Microsoft Sentinel via des connecteurs de données"
  module: Learning Path 8 - Connect logs to Microsoft Sentinel
---

# Parcours d’apprentissage 8 - Labo 1 - Exercice 1 - Connecter des données à Microsoft Sentinel via des connecteurs de données

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex1.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez apprendre à connecter des données de journal provenant de nombreuses sources de données dans votre organisation. L’organisation a des données provenant de Microsoft 365, de Microsoft 365 Defender, des ressources Azure, des machines virtuelles non-Azure, etc. Vous commencez à connecter les sources Microsoft en premier.

>**Important :** les exercices de laboratoire du parcours d’apprentissage #8 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Temps estimé pour terminer ce labo : 20 minutes

### Tâche 1 : Accéder à l’espace de travail Microsoft Sentinel

Dans cette tâche, vous allez accéder à votre espace de travail Microsoft Sentinel.

>**Remarque :** Microsoft Sentinel a été prédéployé dans votre abonnement Azure avec le nom **defenderWorkspace** et les solutions *Content Hub* requises ont été installées.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu'Admin avec le mot de passe suivant : **Pa55w.rd**.  

1. Ouvrez le navigateur Microsoft Edge.

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez le **defenderWorkspace** Microsoft Sentinel.

1. Passez à la tâche suivante.

### Tâche 2 : connecter le connecteur de données Microsoft Defender pour le cloud.

Dans cette tâche, vous allez connecter le connecteur de données Microsoft Defender pour le cloud.

   <!--- >>**Important:** To *Enable* Bi-directional sync, please rerun  **[Lab 05 Exercise 1](https://microsoftlearning.github.io/SC-200T00A-Microsoft-Security-Operations-Analyst/Instructions/Labs/LAB_AK_05_Lab1_Ex01_Enable_MDC.html)**, Task 2, and select **Setup** from the *Microsoft Defender for Cloud* navigation menu to verify all eligible Azure subscriptions are onboarded. --->

1. Dans le menu de navigation de Microsoft Sentinel, faites défiler jusqu’à la section **Gestion du contenu**, puis sélectionnez **Hub de contenu**.

1. Dans le *hub de contenu*, recherchez la solution **Microsoft Defender pour le cloud**, puis sélectionnez-la dans la liste.

1. Dans la page des détails de la solution *Microsoft Defender pour le cloud*, sélectionnez **Gérer**.

    >**Remarque :** la solution *Microsoft Defender pour le cloud* installe le connecteur de données *Microsoft Defender pour le cloud basé sur un abonnement (hérité)*, le connecteur de données *Microsoft Defender pour le cloud basé sur le locataire (préversion)* et une règle analytique. Le connecteur de données *Microsoft Defender pour le cloud basé sur le locataire (Préversion)* est utilisé quand un tenant a plusieurs abonnements.

1. Activez la case à cocher du connecteur de données *Microsoft Defender pour le cloud basé sur un abonnement (hérité)*, puis sélectionnez **Ouvrir la page du connecteur**.

1. Dans la section *Configuration*, **cochez** la case pour l’*abonnement MOC-XXXXXXXXXXXXX*, puis sélectionnez le lien **Se connecter**, ou faites glisser l’option **État** à droite.

1. Pour activer la synchronisation bidirectionnelle, sélectionnez le lien **Activer Microsoft Defender pour tous les abonnements**.

1. Dans la page *Microsoft Defender pour le cloud - Prise en main*, la case à cocher de l’*abonnement MOC-XXXXXXXXXXXXX* doit être sélectionnée, et le *plan Microsoft Defender* doit afficher *Activé - Partiel (30 jours d’essai restants)*.

1. Cliquez sur le bouton **X (Fermer)** dans le coin supérieur droit pour fermer la page *Prise en main*. Vous devriez retourner sur la page de configuration de *Microsoft Defender pour le cloud*.

1. L’*État* de l’*abonnement MOC-XXXXXXXXXXX* doit maintenant être **Connecté**, et la *Synchronisation bidirectionnelle* doit être *Activée*.

    <!--- 1. Scroll down and under the *Create incidents - Recommended!* area, verify that *Create incidents automatically from all alerts generated in this connected service* is **Enabled**. --->

### Tâche 3 : connecter le connecteur de données Activité Azure

Dans cette tâche, vous allez connecter le connecteur de données *Activité Azure*.

1. Dans le menu de navigation de Microsoft Sentinel, faites défiler jusqu’à la section *Gestion du contenu*, puis sélectionnez **Hub de contenu**.

1. Dans le *Hub de contenu*, recherchez la solution **Activité Azure** et sélectionnez-la dans la liste.

1. Dans la page des détails de la solution *Activité Azure*, sélectionnez **Gérer**.

    >**Note :** la solution *Activité Azure* installe le connecteur de données *Activité Azure*, 13 règles analytiques, 14 requêtes de repérage, 1 classeur.

1. Sélectionnez le connecteur de données *Activité Azure*, puis **Ouvrir la page du connecteur**.

1. Dans la zone  *Configuration*, sous l’onglet *Instructions*, faites défiler jusqu'à « 2. Connecter vos abonnements… », sélectionnez **Lancer l’Assistant Attribution Azure Policy>**.

1. Dans l’onglet **Informations de base**, sélectionnez le bouton représentant des points de suspension (…) sous **Étendue**, puis choisissez votre abonnement *MOC Subscription-XXXXXXXXXXX* dans la liste déroulante et enfin, cliquez sur **Sélectionner**.

    >**Note :*** ne sélectionnez pas* de groupe de ressources facultatif.

1. Sélectionnez l’onglet **Paramètres**, choisissez votre espace de travail *nomuniqueDefender* dans la liste déroulante **Espace de travail Log Analytics principal**. Cette action appliquera la configuration de l’abonnement pour envoyer les informations à l’espace de travail Log Analytics.

1. Sélectionnez l’onglet **Correction** et cochez la case **Créer une tâche de correction**. Cette action applique la stratégie aux ressources Azure existantes.

1. Sélectionnez le bouton **Vérifier + créer** pour passer en revue la configuration.

1. Sélectionnez **Créer** pour terminer.

## Passez à l’exercice 2
