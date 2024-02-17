# Module 7 : Repérage des menaces dans Microsoft Sentinel

**Remarque** : la réussite de cette démonstration dépend de l’exécution correcte de toutes les étapes décrites dans le [document sur les conditions préalables](00-prerequisites.md). 

## Créer une requête de repérage

Dans cette tâche, vous allez créer une requête de repérage, ajouter un signet à un résultat et créer un livestream.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur ou Administratrice avec le mot de passe : **Pa55w.rd**.  

1. Dans le navigateur Edge, accédez au portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Connexion**, copiez et collez le compte de **messagerie du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer un mot de passe**, copiez et collez le **mot de passe du locataire** fourni par l’hébergeur du labo, puis sélectionnez **Connexion**.

1. Dans la barre de recherche du portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez votre espace de travail Microsoft Sentinel.

1. Sélectionnez **Journaux**. 

1. Entrez l’instruction KQL suivante dans l’espace Nouvelle requête 1 :

```KQL
let lookback = 2d;
DeviceEvents | where TimeGenerated >= ago(lookback) 
| where ActionType == "DnsQueryResponse"
| extend c2 = substring(tostring(AdditionalFields.DnsQueryString),0,indexof(tostring(AdditionalFields.DnsQueryString),"."))
| where c2 startswith "sub"
| summarize count() by bin(TimeGenerated, 3m), c2
| where count_ > 5
| render timechart 
```

1. L’objectif de cette instruction est de fournir une visualisation pour rechercher un signal C2 à partir d’une base cohérente.  Prenez le temps d’ajuster le paramètre de 3m à 30s et plus.  Changez le paramètre count_ > 5 pour d’autres grandeurs de seuil afin d’en observer l’impact.

1. Vous avez maintenant identifié les requêtes DNS qui sont signalées sur un serveur C2.  Ensuite, déterminez les appareils qui font l’objet d’un signalement.  Entrez l’instruction KQL suivante :

```KQL
let lookback = 2d;
DeviceEvents | where TimeGenerated >= ago(lookback) 
| where ActionType == "DnsQueryResponse"
| extend c2 = substring(tostring(AdditionalFields.DnsQueryString),0,indexof(tostring(AdditionalFields.DnsQueryString),".")) 
| where c2 startswith "sub"
| summarize cnt=count() by bin(TimeGenerated, 5m), c2, DeviceName
| where cnt > 15
```

**Remarque** Les données de journal générées proviennent seulement de l’appareil intégré.

1. Fermez la fenêtre *Journaux* en cliquant sur **X** en haut à droite de la fenêtre, puis sélectionnez **OK** pour ignorer les modifications. 

1. Sélectionnez la page **Repérage** dans la zone Gestion des menaces du portail Microsoft Sentinel.

1. Sélectionnez **Nouvelle requête** dans la barre de commandes.

1. Dans la fenêtre *Créer une requête personnalisée*, pour le type *Nom*, tapez **C2 Hunt**

1. Dans le champ *Requête personnalisée*, entrez l’instruction KQL suivante :

```KQL
let lookback = 2d;
DeviceEvents | where TimeGenerated >= ago(lookback) 
| where ActionType == "DnsQueryResponse"
| extend c2 = substring(tostring(AdditionalFields.DnsQueryString),0,indexof(tostring(AdditionalFields.DnsQueryString),"."))
| where c2 startswith "sub"
| summarize cnt=count() by bin(TimeGenerated, 5m), c2, DeviceName
| where cnt > 15
```

1. Faites défiler vers le bas puis, sous *Mappage d’entité (préversion)*, sélectionnez :

    - Pour la liste déroulante *Type d’entité*, sélectionnez **Hôte**.
    - Pour la liste déroulante *Identificateur*, sélectionnez **Nom d’hôte**.
    - Pour la liste déroulante *Valeur*, sélectionnez **DeviceName**.

1. Faites défiler vers le bas et sous *Tactiques et Techniques*, sélectionnez **Commande et contrôle**, puis **Créer** pour créer la requête de repérage.

1. Dans le panneau *« Microsoft Sentinel - Repérage »*, recherchez dans la liste la requête que vous venez de créer, *C2 Hunt*.

1. Sélectionnez **C2 Hunt** dans la liste.

1. Dans le volet droit, faites défiler vers le bas, puis sélectionnez le bouton **Exécuter la requête**.

1. Le nombre de résultats est affiché dans le volet central sous la colonne *Résultats*. Vous pouvez également faire défiler vers le haut jusqu’à afficher le nombre sur la zone *Résultats*.

1. Sélectionnez **Afficher les résultats**.

1. Sélectionnez la première ligne des résultats. 

1. Sélectionnez **Ajouter un signet**.

1. Sélectionnez **Créer** dans le volet qui s’affiche.

1. Revenez à la page Repérage dans le portail Microsoft Sentinel.

1. Sélectionnez l’onglet **Signets**.

1. Sélectionnez le signet dans la liste des résultats.

1. Sélectionnez **Examiner** dans le volet flottant.

1. Explorez le graphique Investigation.

1. Revenez à la page Repérage dans le portail Microsoft Sentinel.

1. Sélectionnez l’onglet **Requêtes**.

1. Sélectionnez la requête **C2 Hunt**.

1. Sélectionnez **...** à la fin de la ligne pour ouvrir le menu contextuel.

1. Sélectionnez **Ajouter à Livestream**.

## Vous avez terminé la démonstration.