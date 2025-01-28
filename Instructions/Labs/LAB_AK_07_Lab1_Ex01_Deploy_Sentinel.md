---
lab:
  title: "Exercice\_1\_: configurer votre environnement Microsoft\_Sentinel"
  module: Learning Path 7 - Configure your Microsoft Sentinel environment
---

# Parcours d’apprentissage 7 - Labo 1 - Exercice 1 - Configurer votre environnement Microsoft Sentinel

## Scénario de labo

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise qui implémente Microsoft Azure Sentinel. Vous êtes responsable de la configuration de l’environnement Microsoft Sentinel pour répondre aux besoins de l’entreprise de réduire les coûts, de respecter les réglementations en matière de conformité et de fournir l’environnement le plus adapté aux tâches quotidiennes de votre équipe de sécurité.

>**Important :** les exercices de labo du parcours d’apprentissage #7 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

### Temps estimé pour terminer ce labo : 30 minutes

### Tâche 1 : Créer un espace de travail Log Analytics

Créez un espace de travail Log Analytics, y compris l’option de région. En savoir plus sur l’[intégration Microsoft Sentinel](https://learn.microsoft.com/azure/sentinel/quickstart-onboard).

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu'Admin avec le mot de passe suivant : **Pa55w.rd**.

1. Dans le navigateur Microsoft Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.
  
1. Dans la boîte de dialogue **Se connecter** , copiez et collez le compte de messagerie du locataire pour le nom d’utilisateur administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le mot de passe du locataire de l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Se connecter**.

1. Dans la barre de recherche du portail Azure, saisissez « Microsoft Sentinel », puis sélectionnez-le.

1. Sélectionnez **+ Créer**.

1. Sélectionnez **Créer un espace de travail**.

1. Sélectionnez **Créer** pour le groupe de ressources.

1. Entrez *RG-Defender*, puis sélectionnez **OK**.

1. Entrez *defenderWorkspace* pour le nom.

1. Vous pouvez conserver la région par défaut de l’espace de travail.

1. Sélectionnez **Vérifier + créer** pour valider le nouvel espace de travail.

1. Sélectionnez **Créer** pour déployer l’espace de travail.

### Tâche 2 : Déployer Microsoft Sentinel dans un espace de travail

Déployez Microsoft Sentinel dans l’espace de travail.

1. Une fois le déploiement de l’espace de travail terminé, sélectionnez **Actualiser** pour afficher le nouvel espace de travail.

1. Sélectionnez l’espace de travail auquel vous souhaitez ajouter Sentinel (créé lors de la tâche 1).

1. Sélectionnez **Ajouter**.

### Tâche 3 : configurer la rétention des données

1. Dans le menu de navigation de Microsoft Azure, sélectionnez **Accueil**.

1. Dans la barre de recherche du portail Azure, saisissez « Espaces de travail Log Analytics », puis sélectionnez l’espace de travail créé lors de la tâche 1.

1. Développez la section *Paramètres* dans le menu de navigation, puis sélectionnez **Utilisation et coûts estimés**.

1. Sélectionnez **Rétention des données**.

1. Modifiez la période de rétention en la portant à **180 jours**.

1. Cliquez sur **OK**.

### Tâche 4 : créer une watchlist

Dans cette tâche, vous allez créer une watchlist dans Microsoft Sentinel.

1. Dans la zone de recherche située en bas de l’écran Windows 10, entrez *Bloc-notes*. Sélectionnez **Bloc-notes** dans les résultats.

1. Tapez le *nom d’hôte*, puis cliquez sur Entrée pour passer à la ligne suivante.

1. À partir de la ligne 2 du bloc-notes, copiez les noms d’hôte suivants, chacun sur une ligne différente :

    ```Notepad
    Host1
    Host2
    Host3
    Host4
    Host5
    ```

1. Dans le menu, sélectionnez **Fichier - Enregistrer sous**, nommez le fichier *HighValue.csv*, remplacez le type de fichier par **Tous les fichiers (*.*)** et sélectionnez **Enregistrer**. **Conseil :** le fichier peut être enregistré dans le dossier *Documents*.

1. Fermez le Bloc-notes.

1. Dans Microsoft Sentinel, sélectionnez l’option **Watchlist** sous la zone Configuration.

1. Sélectionnez **+ Nouveau** dans la barre de commandes.

1. Dans l’assistant Watchlist, entrez les éléments suivants :

    |Paramètres généraux|Valeur|
    |---|---|
    |Nom|**HighValueHosts**|
    |Description|**Hôtes à valeur élevée**|
    |Alias Watchlist|**HighValueHosts**|

1. Sélectionnez **Suivant : Source >**.

1. Sélectionnez **Parcourir les fichiers** sous *Charger un fichier* et recherchez le fichier *HighValue.csv* que vous venez de créer.

1. Dans le *champ SearchKey*, sélectionnez **Nom d’hôte**.

1. Sélectionnez **Suivant : Vérifier et créer >**.

1. Passez en revue les paramètres que vous avez entrés, puis sélectionnez **Créer**.

1. L’écran revient à la page Watchlist.

1. Sélectionnez la watchlist *HighValueHosts* et, dans le volet droit, sélectionnez **Voir dans les journaux**.

    >**Important :** l’affichage de la watchlist peut prendre jusqu’à dix minutes. **Passez à la tâche suivante et exécutez cette commande sur le labo suivant**.

    >**Remarque :** vous pouvez maintenant utiliser la fonction _GetWatchlist('HighValueHosts') dans vos propres instructions KQL pour accéder à la liste. La colonne à laquelle il faut faire référence est *Hostname*.

1. Fermez la fenêtre *Journaux* en sélectionnant « x » en haut à droite, puis sélectionnez **OK** pour ignorer les modifications non enregistrées.

### Tâche 5 : créer un indicateur de menaces

Dans cette tâche, vous allez créer un indicateur dans Microsoft Sentinel.

1. Dans Microsoft Sentinel, sélectionnez l’option **Renseignement sur les menaces** dans la zone Gestion des menaces.

1. Sélectionnez **+ Ajouter** dans la barre de commandes.

1. Passez en revue les différents types d’indicateurs disponibles dans la liste déroulante *Types*. Sélectionnez ensuite **domain-name**. 

1. Dans Domaine, entrez le nom de domaine, par exemple : *contoso.com*.

1. Pour les *types de menaces*, sélectionnez **+ Ajouter** et saisissez **malicious-activity**. Sélectionnez **Appliquer**.

1. Entrez une **Description**.

1. Pour le **nom**, entrez la même valeur que celle utilisée pour le domaine.

1. Définissez la valeur du champ **Valide à partir du** sur la date du jour.

1. Sélectionnez **Appliquer**.

1. Sélectionnez l’option **Journaux** dans la zone Général. Vous pouvez désactiver l’option « Toujours afficher les requêtes » et fermer la fenêtre *Requêtes* pour exécuter les instructions KQL.

1. Exécutez la commande KQL suivante.

    ```KQL
    ThreatIntelligenceIndicator
    ```

    >**Remarque :** l’affichage de l’indicateur peut prendre jusqu’à cinq minutes.

1. Faites défiler les résultats vers la droite jusqu’à la colonne DomainName. Vous pouvez également exécuter l’instruction KQL suivante pour afficher simplement la colonne DomainName. 

    ```KQL
    ThreatIntelligenceIndicator 
    | project DomainName
    ```

### Tâche 6 : configurer la rétention des journaux

Dans cette tâche, vous allez modifier la période de rétention de la table SecurityEvent.

1. Dans Microsoft Sentinel, sélectionnez l’option **Paramètres** dans la zone *Configuration*.

1. Sélectionnez **Paramètres de l’espace de travail**.

1. Dans l’espace de travail Log Analytics, sélectionnez l’option **Tables** dans la zone *Paramètres*.

1. Recherchez et sélectionnez la table **SecurityEvent**, puis sélectionnez le bouton en forme de points de suspension (…).

1. Sélectionnez **Gérer la table**.

1. Sélectionnez **180 jours** pour la *période totale de rétention*. Notez que la *période d’archivage* n’est que de 150 jours, car elle utilise 30 jours de la *rétention interactive* (par défaut).

1. Sélectionnez **Enregistrer** pour appliquer la modification.

## Vous avez terminé le labo
