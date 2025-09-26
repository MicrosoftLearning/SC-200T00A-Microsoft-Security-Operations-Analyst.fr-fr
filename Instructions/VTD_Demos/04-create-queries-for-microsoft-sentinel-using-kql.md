# Module 4 : créer des requêtes pour Microsoft Sentinel avec le langage de requête Kusto (KQL)

<!--- **Note** Successful completion of this demo depends on completing all of the steps in the  [Pre-requisites document](00-prerequisites.md). --->

>**Important :** Nous vous recommandons d’effectuer les requêtes pour ce labo dans l’environnement de démonstration Zava (anciennement Alpine Ski House). Vous pouvez également utiliser l’environnement de labo SC-200 avec le labo 06 - [Créer des requêtes pour Microsoft Sentinel à l’aide du langage de requête Kusto (KQL)](https://microsoftlearning.github.io/SC-200T00A-Microsoft-Security-Operations-Analyst/Instructions/Labs/LAB_AK_06_Lab1_Ex01_KQL.html/). Ce dernier nécessite 30 minutes de temps de déploiement.

## Accéder à la zone de test KQL

Dans cette tâche, vous accéderez à un environnement Microsoft Sentinel Log Analytics où vous pourrez vous entraîner à écrire des instructions KQL.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur avec le mot de passe suivant : **Pa55w.rd**.  

1. Accédez à <https://security.microsoft.com> dans votre navigateur. Connectez-vous avec les informations d’identification d’utilisateur Zava ou Alpine Ski House.

1. Développez la section **Enquête et réponse** dans le volet de navigation à gauche.

1. Développez la section **Repérage** et sélectionnez **Repérage avancé**.

1. Explorez les tables disponibles répertoriées dans l’onglet *Schéma* situé à gauche de l’écran. Notez les tables *Microsoft Sentinel* et *Security and Audit*.

1. Dans l’éditeur de requête, entrez la requête suivante, puis sélectionnez le bouton Exécuter.  Vous devez voir les résultats de la requête dans la fenêtre inférieure.

    ```KQL
    SecurityEvent
    ```

1. En regard du premier enregistrement, sélectionnez le bouton **>** pour développer les informations de la ligne.

### Tâche 2 : exécuter des instructions KQL simples

Dans cette tâche, vous allez créer des instructions KQL simples.

1. L’opérateur `search` fournit une expérience de recherche dans plusieurs tables ou plusieurs colonnes. Les requêtes suivantes illustrent l’utilisation de l’opérateur `search` :

    > **Remarque :** L’opérateur `search` est très gourmand en ressources. Limitez l’*Intervalle de temps* à *3 dernières heures* et utilisez *limit | 100*.

```KQL
search "err" 

search in (SecurityEvent,SecurityAlert,A*) "err"
```

1. L’opérateur `where` filtre une table d’après le sous-ensemble de lignes correspondant à un prédicat. Les requêtes suivantes illustrent l’utilisation de l’opérateur `where` :

```KQL
SecurityEvent | where EventID in (4624, 4625)

SecurityEvent 
| where TimeGenerated > ago(1d) 

SecurityEvent 
| where TimeGenerated > ago(1h) and EventID == "4624" 

SecurityEvent 
| where TimeGenerated > ago(1h) 
| where EventID == 4624 
| where AccountType =~ "user" 
```

1. L’instruction suivante illustre l’utilisation de l’instruction `let` pour déclarer des variables. Dans la fenêtre Requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** : 

```KQL
let timeOffset = 7d;
let discardEventId = 4688;
SecurityEvent
| where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)
| where EventID != discardEventId
```

1. L’instruction suivante illustre l’utilisation de l’instruction `let` pour déclarer une liste dynamique. Dans la fenêtre Requête, entrez l’instruction suivante, puis sélectionnez **Exécuter**. 

```KQL
let suspiciousAccounts = datatable(account: string) [
    @"\administrator", 
    @"NT AUTHORITY\SYSTEM"
];
SecurityEvent | where Account in (suspiciousAccounts)
```

1. L’instruction suivante illustre la recherche, dans toutes les tables et colonnes, des enregistrements situés dans l’intervalle de temps de la requête affiché dans la fenêtre Requête. Dans la fenêtre Requête, avant d’exécuter ce script, remplacez l’intervalle de temps par « Dernière heure ». Entrez l’instruction suivante et sélectionnez **Exécuter** :

```KQL
search "err"
```

**Avertissement :** veillez à revenir à l’intervalle de temps « Dernières 24 heures » pour les scripts suivants.

### Créer des visualisations dans KQL avec l’opérateur de rendu

Dans cette tâche, vous allez créer des visualisations à l’aide d’instructions KQL.

1. L’instruction suivante illustre la fonction de rendu pour visualiser les résultats sous la forme d’un graphique à barres. Dans la fenêtre Requête. Entrez l’instruction suivante et sélectionnez **Exécuter** : 

```KQL
SecurityEvent 
| summarize count() by Account
| render barchart
```

1. L’instruction suivante illustre la fonction de rendu pour visualiser les résultats sous la forme d’une série chronologique.

Fonction bin() : arrondit les valeurs à l’entier inférieur multiple d’une taille de compartiment donnée.  Utilisé fréquemment en combinaison avec summarize by ..... Si vous avez un ensemble de valeurs éparses, les valeurs sont regroupées en un ensemble plus petit de valeurs spécifiques.  La combinaison de la série chronologique et du canal générés à un opérateur de rendu de type graphique temporel fournit une visualisation de série chronologique. Dans la fenêtre Requête. Entrez l’instruction suivante et sélectionnez **Exécuter** : 

```KQL
SecurityEvent 
| summarize count() by bin(TimeGenerated, 1d) 
| render timechart
```

## Vous avez terminé la démonstration
