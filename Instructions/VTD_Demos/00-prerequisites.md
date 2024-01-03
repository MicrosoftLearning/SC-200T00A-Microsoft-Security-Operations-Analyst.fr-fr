
# Analyste des opérations de sécurité Microsoft
Guide de préparation du formateur

## Objectif

Ce document est destiné aux présentateurs qui se préparent à enseigner pour la Journée de formation virtuelle sur la sécurité Microsoft pour `Defend Against Threats with Extended Detection and Response` et `Configure Security Operations Using Microsoft Sentinel`. Ce matériel est un sous-ensemble du cours de certification SC-200 : analyste des opérations de sécurité Microsoft.

## Conditions préalables à la démonstration

Les labos de ce cours nécessitent à la fois un locataire sous licence Microsoft 365 E5 ainsi qu’un abonnement Azure.

* Vous pouvez demander des Pass Azure de Microsoft Learning pour vous.
* Assurez-vous que vous demandez ces pass au moins deux semaines avant d’effectuer les démonstrations. Après avoir reçu le pass, vous devez l’activer. 
* Le Pass Azure fonctionne de la même manière qu’un Abonnement d’essai Microsoft Azure accessible au public. Cela signifie qu’il existe des limitations à ce que vous pouvez faire avec ce pass.
* Les instructions de labo sont dans le [référentiel GitHub de Microsoft Learning SC-200](https://github.com/MicrosoftLearning/SC-200T00A-Microsoft-Security-Operations-Analyst/tree/master/Instructions/VTD_Demos/).
* Vérifiez que le nouveau navigateur Microsoft Edge est installé sur l’ordinateur que vous utiliserez pour les démonstrations.

## Activer le Pass Azure

## Déployer Defender pour point de terminaison

### Obtenir vos informations d’identification Microsoft 365

Une fois que vous avez lancé le labo, un locataire d’essai gratuit sera mis à votre disposition dans l’environnement de labo virtuel Microsoft. Ce locataire reçoit automatiquement un nom d’utilisateur et un mot de passe uniques. Vous devez récupérer ce nom d’utilisateur et ce mot de passe pour pouvoir vous connecter à Azure et à Microsoft 365 dans l’environnement de labo virtuel Microsoft.

Étant donné que ce cours peut être proposé par des partenaires de formation à l’aide de l’un de plusieurs fournisseurs d’hébergement de labo autorisés, les étapes réelles impliquées pour récupérer l’ID de locataire associé à votre locataire peuvent varier en fonction du fournisseur d’hébergement de labo. Par conséquent, votre instructeur vous fournira les instructions nécessaires sur la façon de récupérer ces informations pour votre cours. Les informations dont vous aurez besoin pour le cours sont les suivantes :

    - **ID de suffixe du locataire.** Cet ID concerne les comptes onmicrosoft.com que vous utiliserez pour vous connecter à Microsoft 365 pendant les labos. Il est au format **{username}@M365xZZZZZZ.onmicrosoft.com**, où ZZZZZZ est votre ID de suffixe de locataire unique, fourni par votre fournisseur d’hébergement de labo. Enregistrez cette valeur ZZZZZZ  pour une utilisation ultérieure. Lorsque l’une des étapes du labo vous dirige vers les portails Microsoft 365, vous devez entrer la valeur ZZZZZZ que vous avez obtenue ici.
    - **Mot de passe du locataire.** Il s’agit du mot de passe du compte d’administrateur communiqué par votre fournisseur d’hébergement de labo.
    

### Initialiser Microsoft Defender pour point de terminaison

Dans cette tâche, vous allez effectuer l’initialisation de Microsoft Defender pour point de terminaison.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Edge, accédez au portail Microsoft 365 Defender à l’adresse (https://security.microsoft.com).

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de messagerie du locataire associé au nom d’utilisateur administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrez le mot de passe**, copiez et collez le mot de passe du locataire de l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Se connecter**.

Dans le portail **Microsoft 365 Defender**, dans le menu de navigation, sélectionnez **Accueil** à gauche.

    >**Note:** You may need to scroll all the way to the menu top.

1. Dans la page d’**Accueil** du portail, l’élément **Bienvenue dans Microsoft 365 Defender** s’affiche.

1. Faites défiler les vignettes jusqu’à trouver la vignette intitulée **Microsoft 365 Defender** affichant le message **Activer Microsoft 365 Defender.**

    >**Conseil :** elle doit se trouver en bas à droite de la section des vignettes.

1. Sélectionnez le bouton qui indique **Activer les nouvelles fonctionnalités.**

1. Pendant un bref instant, vous verrez des messages indiquant *chargement et initialisation* en haut de la page, puis une image d’une tasse de café accompagnée du message suivant : **Attendez, nous préparons de nouveaux espaces pour vos données et nous les connectons.** Cette opération va prendre environ 5 minutes. *Laissez la page ouverte et assurez-vous qu’elle se termine correctement, car elle est requise pour le labo suivant.*

    >**Remarque :** si le message « Attendez ! Nous préparons de nouveaux espaces pour vos données et nous les connectons » ne s’affiche pas ou si la page « Paramètres > Microsoft 365 Defender > Compte » s’ouvre, mais que le message « Échec du chargement de l’emplacement de stockage des données. Réessayez ultérieurement » s’affiche, ouvrez le menu « Général » et sélectionnez « Paramètres du service d’alerte » ou accédez au menu de navigation, faites défiler jusqu’à la section « Ressources » et sélectionnez « Appareils ».

1. Une fois le nouvel espace créé, les paramètres généraux de Microsoft 365 Defender s’affichent, vous permettant de définir les options relatives au compte, aux notifications par e-mail, aux paramètres du service d’alerte, aux autorisations et aux rôles, ainsi qu’à l’API de diffusion en continu. L’option **Fonctionnalités en préversion** est également activée.

**Remarque** : dans l’environnement de labo hébergé, votre emplacement de stockage de données doit être sélectionné pour vous. Il doit également se trouver dans la zone géographique appropriée pour laquelle ce locataire de formation est géré. Vous pouvez toujours sélectionner la durée de conservation des données, mais ce n’est pas obligatoire.

1. Dans **Paramètres**, sélectionnez **Points de terminaison**.

1. Dans la section Gestion des appareils, sélectionnez **Intégration**.

    >**Remarque :** vous pouvez également effectuer l’intégration des appareils à partir de la section **Ressources**, dans la barre de menus de gauche. Développez Ressources et sélectionnez Appareils. Dans la page Inventaire des appareils, avec Ordinateurs et appareils mobiles sélectionné, faites défiler vers le bas jusqu’à **Intégrer des appareils.** Ceci vous dirige vers la page **Paramètres > Points de terminaison**.

1. Dans la zone « 1. Intégrer un appareil », assurez-vous que « Script local (pour jusqu’à 10 appareils) » s’affiche dans la liste déroulante Méthode de déploiement et sélectionnez le bouton **Télécharger le package d’intégration**.

1. Extrayez le contenu du fichier zip téléchargé dans un dossier local, par exemple le dossier Documents.

1. Cliquez avec le bouton droit sur le fichier extrait WindowsDefenderATPLocalOnboardingScript.cmd et choisissez **Exécuter en tant qu’Administrateur**.  Si une fenêtre Windows SmartScreen s’affiche, sélectionnez Exécuter quand même.

**Remarque :** le répertoire par défaut du fichier est le suivant : c:\users\admin\downloads.
    
1. Répondez par **Y** aux questions formulées par le script. Lorsque vous avez terminé, un message similaire à « La machine a été correctement intégrée... » doit s’afficher sur l’écran de commande. 

1. Dans la page Intégration du portail, copiez le script du test de détection et exécutez-le dans une fenêtre de commande ouverte.  Vous devrez peut-être ouvrir une nouvelle fenêtre **Administrateur : Invite de commandes**. Pour ce faire, tapez *CMD* dans la barre de recherche Windows et sélectionnez **Exécuter en tant qu’administrateur**.

1. Dans le menu du portail Microsoft 365 Defender, sélectionnez **Inventaire des appareils**. Vous devriez voir votre appareil dans la liste.

**Remarque :** l’affichage de l’appareil sur le portail peut prendre jusqu’à 5 minutes.


### Configurer un rôle

Dans cette tâche, vous allez configurer des rôles et les attribuer à des groupes d’appareils.

1. Dans le portail Microsoft 365 Defender, dans la barre de menus gauche, sélectionnez **Paramètres**. 

1. Sélectionnez **Points de terminaison**, puis **Rôles** dans la zone d’autorisations.

1. Sélectionnez le bouton **Activer les rôles** .

1. Sélectionnez **Ajouter un élément**.

1. Dans la boîte de dialogue Ajouter un rôle, entrez les valeurs suivantes :

    |Paramètres généraux|Valeur|
    |---|---|
    |Nom de rôle|**Support de niveau 1**|
    |Autorisations|Fonctionnalités de réponse en direct – Avancées|

1. Cliquez sur **Suivant**.

1. Sous l’onglet Groupes d’utilisateurs attribués. Sélectionnez **sg-IT**, puis **Ajouter les groupes sélectionnés**.

1. Sélectionnez **Enregistrer**.

### Configurer des groupes d’appareils

Dans cette tâche, vous allez configurer des groupes d’appareils et spécifier le contrôle d’accès et l’automatisation.

1. Sélectionnez **Paramètres** dans la barre de menus de gauche. 

1. Sélectionnez **Points de terminaison**, puis dans la zone d’autorisations, sélectionnez **Groupes d’appareils**.

1. Sélectionnez **Ajouter** un groupe d’appareils.

1. Sous l’onglet Général, entrez les informations suivantes :

    |Paramètres généraux|Valeur|
    |---|---|
    |Nom du groupe d’appareils|**Regular**|
    |Niveau d’automatisation|Complet - Corrige automatiquement les menaces|

1. Cliquez sur **Suivant**.

1. . Sous l’onglet Appareils, pour la condition de système d’exploitation, sélectionnez **Windows 10**, puis **Suivant**.

1. Sous l’onglet Aperçu des appareils, sélectionnez **Afficher l’aperçu** pour afficher la machine virtuelle WIN1. Cliquez sur **Suivant**. 
**Conseil :** si vous ne voyez pas la machine virtuelle dans la liste d’aperçu, revenez en arrière et sélectionnez également *Aucun* pour la condition du système d’exploitation. Les données de la machine virtuelle ne sont pas encore remplies.

1. Pour l’onglet Accès utilisateur, sélectionnez **sg-IT**, puis **Ajouter des groupes sélectionnés**.

1. Cliquez sur **Terminé**.

1. La configuration du groupe d’appareils a changé. Sélectionnez **Appliquer des modifications** pour vérifier les correspondances et recalculer les regroupements.

1. Vous aurez maintenant deux groupes d’appareils : le groupe « Normal » que vous venez de créer et le groupe « Appareils non groupés (par défaut) » avec le même niveau de correction.

<!--- 
## Deploy sample alerts for Demo in Module 3

In this task, you will load sample security alerts and review the alert details.

1. In the Edge browser, open the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Tenant Email** account provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Defender*, then select **Microsoft Defender for Cloud**.

1. In the **Getting Started** menu the default selection is **Upgrade**, select or **Skip** for now.

1. Select **Security alerts** in the portal menu.

1. Select **Sample Alerts** from the command bar.

1. In the Create sample alerts (Preview) pane make sure your subscription is selected.  Make sure all sample alerts are selected and select **Create sample alerts**.  

**Note** This may take a few minutes to complete. --->

## Déployer l’espace de travail Microsoft Sentinel pour la démonstration dans le module 4

Dans cette tâche, vous allez créer un espace de travail Microsoft Sentinel.

 >**Remarque :** vous devez disposer d’un Pass Azure ou d’un autre abonnement Azure actif pour la démonstration suivante.

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez **+ Créer**.

1. Sélectionnez ensuite **+ Créer un espace de travail**.

**Remarque** : tout d’abord, créez un espace de travail Log Analytics.

1. Sélectionnez votre abonnement.

1. Sélectionnez le lien **Créer**, pour le groupe de ressources et entrez un nouveau nom de groupe de ressources de votre choix.

1. Dans le champ Nom, sous Détails de l’instance, entrez un nom de votre choix pour l’espace de travail Log Analytics.

**Remarque :** ce nom doit être unique et sera également le nom de l’espace de travail Microsoft Sentinel.

1. Sélectionnez la région adaptée à votre situation.  La région appropriée peut être sélectionnée par défaut ou votre instructeur peut avoir des conseils spécifiques sur la région à sélectionner.  

1. Sélectionnez **Vérifier + créer**.

1. Sélectionnez **Create** (Créer). Attendez que le nouvel espace de travail Log Analytics apparaisse dans la liste de la page Ajouter Microsoft Sentinel à un espace de travail.  Cela peut prendre une minute.

1. Sélectionnez l’espace de travail nouvellement créé lorsqu’il apparaît, puis sélectionnez **Ajouter**.

## Déployer des solutions de hub de contenu et des connecteurs de données pour Microsoft Sentinel

### Tâche 1 : Accéder à l’espace de travail Microsoft Sentinel

Dans cette tâche, vous allez accéder à votre espace de travail Microsoft Sentinel.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Ouvrez le navigateur, recherchez, téléchargez et installez le nouveau navigateur Microsoft Edge. Démarrez le nouveau navigateur Edge.

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez l’espace de travail Microsoft Sentinel que vous avez créé dans l'atelier précédent.

### Tâche 2 : connecter le connecteur Activité Azure

Dans cette tâche, vous allez connecter le connecteur de données *Activité Azure*.

1. Dans les menus de gauche de Microsoft Sentinel, faites défiler jusqu’à la section *Gestion de contenu*, puis sélectionnez **Hub de contenu**.

1. Dans le *Hub de contenu*, recherchez la solution **Activité Azure** et sélectionnez-la dans la liste.

1. Dans la page de solution *Microsoft Defender pour le cloud*, sélectionnez **Installer**.

1. Une fois l’installation terminée, sélectionnez **Gérer**.

    >**Remarque :** la solution *Activité Azure* installe le connecteur de données *Activité Azure*, 12 règles analytiques, 14 requêtes de repérage, 1 classeur.

1. Sélectionnez le connecteur de données *Activité Azure*, puis **Ouvrir la page du connecteur**.

1. Dans la zone  *Configuration*, sous l’onglet *Instructions*, faites défiler jusqu'à « 2. Connecter vos abonnements… », sélectionnez **Lancer l’Assistant Attribution Azure Policy>**.

1. Dans l’onglet **Informations de base**, sous **Étendue**, sélectionnez le bouton en forme de points de suspension (…), puis sélectionnez votre abonnement « Pass Azure - Parrainage » dans la liste déroulante et cliquez sur **Sélectionner**.

1. Sélectionnez l’onglet **Paramètres**, choisissez votre espace de travail dans la liste déroulante **Espace de travail Log Analytics principal**. Cette action appliquera la configuration de l’abonnement pour envoyer les informations à l’espace de travail Log Analytics.

1. Sélectionnez l’onglet **Correction** et cochez la case **Créer une tâche de correction**. Cette action applique la stratégie aux ressources Azure existantes.

1. Sélectionnez le bouton **Vérifier + créer** pour passer en revue la configuration.

1. Sélectionnez **Créer** pour terminer.

### Tâche 3 : créer une machine virtuelle Windows dans Azure

Dans cette tâche, vous allez créer une machine virtuelle Windows dans Azure.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu’administrateur ou administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Microsoft Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Sélectionnez **+ Créer une ressource**. **Conseil :** si vous étiez déjà dans le portail Azure, vous devrez peut-être sélectionner *Microsoft Azure* dans la barre supérieure pour accéder à l’accueil.

1. Dans la zone **Rechercher dans les services et la Place de marché**, entrez *Windows 10* et sélectionnez **Microsoft Window 10** dans la liste déroulante.

1. Sélectionnez la zone de **Microsoft Window 10**.

1. Ouvrez la liste déroulante *Abonnement* et sélectionnez **Windows 10 Entreprise, version 22H2**.

1. Sélectionnez **Démarrer avec une configuration prédéfinie** pour continuer.

1. Sélectionnez **Dev/Test**, puis **Continuer pour créer une machine virtuelle**.

1. Sélectionnez **Créer** pour le *groupe de ressources*, entrez `RG-AZWIN01` pour le nom, et sélectionnez **OK**.

    >**Remarque :** il s’agit d’un nouveau groupe de ressources à des fins de suivi. 

1. Dans *Nom de la machine virtuelle*, entrez `AZWIN01`.

1. Laissez **USA Est** comme valeur par défaut pour la *région*.

1. Faites défiler la page vers le bas et passez en revue l’*image* de la machine virtuelle. Si elle est vide, sélectionnez **Windows 10 Entreprise, version 22H2**.

1. Passez en revue la *taille* de la machine virtuelle. Si elle est vide, sélectionnez **Afficher toutes les tailles**, choisissez la première taille de machine virtuelle sous *Utilisée par la plupart des utilisateurs Azure*, puis sélectionnez **Sélectionner**.

    >**Remarque :** si le message suivant s’affiche : *Cette image n’est pas prise en charge pour Azure Automanage. Pour désactiver cette fonctionnalité, accédez à l’onglet Gestion. Sinon, sélectionnez une image prise en charge.* Accédez à l’onglet Gestion et désactivez « Automanage ». Le processus de création aboutira par la suite.

1. Faites défiler la page vers le bas et entrez un *nom d’utilisateur* de votre choix. **Conseil :** évitez les mots réservés tels qu’administrateur ou racine.

1. Entrez un *mot de passe* de votre choix. **Conseil :** il peut être plus facile de réutiliser votre mot de passe de locataire. Il se trouve sous l’onglet Ressources.

1. Faites défiler la page vers le bas et sélectionnez la case à cocher sous *Licences* pour confirmer que vous disposez de la licence éligible.

1. Sélectionnez **Vérifier + créer** et attendez que la validation réussisse.

    >**Remarque :** s’il existe un échec de validation *réseau*, sélectionnez cet onglet, passez en revue son contenu, puis sélectionnez à nouveau **Vérifier + créer**.

1. Sélectionnez **Créer**. Patientez quelques minutes pendant la création de la ressource.

### Tâche 4 : connecter une machine virtuelle Windows Azure

Dans cette tâche, vous allez connecter une machine virtuelle Windows Azure à Microsoft Sentinel.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez l’espace de travail Microsoft Sentinel que vous avez créé précédemment.

1. 1. Dans les menus de gauche de Microsoft Sentinel, faites défiler jusqu’à la section *Gestion de contenu*, puis sélectionnez **Hub de contenu**.

1. Dans le *hub de contenu*, recherchez la solution **Événements de sécurité Windows ** et sélectionnez-la dans la liste.

1. Dans la page de solution *Événements de sécurité Windows*, sélectionnez **Installer**.

1. Une fois l’installation terminée, sélectionnez **Gérer**.

    >**Remarque :** la solution *Événements de sécurité Windows* installe les connecteurs de données *Événements de sécurité Windows via AMA* et *Événements de sécurité via l’ancien agent*. Plus 2 classeurs, 20 règles analytiques et 43 requêtes de repérage.

1. Sélectionnez le connecteur de données *Événements de sécurité Windows via AMA*, puis sélectionnez la page **Ouvrir le connecteur** dans le panneau d’informations du connecteur.

1. Dans la section *Configuration*, sous l’onglet *Instructions*, sélectionnez **Créer une règle de collecte de données**.

1. Entrez **AZWINDCR** pour le nom de la règle, puis sélectionnez **Suivant : Ressources**.

1. Sélectionnez **+ Ajouter une ou plusieurs ressources** pour sélectionner la machine virtuelle que nous avons créée.

1. Développez **RG-AZWIN01**, puis sélectionnez **AZWIN01**.

1. Sélectionnez **Appliquer**, puis **Suivant : Collecter**.

1. Passez en revue l’option de collecte des différents événements de sécurité. Conservez *tous les événements de sécurité*, puis sélectionnez **Suivant : Vérifier + créer**.

1. Sélectionnez **Créer** pour enregistrer la règle de collecte de données.

1. Attendez une minute, puis sélectionnez **Actualiser** pour voir apparaître la nouvelle règle de collecte de données.

### Tâche 5 : installer Azure Arc et connecter un serveur local

Dans cette tâche, vous allez installer Azure Arc sur un serveur local pour faciliter l’intégration.

>**Important :** les étapes suivantes sont effectuées sur une machine différente de celle que vous utilisiez précédemment. Recherchez les références de nom de machine virtuelle.

1. Connectez-vous à la machine virtuelle **WINServer** en tant qu'Administrateur avec le mot de passe suivant : **Passw0rd!** (le cas échéant).  

1. Ouvrez le navigateur Microsoft Edge et accédez au Portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du Portail Azure, tapez *Arc*, puis sélectionnez **Azure Arc**.

1. Dans le volet de navigation, sous **Infrastructure**, sélectionnez **Machines**.

1. Sélectionnez **+ Ajouter/Créer**, puis **Ajouter une machine**.

1. Dans la section « Ajouter un serveur unique », sélectionnez **Générer un script**.

1. Lisez l’onglet *Conditions préalables*, puis sélectionnez **Suivant** pour continuer.

1. Dans la page *Ajouter un serveur avec Azure Arc* , sélectionnez le groupe de ressources que vous avez créé précédemment sous *Détails du projet*. **Conseil :***RG-Defender*

    >**Remarque :** si vous n’avez pas encore créé de groupe de ressources, ouvrez un autre onglet, créez le groupe de ressources et recommencez.

1. Passez en revue les *Détails du serveur* et les options de la *méthode de connectivité*. Conservez les valeurs par défaut et sélectionnez **Suivant** pour accéder à l’onglet Balises.

1. Passez en revue les balises disponibles par défaut. Sélectionnez **Suivant** pour accéder à l’onglet Télécharger et exécuter le script.

1. Faites défiler la page et sélectionnez le bouton **Télécharger**. **Conseil :** si votre navigateur bloque le téléchargement, prenez des mesures dans le navigateur pour l’autoriser. Dans le navigateur Edge, sélectionnez le bouton de points de suspension (...) si nécessaire, puis sélectionnez **Conserver**.

1. Cliquez avec le bouton droit sur Démarrer Windows et sélectionnez **Windows PowerShell (admin)**.

1. Entrez *Administrator* pour le nom d’utilisateur et *Passw0rd!*. pour le « Mot de passe » si une invite UAC apparaît.

1. Entrez : cd C:\Users\Administrator\Downloads

    >**Important :** si ce répertoire n’existe pas, cela signifie probablement que vous n’êtes pas le bon ordinateur. Revenez au début de la tâche 4 et connectez-vous à nouveau à la machine virtuelle WINServer.

1. Tapez *Set-ExecutionPolicy -ExecutionPolicy Unrestricted* et appuyez sur Entrée.

1. Entrez **A** pour Oui pour tout, puis appuyez sur Entrée.

1. Tapez *.\OnboardingScript.ps1* et appuyez sur Entrée.  

    >**Important :** si vous obtenez l’erreur *« Le terme .\OnboardingScript.ps1 n’est pas reconnu... »*, vérifiez que vous effectuez les étapes de la tâche 4 dans la machine virtuelle WINServer. Il se peut également que le nom du fichier ait changé à la suite de plusieurs téléchargements. Recherchez *« .\OnboardingScript (1).ps1 »* ou d’autres numéros de fichier dans le répertoire actif.

1. Entrez **R** pour exécuter une seule fois et appuyez sur Entrée (cela peut prendre quelques minutes).

1. Le processus d’installation ouvre un nouvel onglet dans le navigateur Edge pour authentifier l’agent Azure Arc. Sélectionnez votre compte d’administrateur, attendez que le message « Authentification terminée » s’affiche, puis revenez à la fenêtre Windows PowerShell.

1. Une fois l’installation terminée, revenez à la page Portail Azure où vous avez téléchargé le script, puis sélectionnez **Fermer**. Fermez **Ajouter des serveurs avec Azure Arc** pour revenir à la page **Machines** Azure Arc.

1. Sélectionnez **Actualiser** jusqu’à ce que le nom du serveur WINServer s’affiche et que l’état soit *Connecté*.

    >**Remarque** : cela peut prendre quelques minutes.


### Tâche 6 : protéger un serveur local

Dans cette tâche, vous allez ajouter à Microsoft Sentinel une machine virtuelle Windows non-Azure connectée à Azure Arc.  

   >**Remarque :** le connecteur de données *Événements de sécurité Windows via AMA* nécessite Azure Arc pour les appareils non-Azure.

1. Vérifiez que vous êtes dans le connecteur de données *Événements de sécurité Windows via AMA* dans votre espace de travail Microsoft Sentinel.

1. Sous l’onglet **Instructions**, dans la section *Configuration*, modifiez la *règle de collecte de données* **AZWINDCR** en sélectionnant l’icône en forme de *crayon*.

1. Sélectionnez **Suivant : Ressources** et **+ Ajouter une ou plusieurs ressources**.

1. Développez le groupe de ressources que vous avez créé, puis sélectionnez **WINServer**.

    >**Important :** si vous ne voyez pas WINServer, reportez-vous au Parcours d’apprentissage 3, Exercice 1, Tâche 4 où vous avez installé Azure Arc sur ce serveur.

1. Sélectionnez **Appliquer**.

1. Sélectionnez **Suivant : Collecter**, puis **Suivant : Vérifier + créer**.

1. Sélectionnez **Créer** une fois que *Validation réussie* s’affiche.


<!--- ### Task 4: Connect the Microsoft Defender for Cloud connector.

In this task, you will connect the Microsoft Defender for Cloud connector.

1. From the Data Connectors tab, select the **Microsoft Defender for Cloud** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Review the Connecting Options. Don't connect. This is for informational purposes only.

### Task 5: Connect the Microsoft Defender for Cloud Apps connector.

In this task, you will connect theMicrosoft Defender for Cloud Apps connector.

1. From the Data Connectors Tab, select the **Microsoft Defender for Cloud Apps** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. In the **Instructions** tab in the **Configuration** section, select **Alerts** and then select **Apply Changes**.

### Task 6: Connect the Microsoft Defender for Office 365 connector.

In this task, you will connect the Microsoft Defender for Office 365 connector.

1. From the Data Connectors tab, select the **Microsoft Defender for Office 365** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Select **Connect**.

### Task 7: Connect the Microsoft Defender for Identity connector.

In this task, you will connect the Microsoft Defender for Identity connector.

1. From the Data Connectors Tab, select the **Microsoft Defender for Identity** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Review the Connecting Options. Don't connect. This is for informational purposes only.

### Task 8: Connect the Microsoft Defender for Endpoint connector.

In this task, you will connect the Microsoft Defender for Endpoint connector.

1. From the Data Connectors Tab, select the **Microsoft Defender for Endpoint** connector from the list.

1. Select Open connector page on the connector information blade.

1. Select **Connect**.

### Task 9: Connect the Microsoft 365 Defender connector.

In this task, you will connect the Microsoft 365 Defender connector.

1. From the Data Connectors Tab, select the **Microsoft 365 Defender** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Select all the checkboxes for Microsoft Defender for Endpoint.

1. Select **Apply Changes**. 

### Task 3: Connect a non-Azure Windows Machine.

In this task, you will connect a non-Azure Windows virtual machine to Microsoft Sentinel.

1. Login to WIN2 virtual machine as Admin with the password: **Pa55w.rd**.  

1. Open the browser, search for, download, and install the new Microsoft Edge browser. Start the new Edge browser.

1. Open a browser and log into the Azure Portal at https://portal.azure.com with your credentials.

1. In the Search bar of the Azure Portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace.

1. From the Data Connectors tab, select the **Security Events via Legacy Agent** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. In the Select which events to stream area, select **All Events**, then select **Apply Changes**.

1. Select the **Install agent on a non-Azure Windows  Machine**.

**Note:** The instructions for Install agent on a Windows Virtual Machine and Install agent on a non-Azure Windows Machine may be reversed. The links take you to the proper location even with the reversed text.

1. Select **Download & install agent for non-Azure Windows machines**. 

1. Select the link for **Download Windows Agent (64 bit)**.

1. Run the .exe file that is downloaded and confirm and User Account Control prompt that may appear.

1. Select **Next** on the Welcome dialog.

1. Select **I Agree** on the Microsoft Software License Terms page.  On the Destination prompt select **Next**.

1. On the Agent Setup Options prompt, select **Connect the agent to Azure Log Analytics (OMS)** option, then select **Next**.

1. In the browser, copy the **Workspace ID** from the Agents Management page and paste into the Workspace ID in the dialog. 

1. In the browser, copy the **Primary key** from the Agents Management page and paste into the Primary key in the dialog. 

1. Select **Next**.

1. Select **Next** on the Microsoft Update page.

2. Then select **Install**.

### Task 4: Install and collect Sysmon logs.

In this task, you will install and collect Sysmon logs.

You should still be connected to the WIN2 virtual machine.  The following instructions will install Sysmon with the default configuration.  You should research community based configurations for Sysmon to be used on production machines.

1. In the browser, go to https://docs.microsoft.com/sysinternals/downloads/sysmon

1. Download Sysmon from the page by select **Download Sysmon**.

1. Open the downloaded file and extract the files to a new directory c:\sysmon

1. In the Windows Taskbar for WIN2 search box, enter *command*.  The search results will show command prompt app.  Right-click on the command prompt app and select **Run as Administrator**.  Confirm any User Account Control prompts that appear.

1. Enter *cd \sysmon*

1. type *notepad sysmon.xml* to create a new file.

1. Open a tab in the browser and navigate to: https://github.com/SwiftOnSecurity/sysmon-config/blob/master/sysmonconfig-export.xml

1. Copy the contents of that file from Github to the sysmon.xml notepad file you just created and save the file.

1. In the command prompt type the following and press enter:
    sysmon.exe -accepteula -i sysmon.xml

1. In the browser, navigate to the Azure portal at https://portal.azure.com 

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. In Microsoft Sentinel, select **Settings** from the Configuration area and then select **Workspace settings** tab.

1. Make sure your Microsoft Sentinel Workspace is selected.

1. Select **Agents configuration** in Settings.

1. Select the **Windows Event logs** tab.

1. Select **Add windows event log** button.

1. Enter **Microsoft-Windows-Sysmon/Operational** in the Log name field.

1. Select **Apply**. --->

## Mener des attaques

### Tâche 1 : attaquer Windows configuré avec Defender pour point de terminaison

Dans cette tâche, vous allez effectuer des attaques sur un hôte avec Microsoft Defender pour point de terminaison configuré.

1. Connectez-vous à la machine virtuelle `WIN1` en tant qu’administrateur avec le mot de passe : **Pa55w.rd**.  

1. Dans la recherche de la barre des tâches, entrez *Commande*.  L’invite de commandes s’affiche dans les résultats de la recherche.  Cliquez avec le bouton de droite sur l’invite de commande et sélectionnez **Exécuter en tant qu’administrateur**. Vérifiez les invites de contrôle de compte d’utilisateur qui s’affichent.

1. Dans l’invite de commandes, entrez la commande dans chaque ligne en appuyant sur la touche Entrée après chaque ligne :
```
cd \
mkdir temp
cd temp
```

1. Copiez et exécutez cette commande :

```
REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"
```

### Tâche 2 : créer une attaque C2 (commande et contrôle)

1. Connectez-vous à la machine virtuelle `WIN1` en tant qu’administrateur avec le mot de passe : **Pa55w.rd**.  

1. Dans la recherche de la barre des tâches, entrez *Commande*.  L’invite de commandes s’affiche dans les résultats de la recherche.  Cliquez avec le bouton de droite sur l’invite de commande et sélectionnez **Exécuter en tant qu’administrateur**. Vérifiez les invites de contrôle de compte d’utilisateur qui s’affichent.
1. 
1. 
1. Attaque 2 -  Copiez et exécutez cette commande :

```
notepad c2.ps1
```
Sélectionnez **Oui** pour créer un fichier, puis copiez le script PowerShell suivant dans c2.ps1, puis sélectionnez **Enregistrer**.

**Remarque :** le collage dans la machine virtuelle peut avoir une longueur limitée.  Collez ceci dans trois sections pour vous assurer que tout le script est collé dans la machine virtuelle.  Vérifiez que le script se présente comme dans ces instructions dans le fichier c2.ps1 du bloc-notes.

```


param(
    [string]$Domain = "microsoft.com",
    [string]$Subdomain = "subdomain",
    [string]$Sub2domain = "sub2domain",
    [string]$Sub3domain = "sub3domain",
    [string]$QueryType = "TXT",
        [int]$C2Interval = 8,
        [int]$C2Jitter = 20,
        [int]$RunTime = 240
)


$RunStart = Get-Date
$RunEnd = $RunStart.addminutes($RunTime)

$x2 = 1
$x3 = 1 
Do {
    $TimeNow = Get-Date
    Resolve-DnsName -type $QueryType $Subdomain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout

    if ($x2 -eq 3 )
    {
        Resolve-DnsName -type $QueryType $Sub2domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
        
        $x2 = 1

    }
    else
    {
        $x2 = $x2 + 1
    }
    
    if ($x3 -eq 7 )
    {

        Resolve-DnsName -type $QueryType $Sub3domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout

        $x3 = 1
        
    }
    else
    {
        $x3 = $x3 + 1
    }


    $Jitter = ((Get-Random -Minimum -$C2Jitter -Maximum $C2Jitter) / 100 + 1) +$C2Interval
    Start-Sleep -Seconds $Jitter
}
Until ($TimeNow -ge $RunEnd)

```

À l’invite de commandes, entrez ce qui suit, et entrez la commande dans chaque ligne en appuyant sur la touche Entrée après chaque ligne :
```
powershell
.\c2.ps1
```
**Remarque :** vous verrez des erreurs de résolution. Ce processus est normal.
Laissez ce script de commande et ce script PowerShell s’exécuter en arrière-plan. Ne fermez pas la fenêtre.  La commande doit générer des entrées de journal pendant quelques heures.  Vous pouvez passer à la tâche suivante et aux exercices suivants pendant l’exécution de ce script.  Les données créées par cette tâche seront utilisées dans le labo Repérage des menaces ultérieurement.  Ce processus ne crée pas de quantités substantielles de données ou de traitement.

### Tâche 2 : attaquer Windows configuré avec l’Agent Azure Monitor (AMA)

Dans cette tâche, vous allez effectuer des attaques sur un hôte avec le connecteur Événements de sécurité configuré et Sysmon configuré.

1. Sélectionnez la machine virtuelle `AZWIN01` que vous avez créée précédemment.  

1. Dans le menu gauche, faites défiler jusqu’à **Opérations**, et sélectionnez **Exécuter une commande**.

1. Dans le volet **Exécuter une commande**, sélectionnez **RunPowerShellScript**.

1. Copiez les commandes ci-dessous pour simuler la création d’un compte Administrateur dans le formulaire `PowerShell Script`, et sélectionnez **Exécuter**.

    ```CommandPrompt
    net user theusernametoadd /add
    net user theusernametoadd ThePassword1!
    net localgroup administrators theusernametoadd /add
    ```

>**Remarque** : vérifiez qu’il n’existe qu’une seule commande par ligne et que vous pouvez réexécuter les commandes en modifiant le nom d’utilisateur.

1. Dans la fenêtre `Output`, vous devriez voir `The command completed successfully` trois fois.
