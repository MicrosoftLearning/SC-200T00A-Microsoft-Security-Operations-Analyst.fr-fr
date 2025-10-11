---
lab:
  title: "Exercice\_1\_: créer des requêtes pour Microsoft\_Sentinel avec le langage de requête Kusto (KQL)"
  module: Learning Path 6 - Create queries for Microsoft Sentinel using Kusto Query Language (KQL)
---

# Parcours d’apprentissage 6 - Labo 1- Exercice 1 - Créer des requêtes pour Microsoft Sentinel avec le langage de requête Kusto (KQL)

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod4_L1_Ex1.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise qui implémente Microsoft Sentinel. Vous êtes chargé d’effectuer une analyse des données de journal pour rechercher des activités malveillantes, afficher des visualisations et faire la chasse aux menaces. Pour interroger les données du journal, vous utilisez le langage de requête Kusto (KQL).

>**Important :** Les exercices pratiques du parcours d’apprentissage n°6 se déroulent dans un environnement *autonome*. Si vous quittez le labo avant de l’avoir terminé, vous devrez recommencer toutes les étapes de configuration.

>**Remarque :** La génération complète de ce profil de labo prend plus de 15 minutes, car Microsoft Sentinel est pré-déployé dans votre abonnement Azure sous le nom **defenderWorkspace**.

<!--- >**Tip:** This lab involves entering many KQL scripts into Microsoft Sentinel. The scripts were provided in a file at the beginning of this lab. An alternate location to download them is:  <https://github.com/MicrosoftLearning/SC-200T00A-Microsoft-Security-Operations-Analyst/tree/master/Allfiles> --->

### Temps estimé pour terminer ce labo : 60 minutes

### Tâche 1 : Préparer la zone de test KQL

Dans cette tâche, vous installez **Microsoft Sentinel Training Lab Solution** à partir de la Place de marché, qui remplira un espace de travail Log Analytics avec des exemples de données que vous pourrez utiliser pour vous entraîner à écrire des instructions KQL.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu’administrateur ou administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Microsoft Edge, accédez à <https://portal.azure.com> et connectez-vous avec les informations d’identification attribuées.

1. Dans la barre de recherche Azure, tapez **Microsoft Sentinel Training Lab Solution** et sélectionnez-la dans les résultats.

    >**Conseil :** Elle se trouve dans la section Place de marché.

1. Dans la **Microsoft Sentinel Training Lab Solution**, sélectionnez **Créer** pour installer la solution.

1. Dans la page **Créer Microsoft Sentinel Training Lab Solution**, sélectionnez le groupe de ressources **defender-RG** et l’espace de travail **defenderWorkspace**.

1. Sélectionnez **Passer en revue + créer** pour déployer la solution.

1. Une fois la validation terminée, sélectionnez **Créer** pour déployer la solution.

  >**Remarque :** Il faut environ dix minutes pour que la solution soit entièrement déployée et que toutes les ressources soient disponibles.

1. Attendez la fin du déploiement, puis sélectionnez **Accueil** dans l’exploration à l’aide de la barre de navigation.

### Tâche 2 : Explorer l’espace de travail Log Analytics

1. Dans la barre de recherche du portail Azure, tapez **Microsoft Sentinel** et sélectionnez-le dans les résultats.

1. Sur la page Microsoft Sentinel, sélectionnez l’espace de travail **defenderWorkspace**.

1. Dans Microsoft Sentinel, développez la section **Général** et sélectionnez **Journaux** dans le menu de navigation.

1. Fermez la fenêtre contextuelle de la vidéo Log Analytics qui s’affiche.

1. Fermez le **Hub des requêtes**.

1. Utilisez le menu déroulant pour passer du **mode simple** au **mode KQL**.

1. Explorez les tables disponibles et les autres outils dans le volet *Schéma et filtre* situé sur le côté gauche de l’écran.

1. Dans l’éditeur de requête, entrez la requête suivante, puis sélectionnez le bouton **Exécuter**. Vous devez voir les résultats de la requête dans la fenêtre inférieure.

    ```KQL
    SecurityEvent_CL
    ```

    >**Remarque :** La table *SecurityEvent_CL* est une table personnalisée créée par Microsoft Sentinel Training Lab Solution. Elle contient des exemples de données que vous pouvez utiliser pour vous entraîner à écrire des instructions KQL.

1. Notez que le filtre est défini sur **Afficher : 1000 résultats**.

1. En regard du premier enregistrement, sélectionnez le bouton **>** pour développer les informations de la ligne.

### Tâche 3 : Exécuter des instructions KQL de base

Dans cette tâche, vous allez créer des instructions KQL simples.

>**Important :** pour chaque requête, effacez l’instruction précédente de la fenêtre de requête ou ouvrez une nouvelle fenêtre de requête en sélectionnant **+** après le dernier onglet ouvert (jusqu’à 25).

1. L’instruction suivante illustre l’opérateur **Search**, qui recherche la valeur dans toutes les colonnes de la table.

1. Dans la fenêtre de requête, l’*Intervalle de temps* doit être défini par défaut sur **24 dernières heures**.

1. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    search "Computer"
    ```

    >**Remarque :** L’utilisation de l’opérateur *Search* sans tables spécifiques ou clauses éligibles est moins efficace que le filtrage de texte spécifique à une table ou à une colonne.

1. L’instruction suivante illustre l’opérateur **search** dans les tables répertoriées dans la clause **In**. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    search in (SecurityEvent_CL,App*) "new"
    ```

1. Changez l’*intervalle de temps* et définissez-le sur **Dernières 24 heures** dans la fenêtre de requête.

1. Les instructions suivantes illustrent l’opérateur **Where**, qui filtre selon un prédicat spécifique. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    >**Important :** vous devez sélectionner **Exécuter** après avoir entré chaque requête des blocs de code ci-dessous.

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    ```

    >**Remarque :** l’*intervalle de temps* affiche désormais *Défini dans la requête*, car nous filtrons avec la colonne TimeGenerated.

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) and EventID_s == 4624
    ```

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | where EventID_s == 4624  
    | where AccountType_s =~ "user"
    ```

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) and EventID_s in (4624, 4625)
 
    ```

1. L’instruction suivante illustre l’utilisation de l’instruction **Let** pour déclarer des *variables*. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    let timeOffset = 1h;
    let discardEventID = 4688;
    SecurityEvent_CL
    | where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)
    | where EventID_s != discardEventID
    ```

1. L’instruction suivante illustre l’utilisation de l’instruction **Let** pour déclarer une *liste dynamique*. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    let suspiciousAccounts = datatable(account: string) [
      @"NA\timadmin", 
      @"NT AUTHORITY\SYSTEM"
    ];
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | where Account_s in (suspiciousAccounts)
    ```

    >**Conseil :** vous pouvez facilement mettre en forme la requête en sélectionnant les points de suspension (…) dans la fenêtre de requête et en sélectionnant **Mettre en forme la requête**.

1. L’instruction suivante illustre l’utilisation de l’instruction **Let** pour déclarer une *table dynamique*. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    let LowActivityAccounts =
        SecurityEvent_CL 
        | summarize cnt = count() by Account_s 
        | where cnt < 1000;
    LowActivityAccounts | where Account_s contains "sql"
    ```

### Tâche 4 : Analyser les résultats dans KQL avec l’opérateur Summarize

Dans cette tâche, vous allez créer des instructions KQL pour agréger des données. L’opérateur de **Synthèse** regroupe les lignes en fonction du **regroupement** de colonnes et calcule les agrégations sur chaque groupe

1. L’instruction suivante illustre la fonction **count()**, qui renvoie le compte du groupe. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) and EventID_s == 4688  
    | summarize count() by Computer
    ```

1. L’instruction suivante illustre la fonction **count()**, mais dans cet exemple, nous allons nommer la colonne *cnt*. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) and EventID_s == 4624  
    | summarize cnt=count() by AccountType_s, Computer
    ```

1. L’instruction suivante illustre la fonction **dcount()**, qui renvoie le compte distinct approximatif des éléments de groupe. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    SigninLogs_CL  
    | where TimeGenerated > ago(7d)
    | summarize dcount(IpAddress)
    ```

1. L’instruction suivante est une règle permettant de détecter les échecs pour cause de mot de passe non valide sur plusieurs applications pour le même compte. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    let timeframe = 30d;
    let threshold = 1;
    SigninLogs_CL
    | where TimeGenerated >= ago(timeframe)
    | where ResultDescription has "Invalid password"
    | summarize applicationCount = dcount(AppDisplayName_s) by UserPrincipalName_s, IPAddress
    | where applicationCount >= threshold
    ```

1. L’instruction suivante illustre la fonction **arg_max()**, qui renvoie une ou plusieurs expressions lorsque l’argument est maximisé. L’instruction suivante renvoie la ligne la plus récente de la table SecurityEvent_CL pour l’ordinateur *VictimPC2*. Le * dans la fonction arg_max demande toutes les colonnes de la ligne. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    SecurityEvent_CL  
    | where Computer == "VictimPC2"
    | summarize arg_max(TimeGenerated,*) by Computer
    ```

1. L’instruction suivante illustre la fonction **arg_min()**, qui renvoie une ou plusieurs expressions lorsque l’argument est minimisé. Dans cette instruction, l’événement le plus ancien de SecurityEvent_CL pour l’ordinateur *VictimPC2* sera renvoyé comme jeu de résultats. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    SecurityEvent_CL  
    | where Computer == "VictimPC2"
    | summarize arg_min(TimeGenerated,*) by Computer
    ```

1. Les instructions suivantes illustrent l’importance de comprendre les résultats en fonction de l’ordre du *canal*. Dans la fenêtre Requête, entrez les requêtes suivantes et exécutez-les individuellement :

    1. La **requête 1** a des comptes pour lesquels la dernière activité était une connexion. La table SecurityEvent_CL sera d’abord résumée et renverra la ligne la plus récente pour chaque compte. Ensuite, seules les lignes dont EventID_s est égal à 4 624 (connexion) seront renvoyées.

        ```KQL
        SecurityEvent_CL  
        | summarize arg_max(TimeGenerated, *) by Account_s 
        | where EventID_s == 4624  
        ```

    1. La **requête 2** a la connexion la plus récente pour les comptes qui se sont connectés. La table SecurityEvent_CL est filtrée pour inclure uniquement EventID_s = 4 624. Ces résultats sont résumés pour la ligne de connexion la plus récente par compte.

        ```KQL
        SecurityEvent_CL  
        | where EventID_s == 4624  
        | summarize arg_max(TimeGenerated, *) by Account_s
        ```

    >**Remarque :**  vous pouvez également consulter le « Total UC » et les « Données utilisées pour la requête traitée » en sélectionnant le lien « Détails de la requête », situé en bas à droite et comparer les données entre les deux instructions.

1. L’instruction suivante illustre la fonction **make_list()**, qui renvoie une *liste* de toutes les valeurs dans le groupe. Cette requête KQL filtrera d’abord EventID_s à l’aide de l’opérateur Où. Ensuite, pour chaque ordinateur, les résultats sont un tableau de comptes JSON. Le tableau JSON résultant inclura des comptes dupliqués. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** : 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | where EventID_s == 4624  
    | summarize make_list(Account_s) by Computer
    ```

1. L’instruction suivante illustre la fonction **make_set()**, qui renvoie un jeu de valeurs *distinctes* dans le groupe. Cette requête KQL filtrera d’abord EventID_s à l’aide de l’opérateur Où. Ensuite, pour chaque ordinateur, les résultats sont un tableau de comptes JSON. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** : 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | where EventID_s == 4624  
    | summarize make_set(Account_s) by Computer
    ```

### Tâche 5 : Créer des visualisations en KQL avec l’Opérateur d’affichage

Dans cette tâche, vous allez créer des visualisations à l’aide d’instructions KQL.

1. L’instruction suivante illustre l’opérateur de **rendu** (qui affiche les résultats sous forme de graphique), avec une visualisation sous forme de **graphique à barres**. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** : 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | summarize count() by Account_s
    | render barchart
    ```

1. L’instruction suivante illustre l’opérateur de **rendu**, qui permet d’afficher les résultats dans une série chronologique. La fonction **bin()** arrondit toutes les valeurs d’une période et les regroupe. Elle est souvent associée à l’opérateur de **synthèse**. Si vous avez un ensemble de valeurs éparses, les valeurs sont regroupées en un ensemble plus petit de valeurs spécifiques. En combinant les résultats générés et en les redirigeant vers un opérateur de **rendu** de type **graphique temporel**, nous obtenons une visualisation de série chronologique. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** : 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | summarize count() by bin(TimeGenerated, 1m)
    | render timechart
    ```

### Tâche 6 : Générer des instructions de tables multiples à l’aide de KQL

Dans cette tâche, vous allez générer des instructions KQL à plusieurs tables.

1. Modifiez l’**intervalle de temps** et définissez-le sur **7 derniers jours** dans la fenêtre de requête. Cela limite nos résultats pour les instructions suivantes.

1. L’instruction suivante illustre l’opérateur **Union**, qui prend deux tables ou plus et retourne toutes leurs lignes. Il est essentiel de comprendre comment les résultats sont passés et affectés par le caractère de barre verticale. Dans la fenêtre Requête, entrez les instructions suivantes et sélectionnez **Exécuter** pour chaque requête séparément afin d’afficher les résultats :

    1. La **Requête 1** renvoie toutes les lignes de SecurityEvent_CL et toutes les lignes de SigninLogs_CL.

        ```KQL
        SecurityEvent_CL  
        | union SigninLogs_CL  
        ```

    1. La **Requête 2** renvoie une ligne et une colonne, qui correspondent au nombre total de lignes de SigninLogs_CL et de SecurityEvent_CL.

        ```KQL
        SecurityEvent_CL  
        | union SigninLogs_CL  
        | summarize count() 
        ```

    1. La **Requête 3** renvoie toutes les lignes de SecurityEvent_CL et une (dernière) ligne pour SigninLogs_CL. La dernière ligne de SigninLogs_CL contient le nombre total de lignes.

        ```KQL
        SecurityEvent_CL  
        | union (SigninLogs_CL | summarize count() | project count_)
        ```

    >**Remarque :** La « ligne vide » dans les résultats affichera le nombre total de lignes de SigninLogs_CL.

1. L’instruction suivante illustre la prise en charge de l’opérateur **Union** pour l’union de plusieurs tables avec des caractères génériques. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** : 

    ```KQL
    union App*  
    | summarize count() by Type
    ```

1. L’instruction suivant illustre l’opérateur **Join**, qui fusionne les lignes de deux tables pour en former une nouvelle en mettant en correspondance les valeurs des colonnes spécifiées de chaque table. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    SecurityEvent_CL  
    | where EventID_s == 4624 
    | summarize LogOnCount=count() by  EventID_s, Account_s
    | project LogOnCount, Account_s
    | join kind = inner( 
     SecurityEvent_CL  
    | where EventID_s == 4634 
    | summarize LogOffCount=count() by  EventID_s, Account_s
    | project LogOffCount, Account_s
    ) on Account_s
    ```

    >**Important** : la première table spécifiée dans la jointure est considérée comme la table de gauche. La table après l’opérateur **Join** est la table de droite. Lorsque vous utilisez des colonnes de tables, le nom $left.Column et le nom $right.Column permettent de distinguer les colonnes auxquelles les tables font référence. L’opérateur **Join** prend en charge une gamme complète de types : flouter, inner, innerunique, leftanti, leftantisemi, leftouter, leftsemi, rightanti, rightantisemi, rightouter, rightsemi.

1. Vous pouvez laisser l’**intervalle de temps** défini sur **7 derniers jours** dans la fenêtre de requête.

### Tâche 7 : Utiliser des données de chaîne dans KQL

Dans cette tâche, vous allez utiliser des champs de chaîne structurés et non structurés avec des instructions KQL.

1. L’instruction suivante illustre la fonction **Extract**, qui obtient une correspondance pour une expression régulière à partir d’une chaîne source. Vous avez la possibilité de convertir la sous-chaîne extraite en type indiqué. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** : 

    ```KQL
    print extract("x=([0-9.]+)", 1, "hello x=45.6|wo") == "45.6"
    ```

1. Les instructions suivantes utilisent la fonction **extract** pour extraire le champ Account_s Name à partir du champ Account_s de la table SecurityEvent_CL. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** : 

    ```KQL
    SecurityEvent_CL  
    | where EventID_s == 4672 and AccountType_s == 'User' 
    | extend Account_Name = extract(@"^(.*\\)?([^@]*)(@.*)?$", 2, tolower(Account_s))
    | summarize LoginCount = count() by Account_Name
    | where Account_Name != "" 
    | where LoginCount < 10
    ```

1. L’instruction suivante illustre l’opérateur **Parse**, qui évalue une expression de chaîne et analyse sa valeur en une ou plusieurs colonnes calculées. À utiliser pour structurer des données non structurées. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    let Traces = datatable(EventText:string)
    [
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=23, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=15, lockTime=02/17/2016 08:40:00, releaseTime=02/17/2016 08:40:00, previousLockTime=02/17/2016 08:39:00)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=20, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=22, lockTime=02/17/2016 08:41:01, releaseTime=02/17/2016 08:41:00, previousLockTime=02/17/2016 08:40:01)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=16, lockTime=02/17/2016 08:41:00, releaseTime=02/17/2016 08:41:00, previousLockTime=02/17/2016 08:40:00)"
    ];
    Traces   
    | parse EventText with * "resourceName=" resourceName ", totalSlices=" totalSlices:long * "sliceNumber=" sliceNumber:long * "lockTime=" lockTime ", releaseTime=" releaseTime:date "," * "previousLockTime=" previousLockTime:date ")" *  
    | project resourceName, totalSlices, sliceNumber, lockTime, releaseTime, previousLockTime
    ```

1. Les instructions suivantes illustrent les opérateurs pour manipuler le JSON stocké dans des champs de chaîne. De nombreux journaux envoient des données au format JSON, ce qui vous oblige à savoir comment transformer des données JSON en champs pouvant être interrogés. Dans la fenêtre de requête, entrez l’instruction suivante, puis sélectionnez **Exécuter** :

    ```KQL
    SigninLogs_CL 
    | extend AuthDetails =  parse_json(AuthenticationDetails_s) 
    | extend AuthMethod =  AuthDetails[0].authenticationMethod 
    | extend AuthResult = AuthDetails[0].["authenticationStepResultDetail"] 
    | project AuthMethod, AuthResult, AuthDetails 
    ```

1. L’instruction suivante illustre l’opérateur **mv-expand**, qui transforme les tableaux dynamiques en lignes (expansion à valeurs multiples).

    ```KQL
    SigninLogs_CL 
    | mv-expand AuthDetails = parse_json(AuthenticationDetails_s) 
    | project AuthDetails
    ```

1. Développez la première ligne en sélectionnant « > », puis à nouveau en regard d’*AuthDetails* pour passer en revue les résultats développés.

1. L’instruction suivante illustre l’opérateur **mv-apply**, qui applique une sous-requête à chaque enregistrement et retourne l’union des résultats de toutes les sous-requêtes.

    ```KQL
    SigninLogs_CL 
    | mv-apply AuthDetails = parse_json(AuthenticationDetails_s) on
    (where AuthDetails.authenticationMethod == "Password")
    ```

1. Une **fonction** est une requête de journal qui peut être utilisée dans d’autres requêtes de journal avec le nom enregistré comme commande. Pour créer une **fonction**, après avoir exécuté votre requête, sélectionnez le bouton **Enregistrer**, puis **Enregistrer comme fonction** dans la liste déroulante. Entrez le nom de votre choix (par exemple : *PrivLogins*) dans la zone **Nom de la fonction**, puis entrez une **catégorie héritée** (par exemple : *Général*) et sélectionnez **Enregistrer**. La fonction est disponible dans KQL à l’aide de l’alias de la fonction :

    ```KQL
    PrivLogins  
    ```

## Vous avez terminé le labo
