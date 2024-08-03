---
lab:
  title: "Exercice\_1\_: configurer votre environnement Microsoft\_Sentinel"
  module: Learning Path 5 - Configure your Microsoft Sentinel environment
---

# Parcours d’apprentissage 5 - Labo 1 - Exercice 1 - Configurer votre environnement Microsoft Sentinel

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod5_L1_Ex1.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise qui implémente Microsoft Azure Sentinel. Vous êtes responsable de la configuration de l’environnement Microsoft Sentinel pour répondre aux besoins de l’entreprise de réduire les coûts, de respecter les réglementations en matière de conformité et de fournir l’environnement le plus adapté aux tâches quotidiennes de votre équipe de sécurité.

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Configure%20your%20Microsoft%20Sentinel%20environment)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 


### Tâche 1 : initialiser l’espace de travail Microsoft Sentinel

Dans cette tâche, vous allez créer un espace de travail Microsoft Sentinel.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu'Admin avec le mot de passe suivant : **Pa55w.rd**.  

1. Ouvrez le navigateur Edge.

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez **+ Créer**.

1. Sélectionnez ensuite l’espace de travail Log Analytics que vous avez créé précédemment, par exemple *uniquenameDefender*, puis sélectionnez **Ajouter**. L’activation peut prendre plusieurs minutes.

    >**Remarque :** si vous ne voyez pas d’espace de travail Log Analytics ici, reportez-vous au module 3, exercice 1, tâche 2 pour en créer un.

1. Dans **Microsoft Sentinel**, vous devriez être dans la section **Général** de *Actualités et guides* et voir un avis indiquant *L’essai gratuit de Microsoft Sentinel est activé*. Cliquez sur le bouton **OK**.

1. Parcourez l’espace de travail Microsoft Sentinel nouvellement créé pour vous familiariser avec les options de l’interface utilisateur.

### Tâche 2 : créer une watchlist

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


### Tâche 3 : créer un indicateur de menaces

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


### Tâche 4 : configurer la rétention des journaux

Dans cette tâche, vous allez modifier la période de rétention de la table SecurityEvent.

1. Dans Microsoft Sentinel, sélectionnez l’option **Paramètres** dans la zone *Configuration*.

1. Sélectionnez **Paramètres de l’espace de travail**.

1. Dans l’espace de travail Log Analytics, sélectionnez l’option **Tables** dans la zone *Paramètres*.

1. Recherchez et sélectionnez la table **SecurityEvent**, puis sélectionnez le bouton en forme de points de suspension (…).

1. Sélectionnez **Gérer la table**.

1. Sélectionnez **180 jours** pour la *période totale de rétention*. Notez que la *période d’archivage* n’est que de 150 jours, car elle utilise 30 jours de la *rétention interactive* (par défaut).

1. Sélectionnez **Enregistrer** pour appliquer la modification.


## Vous avez terminé le labo.
