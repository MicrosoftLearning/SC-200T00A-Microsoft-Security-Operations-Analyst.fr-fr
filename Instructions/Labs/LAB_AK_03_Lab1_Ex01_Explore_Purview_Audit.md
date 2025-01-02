---
lab:
  title: "Exercice\_1\_: explorer les journaux Microsoft\_Purview\_Audit"
  module: Learning Path 3 - Mitigate threats using Microsoft Purview
---

# Parcours d’apprentissage 3 - Labo 1 - Exercice 1 - Explorer les journaux Microsoft Purview Audit

## Scénario de labo

Vous êtes analyste des opérations de sécurité et vous travaillez dans une entreprise qui implémente Microsoft Defender XDR et Microsoft Purview. Vous aidez vos collègues de l’équipe de conformité informatique à configurer Purview Audit (Standard) et Audit (Premium). Leur objectif est de s’assurer que tous les accès et toutes les modifications des données des patients de notre réseau d’établissements de soins de santé sont enregistrés avec précision, afin de respecter les réglementations en matière de protection des données de santé.

### Temps estimé pour terminer ce labo : 15 minutes

### Tâche 1 : activer les journaux Microsoft Purview Audit

Dans cette tâche, vous allez attribuer des stratégies de sécurité prédéfinies pour Exchange Online Protection (EOP) et Microsoft Defender for Office 365 dans le portail de sécurité Microsoft 365.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Ouvrez le navigateur Microsoft Edge.

1. Dans le navigateur Microsoft Edge, accédez au portail Microsoft Defender XDR à l’adresse (<https://security.microsoft.com>).

1. Dans la boîte de dialogue **Se connecter** , copiez et collez le compte de messagerie du locataire pour le nom d’utilisateur administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le mot de passe du locataire de l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Se connecter**.

1. Dans le menu de navigation, développez *Technologie opérationnelle* et sélectionnez **Autres ressources**.

1. Dans le volet **Autres ressources**, sélectionnez le bouton **Ouvrir** sur la vignette *Portail Microsoft Purview*.

1. Dès l’ouverture du portail Microsoft Purview, un message à propos du *nouveau portail Microsoft Purview s’affiche*. Sélectionnez l’option permettant d’accepter les conditions de divulgation de flux de données et la déclaration de confidentialité, puis sélectionnez **Essayer maintenant**.

    ![Capture d’écran de l’écran Bienvenue sur le nouveau portail de conformité Microsoft Purview.](../Media/welcome-purview-portal.png)

1. Sélectionnez **Solutions** dans la barre latérale de gauche, puis **Audit**.

1. Sur la page **Recherche**, sélectionnez la barre bleue **Démarrer l’enregistrement de l’activité des utilisateurs et des administrateurs** pour activer l’enregistrement d’audit.

    ![Capture d’écran montrant le bouton Démarrer l’enregistrement de l’activité des utilisateurs et des administrateurs.](../Media/enable-audit-button.png)

1. Après que vous avez sélectionné cette option, la barre bleue doit disparaître de cette page.

    >**Note :** l’enregistrement des activités peut prendre jusqu’à 60 minutes.

## Vous avez terminé le labo