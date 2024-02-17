# Module 1 : atténuer les menaces avec Microsoft 365 Defender

**Remarque** : la réussite de cette démonstration dépend de l’exécution correcte de toutes les étapes décrites dans le [document sur les conditions préalables](00-prerequisites.md). 

## Utiliser le portail Microsoft 365 Defender

Dans cette tâche, vous allez vous familiariser avec les fonctionnalités du portail Microsoft 365 Defender.

- Tableau de bord de l’accueil
- Incidents et alertes
- Chasse
- Centre de notifications
- Threat Analytics
- Degré de sécurisation
- Points de terminaison
- Gestion des vulnérabilités
- E-mail et collaboration
- Applications cloud
- Rapports
- Paramètres
- Autorisations

1. Si vous n’êtes pas déjà au Microsoft Defender Security Center, accédez-y à l’adresse (https://security.microsoft.com) connecté en tant qu’Administrateur pour votre locataire.

1. Dans le tableau de bord **Accueil**, vous pouvez afficher une vue d’ensemble de votre état sécurisé. Vous pouvez personnaliser l’affichage en **Ajoutant des cartes** ou en les supprimant. Pour supprimer un carte, sélectionnez les points de suspension (...) sur une carte.
1. Ensuite, sélectionnez **Incidents et alertes**. Cette action développera les choix de menu ci-dessous. C’est là que les enquêtes sont effectuées.
1. Procédez de la même façon avec **Repérage** pour afficher la page Requête de **Repérage avancé**. 
    1. Vous pouvez exécuter des requêtes KQL ici.
1. Sélectionnez **Actions et soumissions** pour afficher le **Centre de notifications** et les **Soumissions**
1. Sélectionnez **Informations sur les menaces**, puis **Analyses de menaces**. Cette page fournit des informations sur les vulnérabilités et risques courants (CVE) dont vous avez besoin pour effectuer le suivi. Sélectionnez le **Niveau de sécurité** et explorez les onglets. Consultez les **Actions recommandées** ici.
1. Sélectionnez **Ressources** et **Appareils** pour votre `Device Inventory`. Vous pouvez ajouter des appareils ici ou utiliser un parc existant.
1. Sous `Assets` vous trouverez les **Identités**
1. Dans la section **Points de terminaison**, vous pouvez effectuer la **Gestion des vulnérabilités**. `Vulnerability management` propose un `Dashboard` dans lequel vous pouvez consulter votre score d’exposition.
1. La section **Points de terminaison** propose également la fonctionnalité **Évaluations et simulations**. Le **Labo d’évaluation** vous permet de configurer des appareils isolés pour explorer des programmes malveillants.
1. Dans la section **E-mail et collaboration**, vous trouverez les fonctionnalités de `Defender for Office 365`. Le menu **Enquêtes** affiche les résultats des enquêtes et réponses automatisées (AIR) sur les menaces.
1. La section **E-mail et collaboration** contient également un menu **Stratégies et règles**. Il vous permet de configurer les stratégies **Menace et alerte**.
1. Faites défiler vers le bas jusqu’aux **applications cloud**. Cette section est réservée au service **Microsoft Defender pour les applications Cloud**. Le menu **Gouvernance des applications** vous permet de définir des stratégies d’application.
1. La section suivante vous permet de consulter les **Rapports** des services Microsoft 365 Defender, **AUdit**, où vous pouvez activer l’enregistrement de l’activité des administrateurs et des utilisateurs, ainsi que définir les **Autorisations** et les **Paramètres**.
1. Dans **Autorisations**, vous pouvez configurer des rôles **Azure AD** et **Point de terminaison**.
1. Le menu **Paramètres** vous permet de définir les paramètres généraux, tels que le fuseau horaire et les notifications par e-mail, ainsi que de spécifier des paramètres précis pour les points de terminaison, les identités et la découverte d’appareils.
1. Sélectionnez **Paramètres**, puis **Points de terminaison**. Vous pouvez afficher et ajouter des **Licences** ici. Sélectionnez ensuite **Fonctionnalités avancées**. Faites défiler la liste complète des fonctionnalités, mais n’apportez pas de modifications maintenant.
1. Quittez ensuite les **Paramètres** et dans la liste de menus principale, à gauche, sélectionnez **Plus de ressources**. Vous devez voir des cartes ou vignettes contenant des liens vers la **Conformité Microsoft Purview**, **Azure Active Directory** et d’autres fonctionnalités qui ne font pas directement partie de **Microsoft 365 Defender**. Sélectionnez le bouton **Ouvrir** pour afficher la **Conformité Microsoft Purview**. Le portail de conformité doit alors s’afficher.

## Vous avez terminé le labo.