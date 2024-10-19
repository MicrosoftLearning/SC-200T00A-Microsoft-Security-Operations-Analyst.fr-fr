# Module 5 : configuration de votre environnement Microsoft Sentinel

**Remarque** : la réussite de cette démonstration dépend de l’exécution correcte de toutes les étapes décrites dans le [document sur les conditions préalables](00-prerequisites.md).

**Important :** cette version de démonstration n’est pas requise pour VTD-5002-FY25.

## Explorer l'interface de Microsoft Sentinel

1. Revenez à l’instance Microsoft Sentinel que vous avez créée dans la [section Conditions préalables](00-prerequisites.md#deploy-azure-sentinel-workspace-for-demo-in-module-4).

1. Parcourez l’espace de travail Microsoft Sentinel nouvellement créé pour vous familiariser avec les options de l’interface utilisateur.

## Créer une Watchlist

Dans cette tâche, vous allez créer une watchlist.

1. Dans la zone de recherche située en bas de l’écran, entrez `Notepad`.  Sélectionnez **Bloc-notes** dans les résultats.

1. Tapez `Hostname` puis appuyez sur Entrée pour créer une nouvelle ligne.

1. Dans les lignes 2 à 6, ajoutez les noms d’hôte suivants :
    ```
    Host1
    Host2
    Host3
    Host4
    Host5
    ```

1. Dans le menu, sélectionnez **Fichier - Enregistrer sous** et nommez le fichier `HighValue.csv`.  Remplacez ensuite le type de fichier par **Tous les fichiers(*.*)**.  Ensuite, sélectionnez **Enregistrer**.

1. Fermez le Bloc-notes.

1. Dans Microsoft Sentinel, sélectionnez l’option **Watchlist** dans la zone **Mes watchlists**.

1. Cliquez sur **Ajouter nouveau** dans la barre de commandes.

1. Dans l’Assistant Watchlist, entrez les éléments suivants :  Nom : HighValueHosts  Description : High Value Hosts  Alias de Watchlist : HighValueHosts

1. Sélectionnez **Suivant : Source >**.

1. Recherchez le fichier `HighValue.csv` que vous venez de créer. 

1. Une fois le fichier CSV chargé, sélectionnez **Nom d’hôte** dans la zone de liste déroulante du **champ SearchKey**.

1. Sélectionnez **Suivant : Vérifier et créer >**.

1. Sélectionnez **Créer**.

1. L’écran revient à la liste des watchlists.

1. Sélectionnez votre nouvelle watchlist.  Sous l’onglet droit, sélectionnez **Afficher dans Log Analytics**.

1. L’instruction KQL suivante est exécutée automatiquement avec les résultats affichés.

```KQL
_GetWatchlist('HighValueHosts')
```
**Remarque** : l’importation peut prendre une minute.

Vous pouvez maintenant utiliser la fonction _GetWatchlist('HighValueHosts') dans vos propres instructions KQL pour accéder à la liste. La colonne à laquelle il faut faire référence est *Hostname*.

## Créer un indicateur de menaces

Dans cette tâche, vous allez créer un indicateur.

1. Dans Microsoft Sentinel, sélectionnez l’option **Renseignement sur les menaces** dans la zone **Gestion des menaces**.

1. Cliquez sur **Ajouter nouveau** dans la barre de commandes.

1. Passez en revue les différents types d’indicateurs disponibles dans la liste déroulante Types.  Sélectionnez ensuite **domain-name**. Entrez vos initiales dans la zone Domaine. Par exemple, fmg.com.

1. Pour le type de menace, sélectionnez **+ Ajouter**, puis copiez et collez **malicious-activity** dans le champ.

1. Pour le nom, entrez la même valeur que celle utilisée pour le domaine. Par exemple, fmg.com.

1. Définissez la valeur du champ **Valide à partir du** sur la date du jour.

1. Sélectionnez **Appliquer**.

**Remarque** : l’affichage de l’indicateur peut prendre une minute.

1. Sélectionnez l’option **Journaux** dans la zone Général.  Vous devrez peut-être désactiver l’option « Toujours afficher les requêtes » pour accéder à la fenêtre Requête.

1. Exécutez la commande KQL suivante.

```KQL
ThreatIntelligenceIndicator 
```
Faites défiler les résultats vers la droite jusqu’à la colonne DomainName. Vous pouvez également exécuter l’instruction KQL suivante pour afficher simplement la colonne DomainName.  

```KQL
ThreatIntelligenceIndicator 
| project DomainName
```
## Vous avez terminé la démonstration.