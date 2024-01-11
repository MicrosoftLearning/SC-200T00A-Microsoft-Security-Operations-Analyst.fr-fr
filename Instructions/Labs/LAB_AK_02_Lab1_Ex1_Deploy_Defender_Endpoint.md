---
lab:
  title: "Exercice\_1\_: déployer Microsoft\_Defender\_pour\_point\_de\_terminaison"
  module: Learning Path 2 - Mitigate threats using Microsoft Defender for Endpoint
---

# Chemin d’apprentissage 2 - Labo 1 - Exercice 1 - Déployer Microsoft Defender pour point de terminaison

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod2_L1_Ex1.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise qui implémente Microsoft Defender pour point de terminaison. Votre responsable prévoit d’intégrer quelques appareils afin de fournir des informations sur les modifications requises des procédures de réponse de l’équipe chargée des opérations de sécurité.

La première étape consiste à initialiser l’environnement Defender pour point de terminaison. Dans la suite du labo, vous intégrez les appareils initiaux pour votre déploiement en exécutant le script d’intégration sur les appareils. Vous configurez la sécurité pour l’environnement. Pour terminer, vous créez des groupes d’appareils et vous affectez les appareils appropriés.

>**Important :** les machines virtuelles du labo sont utilisées via différents modules. Assurez-vous d’enregistrer vos machines virtuelles. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

>**Remarque :** vérifiez que vous avez terminé la tâche 3 du module précédent.

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Deploy%20Microsoft%20Defender%20for%20Endpoint)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 


### Tâche 1 : initialiser Microsoft Defender pour point de terminaison

Dans cette tâche, vous allez effectuer l’initialisation du portail Microsoft Defender pour point de terminaison.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu'Admin avec le mot de passe suivant : **Pa55w.rd**.  

1. Si vous n’êtes pas déjà sur le portail Microsoft 365 Defender, ouvrez le navigateur Microsoft Edge.

1. Dans le navigateur Edge, accédez au portail Microsoft 365 Defender à l’adresse (https://security.microsoft.com).

1. Dans la boîte de dialogue **Se connecter** , copiez et collez le compte de messagerie du locataire pour le nom d’utilisateur administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le mot de passe du locataire de l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Se connecter**.

    >**Conseil :** le compte de messagerie et le mot de passe du locataire de l’administrateur sont disponibles sous l’onglet Ressources.

1. Dans le portail **Microsoft 365 Defender**, dans le menu de navigation, sélectionnez **Paramètres** à gauche.

1. Dans la page Paramètres, sélectionnez **Découverte de l’appareil**. 

    >**Remarque :**  si l’option **Découverte de l’appareil** n’est pas affichée sous **Paramètres**, déconnectez-vous en sélectionnant le cercle en haut à droite qui indique les initiales de votre compte, puis sélectionnez **Se déconnecter**. Vous pouvez également essayer d’actualiser la page avec Ctrl + F5 ou ouvrir la page en mode InPrivate. Connectez-vous à nouveau avec les informations d’identification de **l’adresse e-mail du locataire**.

1. Dans Configuration de la découverte, assurez-vous que l’option **Découverte standard (recommandée)** est sélectionnée. 

    >**Conseil :** si l’option n’est pas affichée, actualisez la page.


### Tâche 2 : intégrer un appareil

Dans cette tâche, vous allez intégrer un appareil à Microsoft Defender pour point de terminaison à l’aide d’un script d’intégration.

1. Sélectionnez **Paramètres** dans la barre de menus de gauche, puis, sur la page Paramètres, choisissez **Points de terminaison**.

1. Dans la section Gestion des appareils, sélectionnez **Intégration**.

    >**Remarque :** vous pouvez également effectuer l’intégration des appareils à partir de la section **Ressources**, dans la barre de menus de gauche. Développez Ressources et sélectionnez Appareils. Dans la page Inventaire des appareils, avec Ordinateurs et appareils mobiles sélectionné, faites défiler vers le bas jusqu’à **Intégrer des appareils.** Ceci vous dirige vers la page **Paramètres > Points de terminaison**.

1. Dans la zone « 1. Intégrer un appareil », assurez-vous que « Script local (pour jusqu’à 10 appareils) » s’affiche dans la liste déroulante Méthode de déploiement et sélectionnez le bouton **Télécharger le package d’intégration**.

1. Dans la fenêtre contextuelle *Téléchargements*, mettez en surbrillance le fichier « WindowsDefenderATPOnboardingPackage.zip » avec votre souris et sélectionnez l’icône de dossier **Afficher dans le dossier**. **Conseil :** si vous ne voyez pas le fichier, accédez au répertoire c:\users\admin\downloads.

    >**Conseil :** si votre navigateur bloque le téléchargement, prenez des mesures dans le navigateur pour l’autoriser. Dans le navigateur Microsoft Edge, le message suivant « *WindowsDefenderATPOnboardingPackage.zip n’est pas couramment téléchargé. Assurez-vous que vous faites confiance...*, sélectionnez le bouton des points de suspension (...) si nécessaire, puis cliquez sur **Garder**. Dans Microsoft Edge, une deuxième fenêtre contextuelle s’affiche avec le message suivant « * Assurez-vous que vous faites confiance à WindowsDefenderATPOnboardingPackage.zip avant de l’ouvrir* », sélectionnez **Afficher plus** pour développer les sélections et cliquez sur **Garder quand même**.


1. Cliquez avec le bouton droit sur le fichier zip téléchargé et sélectionnez **Extraire tout...**, assurez-vous de cocher la case *Afficher les fichiers extraits une fois l’opération terminée*, puis cliquez sur **Extraire**.

1. Cliquez avec le bouton droit sur le fichier extrait « WindowsDefenderATPLocalOnboardingScript.cmd » et sélectionnez **Propriétés**. Cochez la case **Débloquer** en bas à droite de la fenêtre Propriétés, puis sélectionnez **OK**.

1. Cliquez avec le bouton droit sur le fichier extrait « WindowsDefenderATPLocalOnboardingScript.cmd », puis choisissez **Exécuter en tant qu’administrateur**.  **Conseil :** si la fenêtre Windows SmartScreen, sélectionnez **Plus d’informations**, puis cliquez sur **Exécuter quand même**. 
    
1. Lorsque la fenêtre « Contrôle de compte d’utilisateur » s’affiche, sélectionnez **Oui** pour autoriser l’exécution du script et répondre **Y** à la question présentée par le script, puis appuyez sur **Entrée**. Une fois l’opération terminée, un message doit s’afficher dans l’écran de commande indiquant que *Machine intégrée à Microsoft Defender pour point de terminaison*.

1. Appuyez sur une touche pour continuer. Cette opération ferme la fenêtre d’invite de commandes.


### Tâche 3 : configurer des rôles

Dans cette tâche, vous allez configurer des rôles à utiliser avec des groupes d’appareils.

1. Dans le portail Microsoft 365 Defender, sélectionnez **Paramètres** dans la barre de menus de gauche, puis **Points de terminaison**. 

1. Sous la zone des autorisations, sélectionnez **Rôles**.

1. Sélectionnez le bouton **Activer les rôles** .

1. Sélectionnez **+ Ajouter un rôle**.

1. Dans la boîte de dialogue Ajouter un rôle, entrez les informations suivantes :

    |Paramètres généraux|Valeur|
    |---|---|
    |Nom de rôle|**Support de niveau 1**|
    |Autorisations|Fonctionnalités de réponse en direct – Avancées|

1. Cliquez sur **Suivant**.

1. Sélectionnez l’onglet **Groupes d’utilisateurs affectés** en haut. Sélectionnez **sg-IT**, puis **Ajouter des groupes sélectionnés**. Vérifiez qu’il apparaît sous *Groupes d’utilisateurs Azure AD avec ce rôle*.

1. Sélectionnez **Envoyer**, puis **Terminé** lorsque vous avez terminé.

    >**Remarque :** si vous recevez l’erreur *« L’utilisateur ne peut pas effectuer cette action, car son UserAuthEnforcementMode est Rbac et cette action nécessite l’une des opérations suivantes : RbacV2 »,* sélectionnez **OK** et réessayez.

### Tâche 4 : configurer des groupes d’appareils

Dans cette tâche, vous allez configurer des groupes d’appareils qui autorisent la configuration du contrôle d’accès et de l’automatisation.

1. Dans le portail Microsoft 365 Defender, sélectionnez **Paramètres** dans la barre de menus de gauche, puis **Points de terminaison**. 

1. Sous la zone Autorisations, sélectionnez **Groupes d’appareils**.

1. Sélectionnez l’icône **+ Ajouter un groupe d’appareils**.

1. Sous l’onglet Général, entrez les informations suivantes :

    |Paramètres généraux|Valeur|
    |---|---|
    |Nom du groupe d’appareils|**Regular**|
    |Niveau de correction|Complet - Corrige automatiquement les menaces|

1. Cliquez sur **Suivant**.

1. Sous l’onglet Appareils, pour la condition de système d’exploitation, sélectionnez **Windows 10**, puis **Suivant**.
 
    >**Remarque :** certains fournisseurs d’hébergement de labo peuvent avoir configuré des images *Windows 11* pour WIN1. Vous pouvez sélectionner l’un ou l’autre, ou les deux.

1. Sous l’onglet Aperçu des appareils, le bouton *Afficher l’aperçu* peut afficher la machine virtuelle WIN1, mais il est probable que les données ne soient pas encore remplies. Sélectionnez **Suivant** pour continuer.

1. Pour l’onglet Accès utilisateur, sélectionnez **sg-IT**, puis le bouton **Ajouter des groupes sélectionnés**. Vérifiez qu’il apparaît sous *Groupes d’utilisateurs Azure AD ayant accès à ce groupe d’appareils*.

1. Sélectionnez **Envoyer**, puis **Terminé** lorsque vous avez terminé.

1. La configuration du groupe d’appareils a changé. Sélectionnez **Appliquer des modifications** pour vérifier les correspondances et recalculer les regroupements.

1. Vous aurez maintenant deux groupes d’appareils : le groupe « Normal » que vous venez de créer et le groupe « Appareils non groupés (par défaut) » avec le même niveau de correction.

## Passez à l’exercice 2
