---
lab:
  title: "Exercice\_2 - Connecter des appareils Windows à Microsoft\_Sentinel avec des connecteurs de données"
  module: Learning Path 8 - Connect logs to Microsoft Sentinel
---

# Parcours d’apprentissage 8 - Labo 1 - Exercice 2 - Connecter des appareils Windows à Microsoft Sentinel avec des connecteurs de données

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex2.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez apprendre à connecter des données de journal provenant de nombreuses sources de données dans votre organisation. La source de données suivante est des machines virtuelles Windows à l’intérieur et à l’extérieur d’Azure, comme les environnements locaux ou d’autres clouds publics.

>**Important :** les exercices de laboratoire du parcours d’apprentissage #8 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Temps estimé pour terminer ce labo : 30 minutes

### Tâche 1 : créer une machine virtuelle Windows dans Azure

Dans cette tâche, vous allez créer une machine virtuelle Windows dans Azure.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu’administrateur ou administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Microsoft Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Sélectionnez **+ Créer une ressource**. **Conseil :** si vous étiez déjà dans le portail Azure, vous devrez peut-être sélectionner *Microsoft Azure* dans la barre supérieure pour accéder à l’accueil.

1. Dans la zone **Rechercher dans les services et la Place de marché**, entrez *Windows 10* et sélectionnez **Microsoft Window 10** dans la liste déroulante.

1. Sélectionnez la zone de **Microsoft Window 10**.

1. Ouvrez la liste déroulante *Abonnement* et sélectionnez **Windows 10 Entreprise, version 22H2**.

1. Sélectionnez **Démarrer avec une configuration prédéfinie** pour continuer.

1. Sélectionnez **Dev/Test**, puis **Continuer pour créer une machine virtuelle**.

1. Sélectionnez **Créer** pour le *groupe de ressources*, entrez RG-AZWIN01 pour le nom, et sélectionnez **OK**.

    >**Remarque :** il s’agit d’un nouveau groupe de ressources à des fins de suivi. 

1. Dans le *nom de la machine virtuelle*, entrez AZWIN01.

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

### Tâche 2 : connexion d'un serveur local à Azure

Dans cette tâche, vous allez connecter un serveur local à votre abonnement Azure. Azure Arc a été préinstallé sur ce serveur. Le serveur sera utilisé dans les exercices suivants pour exécuter des attaques simulées que vous détecterez et étudierez ultérieurement dans Microsoft Sentinel.

>**Important :** les étapes suivantes sont effectuées sur une machine différente de celle que vous utilisiez précédemment.

1. Connectez-vous à la machine virtuelle **WINServer** en tant qu'Administrateur avec le mot de passe suivant : **Passw0rd!** si nécessaire.  

    >**Remarque :** comme décrit ci-dessus, Azure Arc a été préinstallé sur la machine **WINServer**. Vous allez maintenant connecter cette machine à votre abonnement Azure.

1. Sur la machine *WINServer*, sélectionnez l’icône de *recherche* et entrez **cmd**.

1. Dans les résultats de la recherche, cliquez sur *Invite de commandes* avec le bouton droit, puis sélectionnez **Exécuter en tant qu’administrateur**.

1. Dans la fenêtre d’invite de commandes, tapez la commande suivante : *N’appuyez pas sur Entrée* :

    ```cmd
    azcmagent connect -g "defender-RG" -l "EastUS" -s "Subscription ID string"
    ```

1. Remplacez la **chaîne d’ID d’abonnement** par l’*ID d’abonnement* fourni par votre hébergeur de labo (*onglet Ressources). Veillez à conserver les guillemets.

1. Appuyez sur **Entrée** pour exécuter la commande (cela peut prendre quelques minutes).

    >**Remarque** : si vous voyez la fenêtre de sélection de navigateur *Comment voulez-vous ouvrir ceci ?*, sélectionnez **Microsoft Edge**. 

1. Dans la boîte de dialogue *Connexion*, entrez l’**e-mail du locataire** et le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**. Attendez le message *Authentification terminée*, fermez l’onglet du navigateur et revenez à la fenêtre *Invite de commandes*.

1. Une fois les commandes exécutées, laissez la fenêtre *Invite de commandes* ouverte et entrez la commande suivante pour vérifier que la connexion a réussi :

    ```cmd
    azcmagent show
    ```

1. Dans la sortie de la commande, vérifiez que l’*état de l’agent* est **Connecté**.

### Tâche 3 : connecter une machine virtuelle Windows Azure

Dans cette tâche, vous allez connecter une machine virtuelle Windows Azure à Microsoft Sentinel.

>**Remarque :** Microsoft Sentinel a été prédéployé dans votre abonnement Azure avec le nom **defenderWorkspace** et les solutions *Content Hub* requises ont été installées.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu’administrateur ou administratrice avec le mot de passe : **Pa55w.rd**.  

1. Si nécessaire, ouvrez le navigateur Microsoft Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>, puis connectez-vous avec les informations d’identification fournies.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez le **defenderWorkspace** Microsoft Sentinel.

1. Dans le menu de gauche de Microsoft Sentinel, faites défiler jusqu’à la section *Gestion du contenu*, puis sélectionnez **Hub de contenu**.

1. Dans le *hub de contenu*, recherchez la solution **Événements de sécurité Windows ** et sélectionnez-la dans la liste.

1. Dans la page de solution *Événements de sécurité Windows*, sélectionnez **Gérer**.

    >**Remarque :** la solution *Événements de sécurité Windows* installe les connecteurs de données *Événements de sécurité Windows via AMA* et *Événements de sécurité via l’ancien agent*. Plus 2 classeurs, 20 règles analytiques et 43 requêtes de repérage.

1. Sélectionnez le connecteur de données *Événements de sécurité Windows via AMA*, puis sélectionnez la page **Ouvrir le connecteur** dans le panneau d’informations du connecteur.

1. Dans la section *Configuration*, sélectionnez le bouton **+Créer une règle de collecte de données**.

1. Entrez **AZWINDCR** pour le nom de la règle, puis sélectionnez **Suivant : Ressources**.

1. Développez votre *Abonnement MOC* sous *Étendue* dans l’onglet *Ressources*.

    >**Conseil :** Vous pouvez développer l’ensemble de la hiérarchie *Étendue* en sélectionnant « > » devant la colonne *Étendue*.

1. Développez **defender-RG**, puis sélectionnez **AZWIN01**.

1. Sélectionnez **Suivant : Collecter**.

1. Passez en revue l’option de collecte des différents événements de sécurité. Conservez *tous les événements de sécurité*, puis sélectionnez **Suivant : Vérifier + créer**.

1. Sélectionnez **Créer** pour enregistrer la règle de collecte de données.

1. Attendez une minute, puis sélectionnez **Actualiser** pour voir apparaître la nouvelle règle de collecte de données.

### Tâche 4 : connecter une machine Windows non-Azure

Dans cette tâche, vous allez ajouter à Microsoft Sentinel une machine virtuelle Windows non-Azure connectée à Azure Arc.  

   >**Remarque :** le connecteur de données *Événements de sécurité Windows via AMA* nécessite Azure Arc pour les appareils non-Azure.

1. Vérifiez que vous êtes dans le connecteur de données *Événements de sécurité Windows via AMA* dans votre espace de travail Microsoft Sentinel.

1. Sous l’onglet *Configuration*, modifiez la *règle de collecte de données* **AZWINDCR** en sélectionnant l’icône en forme de *crayon*.

1. Sélectionnez **Suivant : Ressources** et développez votre *Abonnement MOC* sous *Étendue* sous l’onglet *Ressources*.

    >**Conseil :** Vous pouvez développer l’ensemble de la hiérarchie *Étendue* en sélectionnant « > » devant la colonne *Étendue*.

1. Développez **defender-RG** (ou le groupe de ressources que vous avez créé), puis sélectionnez **WINServer**.

    >**Important :** si vous ne voyez pas WINServer, reportez-vous au Parcours d’apprentissage 3, Exercice 1, Tâche 4 où vous avez installé Azure Arc sur ce serveur.

1. Sélectionnez **Suivant : Collecter**, puis **Suivant : Vérifier + créer**.

1. Sélectionnez **Créer** une fois que *Validation réussie* s’affiche.

## Passez à l’exercice 3
