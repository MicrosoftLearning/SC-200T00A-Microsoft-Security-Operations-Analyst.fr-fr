---
lab:
  title: 'Exercice 4 : connecter Defender XDR à Microsoft Sentinel en tirant parti de connecteurs de données'
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Parcours d’apprentissage 6 : Labo 1 – Exercice 4 – Connecter Defender XDR à Microsoft Sentinel en tirant parti de connecteurs de données

## Scénario de labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex4.png)

Vous êtes Analyste des opérations de sécurité et vous travaillez dans une entreprise qui a déployé Microsoft Defender XDR et Microsoft Sentinel. Vous devez préparer la Plateforme d’opérations de sécurité unifiée qui connecte Microsoft Sentinel à Defender XDR. Votre étape suivante consiste à installer la solution Hub de contenu Defender XDR et à déployer le connecteur de données Defender XDR dans Microsoft Sentinel.

>**Important :** Notez qu’il existe des différences de fonctionnalités entre le portail Microsoft Sentinel d’Azure et Sentinel dans le portail Microsoft Defender XDR **[Différences de fonctionnalités des portails](https://learn.microsoft.com/azure/sentinel/microsoft-sentinel-defender-portal#capability-differences-between-portals)**.

### Tâche 1 : Connecter Defender XDR

Dans cette tâche, vous déployez le connecteur Microsoft Defender XDR.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur avec le mot de passe suivant : **Pa55w.rd**.  

1. Dans le navigateur Microsoft Edge, accédez au Portail Azure sur (<https://portal.azure.com>).

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez l’espace de travail Microsoft Sentinel que vous avez créé précédemment.

1. Dans les menus de gauche de Microsoft Sentinel, faites défiler jusqu’à la section **Gestion de contenu**, puis sélectionnez **Hub de contenu**.

1. Dans le *Hub de contenu*, recherchez la solution **Microsoft Defender XDR**, puis sélectionnez-la dans la liste.

1. Dans la page des détails de la solution *Microsoft Defender XDR*, sélectionnez **Installer**.

1. Une fois l’installation terminée, recherchez la solution **Microsoft Defender XDR**, puis sélectionnez-la.

1. Dans la page des détails de la solution *Microsoft Defender XDR*, sélectionnez **Gérer**

>**Remarque :** La solution *Microsoft Defender XDR*installe le connecteur de données *Microsoft Defender XDR*, les requêtes de repérage, les classeurs et les règles analytiques.

1. Sélectionnez la case à cocher du connecteur de données *Microsoft Defender XDR*, puis sélectionnez la **page Ouvrir le connecteur**.

1. Dans la section *Configuration*, sous l’onglet *Instructions*, **désélectionnez** la case à cocher pour l’option *Désactiver toutes les règles de création d’incident Microsoft pour ces produits. Recommandé*, puis sélectionnez le bouton **Connecter des incidents et des alertes**.

1. Vous devez voir un message indiquant que la connexion a réussi.

### Tâche 2 : Connectez Microsoft Sentinel à Microsoft Defender XDR

Dans cette tâche, vous allez connecter un espace de travail Microsoft Sentinel à Microsoft Defender XDR.

>**Remarque :** Microsoft Sentinel dans le portail Microsoft Defender XDR est en préversion publique et l’expérience et les étapes de l’interface utilisateur peuvent différer des instructions du labo.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu’*Administrateur* avec le mot de passe : **Pa55w.rd**.  

1. Ouvrez le navigateur Microsoft Edge.

1. Dans le navigateur Edge, accédez au portail Microsoft Defender XDR à l’adresse (https://security.microsoft.com).

1. Dans la boîte de dialogue **Se connecter** , copiez et collez le compte de messagerie du locataire pour le nom d’utilisateur administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le mot de passe du locataire de l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Se connecter**.

    >**Conseil :** le compte de messagerie et le mot de passe du locataire de l’administrateur sont disponibles sous l’onglet Ressources.

1. Sur le portail **Defender XDR**, sur la **page d’accueil**, vous devez voir une bannière en haut avec le message *Obtenir votre SIEM et XDR à un seul endroit*. Sélectionnez le bouton **Connecter un espace de travail**.

1. Sur la page *Choisir un espace de travail*, sélectionnez l’espace de travail **Microsoft Sentinel** que vous avez créé précédemment.

    >**Conseil :** Il doit avoir un nom comme *nomuniqueDefender*.

1. Cliquez sur le bouton **Suivant**.

    >**Remarque :** si le bouton *Suivant* est désactivé ou grisé et que vous voyez un message d’erreur indiquant que l’espace de travail Microsoft Sentinel n’est *pas intégré* à Defender XDR, essayez d’actualiser la page du portail Defender XDR, car la synchronisation peut prendre 5 à 10 minutes.

1. Sur la page *Révision des modifications*, vérifiez que l’*Espace de travail* sélectionné est correct et passez en revue les éléments à puces sous la section *À quoi s’attendre lorsque l’espace de travail est connecté*. Cliquez sur le bouton **Connecter**.

1. Vous devez voir le message *Connexion de l’espace de travail en cours* suivi d’un message *Connecté à l’espace de travail*.

1. Cliquez sur le bouton **Fermer**. 

1. Sur le portail **Defender XDR**, sur la **page d’accueil**, vous devez voir une bannière en haut avec le message *Votre SIEM et XDR unifié est prêt*. Sélectionnez le bouton **Démarrer la chasse**.

1. Dans *Chasse avancée*, un message doit s’afficher pour « Explorer votre contenu à partir de Sentinel ». Dans le volet de menu de gauche, notez les tables, fonctions et requêtes *Microsoft Sentinel* sous les onglets correspondants.

1. Développez le volet de menu principal de gauche s’il est réduit et développez les nouveaux éléments de menu **Microsoft Sentinel**. Vous devez voir les sélections *Gestion des menaces*, *Gestion des contenus* et *Configuration*.

 >**Remarque :** Certaines fonctionnalités peuvent ne pas être disponibles dans la préversion publique et l’interface utilisateur peut différer des instructions du labo. En outre, la synchronisation entre Microsoft Sentinel et Microsoft Defender XDR peut prendre quelques minutes. Il est donc possible que vous ne voyez pas tous les *Connecteurs de données* installés, par exemple.

## Vous avez terminé le labo
