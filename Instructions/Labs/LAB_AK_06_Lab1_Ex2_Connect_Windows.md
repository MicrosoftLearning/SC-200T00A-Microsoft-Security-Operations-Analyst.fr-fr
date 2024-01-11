---
lab:
  title: "Exercice\_2 - Connecter des appareils Windows à Microsoft\_Sentinel avec des connecteurs de données"
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Parcours d’apprentissage 6 - Labo 1 - Exercice 2 - Connecter des appareils Windows à Microsoft Sentinel avec des connecteurs de données

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex2.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous devez apprendre à connecter des données de journal provenant de nombreuses sources de données dans votre organisation. La source de données suivante est des machines virtuelles Windows à l’intérieur et à l’extérieur d’Azure, comme les environnements locaux ou d’autres clouds publics.

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Connect%20Windows%20devices%20to%20Microsoft%20Sentinel%20using%20data%20connectors)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 


### Tâche 1 : créer une machine virtuelle Windows dans Azure

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

### Tâche 2 : connecter une machine virtuelle Windows Azure

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

### Tâche 3 : connecter une machine Windows non-Azure

Dans cette tâche, vous allez ajouter à Microsoft Sentinel une machine virtuelle Windows non-Azure connectée à Azure Arc.  

   >**Remarque :** le connecteur de données *Événements de sécurité Windows via AMA* nécessite Azure Arc pour les appareils non-Azure.

1. Vérifiez que vous êtes dans le connecteur de données *Événements de sécurité Windows via AMA* dans votre espace de travail Microsoft Sentinel.

1. Sous l’onglet **Instructions**, dans la section *Configuration*, modifiez la *règle de collecte de données* **AZWINDCR** en sélectionnant l’icône en forme de *crayon*.

1. Sélectionnez **Suivant : Ressources** et **+ Ajouter une ou plusieurs ressources**.

1. Développez **RG-Defender** (ou le groupe de ressources que vous avez créé), puis sélectionnez **WINServer**.

    >**Important :** si vous ne voyez pas WINServer, reportez-vous au Parcours d’apprentissage 3, Exercice 1, Tâche 4 où vous avez installé Azure Arc sur ce serveur.

1. Sélectionnez **Appliquer**.

1. Sélectionnez **Suivant : Collecter**, puis **Suivant : Vérifier + créer**.

1. Sélectionnez **Créer** une fois que *Validation réussie* s’affiche.

## Passez à l’exercice 3
