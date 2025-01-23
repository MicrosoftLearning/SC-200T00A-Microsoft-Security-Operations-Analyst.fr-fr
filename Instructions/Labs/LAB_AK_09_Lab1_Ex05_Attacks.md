---
lab:
  title: "Exercice\_5\_: se préparer à effectuer des attaques simulées"
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Parcours d’apprentissage 9, Laboratoire 1, Exercice 5 : se préparer à effectuer des attaques simulées

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod9_L1_Ex5.png)

### Temps estimé pour terminer ce labo : 30 minutes

### Tâche 1 : connexion à un serveur local

Dans cette tâche, vous allez connecter un serveur local à votre abonnement Azure. Azure Arc a été préinstallé sur ce serveur. Le serveur sera utilisé dans les exercices suivants pour exécuter des attaques simulées que vous détecterez et étudierez ultérieurement dans Microsoft Sentinel.

>**Remarque :** les exercices de laboratoire du parcours d’apprentissage #9 se trouvent dans un *environnement autonome*. Si vous quittez le labo sans enregistrer, vous devrez réexécuter certaines configurations.

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

1. Dans la boîte de dialogue *Connexion*, entrez l’**e-mail du locataire** et le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**. Attendez le message *Authentification terminée*, fermez l’onglet du navigateur et revenez à la fenêtre *Invite de commandes*.

1. Une fois les commandes exécutées, laissez la fenêtre *Invite de commandes* ouverte et entrez la commande suivante pour vérifier que la connexion a réussi :

    ```cmd
    azcmagent show
    ```

1. Dans la sortie de la commande, vérifiez que l’*état de l’agent* est **Connecté**.

## Tâche 2 : connecter une machine Windows non-Azure

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

### Tâche 3 : comprendre les attaques

>**Important : vous n’effectuerez aucune action dans cet exercice.**  Ces instructions décrivent simplement les attaques que vous allez effectuer dans l’exercice suivant. Veuillez lire attentivement cette page.

Les modèles d’attaque sont basés sur un projet open source : <https://github.com/redcanaryco/atomic-red-team>

#### Attaque 1 : persistance avec l’ajout de la clé de Registre

Les attaquants ajoutent un programme dans la clé Exécuter le Registre. La persistance est obtenue en exécutant le programme à chaque fois que l’utilisateur se connecte.

```
REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"
```

#### Attaque 2 : ajout d’un utilisateur et élévation des privilèges

Les attaquants ajoutent de nouveaux utilisateurs et élèvent leurs privilèges au niveau du groupe Administrateurs. L’attaquant peut alors se connecter avec un autre compte élevé.

```
net user theusernametoadd /add
net user theusernametoadd ThePassword1!
net localgroup administrators theusernametoadd /add
```

#### Attaque 3 : DNS / C2

L’attaquant envoie un nombre élevé de requêtes DNS à un serveur de commande et contrôle (C2). L’objectif est de déclencher une détection basée sur des seuils en fonction du nombre de requêtes DNS provenant d’un système source unique ou d’un domaine cible unique.

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

### Tâche 4 : comprendre la modélisation de la détection

Le cycle de configuration de détection d’attaque utilisé dans ce labo représente toutes les sources de données, même si vous ne vous concentrez que sur deux sources de données spécifiques.

Pour créer une détection, commencez par écrire une instruction KQL. Étant donné que vous attaquerez un hôte, vous aurez des données à son sujet pour commencer à générer l’instruction KQL.

Une fois l’instruction KQL prête, vous devez créer la règle analytique.

Le déclenchement de la règle entraîne la création d’alertes et d’incidents. Examinez-les pour déterminer si vous communiquez des champs aux analystes des opérations de sécurité pour les aider dans leur investigation.

Vous devez ensuite apporter d’autres modifications à la règle analytique.

>**Remarque :** certaines alertes sont déclenchées dans un délai plus court uniquement dans le cadre de notre labo.

## Passez à l’exercice 6
