---
lab:
  title: 'Exercice 4 : connecter Defender XDR à Microsoft Sentinel en tirant parti de connecteurs de données'
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Parcours d’apprentissage 6 : Labo 1 – Exercice 4 – Connecter Defender XDR à Microsoft Sentinel en tirant parti de connecteurs de données

## Scénario de labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex4.png)

Vous êtes Analyste des opérations de sécurité et vous travaillez dans une entreprise qui a déployé Microsoft Defender XDR et Microsoft Sentinel. Vous devez préparer la Plateforme d’opérations de sécurité unifiée qui connecte Microsoft Sentinel à Defender XDR. Votre étape suivante consiste à installer la solution Hub de contenu Defender XDR et à déployer le connecteur de données Defender XDR dans Microsoft Sentinel.

### Tâche 1 : Connecter Defender XDR

Dans cette tâche, vous allez déployer le connecteur Microsoft Defender XDR.

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

## Vous avez terminé le labo
