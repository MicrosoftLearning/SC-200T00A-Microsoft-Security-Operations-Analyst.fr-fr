---
lab:
  title: "Exercice\_7 – Créer des détections"
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Parcours d’apprentissage 7 – Labo 1 – Exercice 7 – Créer des détections

## Scénario de l’exercice

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex7.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise ayant mis en œuvre Microsoft Sentinel. Vous allez travailler avec des requêtes KQL Log Analytics et à partir de là, vous allez créer des règles analytiques personnalisées pour vous aider à identifier les menaces et les comportements anormaux dans votre environnement.

Les règles analytiques recherchent des événements ou des ensembles d'événements spécifiques au sein de votre environnement, vous préviennent lorsque certains seuils ou conditions d’événements sont atteints, génèrent des incidents que votre centre des opérations de sécurité (SOC) doit trier et examiner, et répondent aux menaces grâce à des processus de suivi et de correction automatisés.


>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20detections)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques. 


### Tâche 1 : détection des attaques de persistance

>**Important :** les étapes suivantes sont effectuées sur une machine différente de celle que vous utilisiez précédemment. Recherchez les références de nom de machine virtuelle.

Dans cette tâche, vous allez créer une détection pour la première attaque de l’exercice précédent.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez l’espace de travail Microsoft Sentinel que vous avez créé précédemment.

1. Sous la section **Général**, sélectionnez *Journaux*.

1. **Réexécutez** l’instruction KQL suivante pour rappeler les tables où nous disposons de ces données :

    ```KQL
    search "temp\\startup.bat"
    ```

    >**Remarque :** un résultat avec l’événement peut prendre jusqu’à 5 minutes. Patientez jusqu’à ce que le résultat apparaisse. S’il n’apparaît pas, vérifiez que vous avez redémarré WINServer comme indiqué dans l’exercice précédent et que vous avez terminé la tâche 3 du labo du parcours d’apprentissage 6, exercice 2.

1. La table *SecurityEvent* semble avoir les données déjà normalisées et faciles à interroger. Développez la ligne pour afficher toutes les colonnes associées à l’enregistrement.

1. À partir des résultats, nous savons désormais que l’acteur de la menace utilise reg.exe pour ajouter des clés à la clé de Registre et que le programme se trouve dans C:\temp. **Exécutez** l’instruction suivante pour remplacer l’opérateur *Search* par l’opérateur *Where* dans notre requête :

    ```KQL
    SecurityEvent 
    | where Activity startswith "4688" 
    | where Process == "reg.exe" 
    | where CommandLine startswith "REG" 
    ```

1. Il est important d’aider l’analyste du centre des opérations de sécurité en fournissant autant de contexte sur l’alerte que possible. Cela inclut la projection d’entités à utiliser dans le graphe d’investigation. **Exécutez** la requête suivante :

    ```KQL
    SecurityEvent 
    | where Activity startswith "4688" 
    | where Process == "reg.exe" 
    | where CommandLine startswith "REG" 
    | extend timestamp = TimeGenerated, HostCustomEntity = Computer, AccountCustomEntity = SubjectUserName
    ```

1. Maintenant que vous disposez d’une bonne règle de détection, depuis la fenêtre Journaux, sélectionnez **+ Nouvelle règle d’alerte** dans la barre de commandes, puis **Créer une alerte Microsoft Sentinel**. Une règle planifiée est alors créée. **Conseil :** vous devrez peut-être sélectionner le bouton représentant des points de suspension (…) dans la barre de commandes.

1. L’Assistant Règle analytique s’ouvre alors. Pour le type d’onglet *Général* :

    |Paramètre|Valeur|
    |---|---|
    |Nom|Démarrage de RegKey|
    |Description|Démarrage de RegKey dans C:\temp|
    |Tactique|Persistance|
    |Gravité|Élevée|

1. Sélectionnez le bouton **Suivant : Définir la logique de la règle >**.

1. Dans l’onglet *Définir la logique de la règle*, la *requête de règle* doit être déjà remplie avec votre requête KQL, ainsi qu’avec les entités sous *Enrichissement des alertes – Mappage d’entités*.

    |Entité|Identificateur|Champ de données|
    |:----|:----|:----|
    |Compte|FullName|AccountCustomEntity|
    |Hôte|Nom d’hôte|HostCustomEntity|

1. Si le **nom d’hôte** n’est pas sélectionné pour l’entité *hôte*, sélectionnez-le dans la liste déroulante.

1. Pour la *planification de la requête*, définissez les éléments suivants :

    |Paramètre|Valeur|
    |---|---|
    |Exécuter la requête toutes les|5 minutes|
    |Rechercher les données des dernières|1 jour|

    >**Remarque :** nous générons volontairement de nombreux incidents pour les mêmes données. Cela permet au labo d’utiliser ces alertes.

1. Laissez les autres options par défaut. Sélectionnez le bouton **Suivant : Paramètres d’incident >**.

1. Sous l’onglet *Paramètres d’incident*, conservez les valeurs par défaut et sélectionnez le bouton **Suivant : Réponse automatique >**.

1. Dans l’onglet *Réponse automatique*, sous *Règles d’automatisation*, sélectionnez **Ajouter**.

1. Utilisez les paramètres de la table pour configurer la règle d’automatisation.

    |Paramètre|Valeur|
    |:----|:----|
    |Nom de la règle d'automatisation|Démarrage de RegKey|
    |Déclencheur|Lorsqu’un incident est créé|
    |Actions |Exécuter des playbooks|
    |playbook |PostMessageTeams-OnIncident|

    >**Remarque :** vous avez déjà attribué des autorisations au playbook. Il sera donc disponible.

1. Sélectionnez **Appliquer**

1. Sélectionnez ensuite le bouton **Suivant : Vérifier >**.
  
1. Sous l’onglet *Vérifier et créer*, sélectionnez le bouton **Créer** pour créer la nouvelle règle analytique planifiée.

### Tâche 2 : détection des attaques par élévation de privilèges

Dans cette tâche, vous allez créer une détection pour la deuxième attaque de l’exercice précédent.

1. Dans le portail Microsoft Sentinel, sélectionnez **Journaux** dans la section Général au cas où vous vous seriez éloigné de cette page.

1. **Exécutez** l’instruction KQL suivante pour identifier toute entrée qui fait référence aux administrateurs :

    ```KQL
    search "administrators" 
    | summarize count() by $table
    ```

1. Le résultat peut afficher des événements provenant de différentes tables, mais dans notre cas, nous voulons examiner la table SecurityEvent. L’EventID et l’événement que nous recherchons sont « 4732 – Un membre a été ajouté à un groupe local sécurisé ». Avec cela, nous allons identifier l’ajout d’un membre à un groupe privilégié. **Exécutez** la requête KQL suivante pour confirmer ce qui suit :

    ```KQL
    SecurityEvent 
    | where EventID == 4732
    | where TargetAccount == "Builtin\\Administrators"
    ```

1. Développez la ligne pour afficher toutes les colonnes associées à l’enregistrement. Le nom d’utilisateur du compte ajouté en tant qu’administrateur ou administratrice ne s’affiche pas Le problème est qu’au lieu de stocker le nom d’utilisateur, nous avons l’identificateur de sécurité (SID). **Exécutez** le KQL suivant pour faire correspondre le SID au nom d’utilisateur ajouté au groupe Administrateurs :

    ```KQL
    SecurityEvent 
    | where EventID == 4732
    | where TargetAccount == "Builtin\\Administrators"
    | extend Acct = MemberSid, MachId = SourceComputerId  
    | join kind=leftouter (
        SecurityEvent 
        | summarize count() by TargetSid, SourceComputerId, TargetUserName 
        | project Acct1 = TargetSid, MachId1 = SourceComputerId, UserName1 = TargetUserName) on $left.MachId == $right.MachId1, $left.Acct == $right.Acct1
    ```

   ![Capture d’écran](../Media/SC200_sysmon_attack3.png)

1. Étendez la ligne pour afficher les colonnes résultantes. Dans la dernière, nous voyons le nom de l’utilisateur ajouté sous la colonne *UserName1* que nous *projetons* dans la requête KQL. Il est important d’aider l’analyste des opérations de sécurité en fournissant autant de contexte sur l’alerte que possible. Cela inclut la projection d’entités à utiliser dans le graphe d’investigation. **Exécutez** la requête suivante :

    ```KQL
    SecurityEvent 
    | where EventID == 4732
    | where TargetAccount == "Builtin\\Administrators"
    | extend Acct = MemberSid, MachId = SourceComputerId  
    | join kind=leftouter (
        SecurityEvent 
        | summarize count() by TargetSid, SourceComputerId, TargetUserName 
        | project Acct1 = TargetSid, MachId1 = SourceComputerId, UserName1 = TargetUserName) on $left.MachId == $right.MachId1, $left.Acct == $right.Acct1
    | extend timestamp = TimeGenerated, HostCustomEntity = Computer, AccountCustomEntity = UserName1
    ```

1. Maintenant que vous disposez d’une bonne règle de détection, dans la fenêtre Journaux, sélectionnez **+ Nouvelle règle d’alerte** dans la barre de commandes, puis **Créer une alerte Microsoft Sentinel**. **Conseil :** vous devrez peut-être sélectionner le bouton représentant des points de suspension (…) dans la barre de commandes.

1. L’Assistant Règle analytique s’ouvre alors. Pour le type d’onglet *Général* :

    |Paramètre|Valeur|
    |---|---|
    |Nom|**SecurityEvent : ajout d’utilisateurs aux administrateurs locaux**|
    |Description|**Utilisateur ajouté au groupe Administrateurs local**|
    |Tactique|**Élévation des privilèges**|
    |Gravité|**Activité**|

1. Sélectionnez le bouton **Suivant : Définir la logique de la règle >**. 

1. Dans l’onglet *Définir la logique de la règle*, la *requête de règle* doit être déjà remplie avec votre requête KQL, ainsi qu’avec les entités sous *Enrichissement des alertes – Mappage d’entités*.

1. Pour la *planification de la requête*, définissez les éléments suivants :

    |Paramètre|Valeur|
    |---|---|
    |Exécuter la requête toutes les|5 minutes|
    |Rechercher les données des dernières|1 jour|

    >**Remarque :** nous générons volontairement de nombreux incidents pour les mêmes données. Cela permet au labo d’utiliser ces alertes.

1. Laissez les autres options par défaut. Sélectionnez le bouton **Suivant : Paramètres d’incident >**.

1. Sous l’onglet *Paramètres d’incident*, conservez les valeurs par défaut et sélectionnez le bouton **Suivant : Réponse automatique >**.

1. Dans l’onglet *Réponse automatique*, sous *Règles d’automatisation*, sélectionnez **Ajouter**.

1. Utilisez les paramètres de la table pour configurer la règle d’automatisation.

   |Paramètre|Valeur|
   |:----|:----|
   |Nom de la règle d'automatisation|SecurityEvent : ajout d’utilisateurs aux administrateurs locaux|
   |Déclencheur|Lorsqu’un incident est créé|
   |Actions |Exécuter des playbooks|
   |playbook |PostMessageTeams-OnIncident|

   >**Remarque :** vous avez déjà attribué des autorisations au playbook. Il sera donc disponible.

1. Sélectionnez **Appliquer**

1. Sélectionnez le bouton **Suivant : Vérifier et créer >**.
  
1. Sous l’onglet *Vérifier et créer*, sélectionnez le bouton **Créer** pour créer la nouvelle règle analytique planifiée.

## Passez à l’exercice 8
