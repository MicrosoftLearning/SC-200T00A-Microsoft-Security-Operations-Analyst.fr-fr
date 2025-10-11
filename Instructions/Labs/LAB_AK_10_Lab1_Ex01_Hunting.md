---
lab:
  title: "Exercice\_1\_: repérer les menaces dans Microsoft\_Sentinel"
  module: Learning Path 10 - Perform threat hunting in Microsoft Sentinel
---

# Parcours d’apprentissage 10 - Labo 1 - Exercice 1 - Repérer les menaces dans Microsoft Sentinel

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod8_L1_Ex1.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous avez reçu des informations selon lesquelles vous subissez une attaque par commande et contrôle (C2 ou C&C). Vous devez identifier la menace et la surveiller.

>**Important :** les exercices de laboratoire du parcours d’apprentissage #10 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

Les données de journal créées dans les exercices de labo du parcours d’apprentissage 9 ne seront pas disponibles dans ce labo sans réexécution des tâches préalables suivantes.

<!--- **[Lab 09 Exercise 5](https://microsoftlearning.github.io/SC-200T00A-Microsoft-Security-Operations-Analyst/Instructions/Labs/LAB_AK_09_Lab1_Ex05_Attacks.html)**

**[Lab 09 Exercise 6](https://microsoftlearning.github.io/SC-200T00A-Microsoft-Security-Operations-Analyst/Instructions/Labs/LAB_AK_09_Lab1_Ex06_Perform_Attacks.html)** --->

### Temps estimé pour terminer ce labo : 45 - 60 minutes

### Tâche préalable 1 : se connecter à un serveur local

Dans cette tâche, vous allez connecter un serveur local à votre abonnement Azure. Azure Arc a été préinstallé sur ce serveur. Le serveur sera utilisé dans les exercices suivants pour exécuter des attaques simulées que vous détecterez et étudierez ultérieurement dans Microsoft Sentinel.

>**Important :** les étapes suivantes sont effectuées sur une machine différente de celle que vous utilisiez précédemment. Recherchez le nom de l’ordinateur virtuel dans l’onglet des références.

1. Connectez-vous à la machine virtuelle **WINServer** en tant qu'Administrateur avec le mot de passe suivant : **Passw0rd!** si nécessaire.  

Comme décrit ci-dessus, Azure Arc a été préinstallé sur la machine **WINServer**. Vous allez maintenant connecter cette machine à votre abonnement Azure.

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

## Tâche préalable 2 : connecter une machine Windows non-Azure

Dans cette tâche, vous allez ajouter à Microsoft Sentinel une machine locale connectée à Azure Arc.  

>**Remarque :** Microsoft Sentinel a été prédéployé dans votre abonnement Azure avec le nom **defenderWorkspace** et les solutions *Content Hub* requises ont été installées.

1. Connectez-vous à la machine virtuelle **WIN1** en tant qu’administrateur ou administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Microsoft Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez le **defenderWorkspace** Microsoft Sentinel.

1. Dans le menu de navigation de gauche de Microsoft Sentinel, faites défiler jusqu’à la section *Configuration* et sélectionnez **Connecteurs de données**.

1. Dans les *Connecteurs de données*, recherchez la solution **Événements de sécurité Windows via le connecteur AMA** et sélectionnez-la dans la liste.

1. Sélectionnez *Événements de sécurité Windows via le connecteur AMA* dans le volet d’informations, puis choisissez **Ouvrir la page du connecteur**.

    >**Remarque :** la solution *Événements de sécurité Windows* installe les connecteurs de données *Événements de sécurité Windows via AMA* et *Événements de sécurité via l’ancien agent*. Plus 2 classeurs, 20 règles analytiques et 43 requêtes de repérage.

1. Dans la section *Configuration*, sous l’onglet *Instructions*, sélectionnez **Créer une règle de collecte de données**.

1. Entrez **AZWINDCR** pour le nom de la règle, puis sélectionnez **Suivant : Ressources**.

1. Développez votre *Abonnement* sous *Étendue* dans l’onglet *Ressources*.

    >**Conseil :** Vous pouvez développer l’ensemble de la hiérarchie *Étendue* en sélectionnant « > » devant la colonne *Étendue*.

1. Développez le groupe de ressources **defender-RG**, puis sélectionnez **WINServer**.

1. Sélectionnez **Suivant : collecter** et laissez l’option *Tous les événements de sécurité* sélectionné.

1. Sélectionnez **Suivant : Vérifier + créer**.

1. Sélectionnez **Créer** une fois que *Validation réussie* s’affiche.

### Tâche préalable 3 : attaque de contrôle et commande avec DNS

>**Important :** les étapes suivantes sont effectuées sur une machine différente de celle que vous utilisiez précédemment. Recherchez le nom de l’ordinateur virtuel dans l’onglet des références.

1. Connectez-vous à la machine virtuelle **WINServer** en tant qu'Administrateur avec le mot de passe suivant : **Passw0rd!** si nécessaire.

1. Sur la machine *WINServer*, sélectionnez l’icône de *recherche* et entrez **cmd**.

1. Dans les résultats de la recherche, cliquez sur *Invite de commandes* avec le bouton droit, puis sélectionnez **Exécuter en tant qu’administrateur**.

1. Copiez et exécutez cette commande pour créer un script qui simulera une requête DNS sur un serveur C2 :

    ```CommandPrompt
    notepad c2.ps1
    ```

1. Sélectionnez **Oui** pour créer un fichier et copier le script PowerShell suivant dans *c2.ps1*.

    >**Remarque :** le collage dans le fichier de machine virtuelle peut ne pas afficher la longueur complète du script. Vérifiez que le script correspond aux instructions contenues dans le fichier *c2.ps1*.

    ```PowerShell
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

1. Dans le menu Bloc-notes, sélectionnez **Fichier**, puis **Enregistrer**. 

1. Revenez à la fenêtre d’invite de commandes, tapez la commande suivante et appuyez sur Entrée. 

    >**Remarque :** vous verrez les erreurs de résolution DNS. Ceci est normal.

    ```CommandPrompt
    Start PowerShell.exe -file c2.ps1
    ```

>**Important :** ne fermez pas ces fenêtres. Laissez ce script PowerShell s’exécuter en arrière-plan. La commande doit générer des entrées de journal pendant quelques heures. Vous pouvez passer à la tâche suivante et aux exercices suivants pendant l’exécution de ce script. Les données créées par cette tâche seront utilisées dans le labo Repérage des menaces ultérieurement. Ce processus ne crée pas de quantités substantielles de données ou de traitement.

### Tâche 1 : créer une requête de repérage

Dans cette tâche, vous allez créer une requête de repérage, ajouter un signet à un résultat et créer un livestream.

>**Remarque :** Microsoft Sentinel a été prédéployé dans votre abonnement Azure avec le nom **defenderWorkspace** et les solutions *Content Hub* requises ont été installées.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Microsoft Edge, accédez au portail Azure à l’adresse <https://portal.azure.com>.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez le **defenderWorkspace** Microsoft Sentinel.

1. Sélectionnez **Journaux**.

1. Entrez l’instruction KQL suivante dans l’espace *Nouvelle requête 1* :

   >**Important :** collez d’abord toutes les requêtes KQL dans le Bloc-notes pour éviter toute erreur, puis copiez-les dans la fenêtre du journal *Requête 1*.

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam 
    | order by count_ desc nulls last 
    ```

1. Passez en revue les différents résultats. Vous avez maintenant identifié les requêtes PowerShell qui s’exécutent dans votre environnement.

1. Cochez la case *« -file c2.ps1 »* qui s’affiche dans les résultats. 

1. Dans la barre de commandes du volet *Résultats*, sélectionnez le bouton **Ajouter un signet**.

1. Sélectionnez **+ Ajouter une nouvelle entité** sous *Mappage d’entités*.

1. Pour *Entité*, sélectionnez les valeurs **Hôte**, puis **Nom d’hôte** et **Ordinateur**.

1. Pour les *Tactiques et techniques*, sélectionnez **Commande et contrôle**.

1. Dans le volet *Ajouter un signet*, sélectionnez **Créer**. Nous allons mapper ce signet à un incident plus loin dans ce labo.

1. Fermez la fenêtre *Journaux* en cliquant sur **X** en haut à droite de la fenêtre, puis sélectionnez **OK** pour ignorer les modifications. 

1. Sélectionnez à nouveau votre espace de travail Microsoft Sentinel et accédez à la page **Repérage** dans la zone *Gestion des menaces*.

1. Sélectionnez l’onglet **Requêtes**, puis **+ Nouvelle requête** dans la barre de commandes.

1. Dans la fenêtre *Créer une requête personnalisée*, dans le champ *Nom*, entrez **Repérage PowerShell**.

1. Dans le champ *Requête personnalisée*, entrez l’instruction KQL suivante :

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam 
    | order by count_ desc nulls last 
    ```

1. Faites défiler vers le bas et sous *Mappage d’entités*, sélectionnez :

    - Pour la liste déroulante *Type d’entité*, sélectionnez **Hôte**.
    - Pour la liste déroulante *Identificateur*, sélectionnez **Nom d’hôte**.
    - Pour la liste déroulante *Valeur*, sélectionnez **Ordinateur**.

1. Faites défiler vers le bas et sous *Tactiques et Techniques*, sélectionnez **Commande et contrôle**, puis **Créer** pour créer la requête de repérage.

1. Dans le panneau *« Microsoft Sentinel - Repérage »,* recherchez la requête que vous venez de créer dans la liste, à savoir *Repérage PowerShell*.

1. Sélectionnez **Repérage PowerShell** dans la liste.

1. Passez en revue le nombre de résultats dans le volet central sous la colonne *Résultats*.

1. Sélectionnez le bouton **Afficher les résultats** dans le volet droit. Votre requête KQL est exécutée automatiquement.

1. Fermez la fenêtre *Journaux* en cliquant sur **X** en haut à droite de la fenêtre, puis sélectionnez **OK** pour ignorer les modifications. 

1. Cliquez avec le bouton droit sur la requête **Repérage PowerShell** et sélectionnez **Ajouter à livestream**. **Conseil :** vous pouvez également effectuer cette opération en faisant glisser vers la droite et en sélectionnant les points de suspension **(...)** à la fin de la ligne afin d’ouvrir un menu contextuel.

1. Vérifiez que l’*État* est *En cours d’exécution*. La requête s’exécute toutes les 30 secondes en arrière-plan. Vous recevrez une notification dans le portail Azure (icône en forme de cloche) en cas de nouveau résultat. 

1. Sélectionnez l’onglet **Signets** dans le volet central.

1. Sélectionnez le signet que vous avez créé dans la liste des résultats.

1. Dans le volet droit, faites défiler vers le bas et sélectionnez le bouton **Examiner**. **Conseil :** l’affichage du graphique d’examen peut prendre quelques minutes.

1. Consultez le graphique d’examen comme vous l’avez fait dans le module précédent. Notez le nombre élevé d’*Alertes associées* pour *WINServer*.

1. Fermez la fenêtre du graphique d’ *Examen* en sélectionnant le bouton **X** en haut à droite de la fenêtre. 

1. Masquez le panneau droit en sélectionnant l’icône **>>**, puis faites défiler vers la droite jusqu’à l’icône des points de suspension **(...)**.

1. Sélectionnez **Ajouter à un incident existant**. Tous les incidents apparaissent dans le volet droit.

1. Sélectionnez l’un des incidents, puis cliquez sur **Ajouter**.

1. Faites défiler vers la gauche jusqu’à la colonne *Gravité*. Vous verrez alors qu’elle contient les données relatives à l’incident.

### Tâche 2 : créer une règle de requête NRT

Dans cette tâche, au lieu d’utiliser un livestream, vous allez créer une règle de requête d’analytique NRT. Les règles NRT s’exécutent toutes les minutes, avec une période de recherche arrière d’une minute. L’avantage des règles NRT est qu’elles peuvent utiliser la logique de création d’alerte et d’incident.

1. Dans Microsoft Sentinel, sous *Configuration*, sélectionnez la page **Analytique**. 

1. Sélectionnez l’onglet **Créer**, puis **Règle de requête NRT**.

1. L’Assistant Règle d’analytique s’ouvre alors. Pour le type d’onglet *Général* :

    |Paramètre|Valeur|
    |---|---|
    |Nom|**Repérage PowerShell NRT**|
    |Description|**Repérage PowerShell NRT**|
    |Tactique|**Commande et contrôle**|
    |Niveau de gravité|**Activité**|

1. Sélectionnez le bouton **Suivant : Définir la logique de la règle >**. 

1. Pour la *Règle de requête*, entrez l’instruction KQL suivante :

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam
    ```

1. Sélectionnez **Afficher les résultats de la requête >** pour vous assurer que votre requête ne contient pas d’erreurs.

1. Fermez la fenêtre *Journaux* en cliquant sur **X** en haut à droite de la fenêtre, puis sélectionnez **OK** pour ignorer les modifications. 

1. Sous *Simulation des résultats*, sélectionnez **Tester avec les données actuelles**. Notez le nombre attendu d’*Alertes par jour*.

1. Dans la section *Amélioration de l’alerte*, sélectionnez *Mappage d’entités >*, **+ Ajouter une nouvelle entité**.

1. Dans l’*Entité*, sélectionnez :

    - Pour la liste déroulante *Type d’entité*, sélectionnez **Hôte**.
    - Pour la liste déroulante *Identificateur*, sélectionnez **Nom d’hôte**.
    - Pour la liste déroulante *Valeur*, sélectionnez **Ordinateur**.

1. Faites défiler vers le bas et sélectionnez le bouton **Suivant : Paramètres d’incident>**.

1. Sous l’onglet *Paramètres d’incident*, conservez les valeurs par défaut et sélectionnez le bouton **Suivant : Réponse automatisée >**.

1. Sous l’onglet *Réponse automatique*, sélectionnez le bouton **Suivant : examiner et créer**.

1. Sous l’onglet *Vérifier et créer*, sélectionnez le bouton **Enregistrer** pour créer et enregistrer la nouvelle règle d’analytique planifiée.

### Tâche 3 : créer un travail de recherche

Dans cette tâche, vous allez effectuer un travail de recherche pour rechercher un serveur C2.

**Note :** l’opération *Restaurer* entraîne des coûts qui peuvent entamer vos crédits d’abonnement Azure. Pour cette raison, vous n’effectuerez pas l’opération de restauration dans ce labo. Toutefois, vous pouvez suivre les étapes ci-dessous pour effectuer l’opération de restauration dans votre propre environnement.

1. Dans Microsoft Sentinel, sous *Général*, sélectionnez la page **Rechercher**.

1. Tapez **reg.exe** dans la zone de recherche, puis cliquez sur **Démarrer**.

1. Une nouvelle fenêtre exécutant la requête s’ouvre. Sélectionnez l’icône des points de suspension ** (...)** en haut à droite, puis passez en **Mode de travail de recherche**.

1. Sélectionnez le bouton **Travail de recherche** dans la barre de commandes. 

1. Le travail de recherche crée une table avec vos résultats dès qu’ils sont transmis. Les résultats peuvent être consultés à partir de l’onglet *Recherches enregistrées*.

1. Fermez la fenêtre *Journaux* en cliquant sur **X** en haut à droite de la fenêtre, puis sélectionnez **OK** pour ignorer les modifications.

1. Sélectionnez l’onglet **Restauration** dans la barre de commandes, puis cliquez sur le bouton **Restaurer** .

1. Sous *Sélectionner une table à restaurer*, recherchez et sélectionnez **SecurityEvent**.

1. Passez en revue les options disponibles, puis sélectionnez le bouton **Annuler**.

    >**Remarque :** si vous exécutez le travail, la restauration durera quelques minutes et vos données seront disponibles dans une nouvelle table.

### Tâche 4 : créer un repérage qui combine plusieurs requêtes dans une tactique MITRE

1. La carte MITRE ATT CK vous aide à identifier des lacunes spécifiques de votre couverture de détection. Utilisez des requêtes de chasse prédéfinies pour des techniques MITRE ATT CK spécifiques comme point de départ pour développer une nouvelle logique de détection.

1. Dans Microsoft Sentinel, développez **Gestion des menaces** dans les menus de navigation de gauche.

1. Sélectionnez **MITRE ATT&CK (version préliminaire)**.

1. Désélectionnez les éléments dans le menu déroulant *Règles actives*.

1. Sélectionnez **Requêtes de repérage** dans le filtre *Règles simulées* pour voir les techniques auxquelles sont associées des requêtes de repérage.

1. Sélectionnez la carte pour la **manipulation de compte**.

1. Dans le volet d’informations, recherchez la *couverture simulée* et sélectionnez le lien **Affichage** en regard des *requêtes de repérage*.

1. Ce lien vous dirige vers une vue filtrée de l’onglet Requêtes de la page Chasse en fonction de la technique que vous avez sélectionnée.

1. Sélectionnez toutes les requêtes de cette technique en sélectionnant la zone située en haut de la liste à gauche.

1. Sélectionnez le **menu déroulant Actions de repérage** au milieu de l’écran, au-dessus des filtres.

1. Sélectionnez **Créer un repérage**. Toutes les requêtes que vous avez sélectionnées sont clonées pour cette nouvelle chasse.

1. Renseignez le nom de la chasse et les champs facultatifs. La description est l’endroit idéal pour mettre des mots sur votre hypothèse. Le menu déroulant Hypothèse est l’endroit où vous définissez le statut de votre hypothèse de travail.

1. Sélectionnez **Créer** pour commencer.

1. Sélectionnez l’onglet **Chasses (préversion)** pour afficher votre nouvelle chasse.

1. Sélectionnez le lien de chasse par nom pour afficher les détails et effectuer des actions.

1. Affichez le volet d’informations contenant le nom de la chasse, la description, le contenu, l’heure de la dernière mise à jour et l’heure de création.

1. Sélectionnez toutes les requêtes à l’aide de la zone en regard de la colonne *Requête*.

1. Sélectionnez **Exécuter les requêtes sélectionnées** ou décochez les lignes sélectionnées, puis *cliquez avec le bouton droit* et **exécutez** une seule requête.

1. Vous pouvez également sélectionner une requête unique et sélectionner **Afficher les résultats** dans le volet d’informations.

1. Passez en revue les résultats retournés.

1. En fonction des résultats, déterminez s’il existe suffisamment de preuves solides pour valider l’hypothèse. Si ce n’est pas le cas, fermez le repérage et marquez-le comme invalidé.

1. Étapes alternatives :
    - Accédez à Microsoft Sentinel.
    - Développez Gestion des menaces.
    - Choisissez Repérage.
    - Sélectionnez Ajouter un filtre.
    - Définissez le filtre sur tactiques:persistence.
    - Ajoutez un autre filtre.
    - Définissez le deuxième filtre pour qu’il contienne des techniques : T1098.

## Passez à l’exercice 2
