# Module 1 : atténuer les menaces avec Microsoft 365 Defender

**Remarque** : la réussite de cette démonstration dépend de l’exécution correcte de toutes les étapes décrites dans le [document sur les conditions préalables](00-prerequisites.md).

## Utiliser le portail Microsoft Defender

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

## Connecter Microsoft Sentinel et Microsoft Defender XDR

Dans cette tâche, vous allez connecter un espace de travail Microsoft Sentinel à Microsoft Defender XDR.

**Remarque :** il existe des différences de capacité entre le portail Microsoft Defender XDR et le portail Microsoft Sentinel. L’expérience et les étapes de l’interface utilisateur peuvent différer des instructions de labo.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu’*Administrateur* avec le mot de passe : **Pa55w.rd**.  

1. Ouvrez le navigateur Microsoft Edge.

1. Dans le navigateur Edge, accédez au portail Microsoft Defender XDR à l’adresse <https://security.microsoft.com>.

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

 >**Remarque** : la synchronisation entre Microsoft Sentinel et Microsoft Defender XDR peut prendre quelques minutes. Il est donc possible que vous ne voyiez pas tous les *Connecteurs de données* installés, par exemple.

## Vous avez terminé le labo.