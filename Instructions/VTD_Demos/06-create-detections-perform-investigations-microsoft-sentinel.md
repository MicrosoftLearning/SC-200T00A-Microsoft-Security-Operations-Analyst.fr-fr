# Module 6 : création de détections et investigations avec Microsoft Sentinel

**Remarque** : la réussite de cette démonstration dépend de l’exécution correcte de toutes les étapes décrites dans le [document sur les conditions préalables](00-prerequisites.md). 

## Créer une règle de requête NRT

Dans cette tâche, vous allez créer une règle de requête d’analytique NRT (en quasi-temps réel).

1. Dans Microsoft Sentinel, sous *Configuration*, sélectionnez la page **Analytique**.

1. Sélectionnez l’onglet **Créer**, puis **Règle de requête NRT**.

1. L’Assistant Règle d’analytique s’ouvre alors. Pour l’onglet *Général*, saisissez les valeurs suivantes :

    |Paramètre|Valeur|
    |---|---|
    |Nom|**Repérage PowerShell NRT**|
    |Description|**Repérage PowerShell NRT**|
    |Tactiques et techniques|**Commande et contrôle**|
    |Niveau de gravité|**Activité**|

1. Sélectionnez le bouton **Suivant : Définir la logique de la règle >**. 

1. Pour la *Requête de règle*, entrez l’instruction KQL suivante :

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

1. Fermez la fenêtre *Journaux* en cliquant sur le bouton **X** en haut à droite de la fenêtre, puis sélectionnez **OK** pour ignorer les modifications. 

1. Sous *Simulation des résultats*, sélectionnez **Tester avec les données actuelles**. Notez le nombre attendu d’*Alertes par jour*.

1. Sous *Mappage d’entités*, sélectionnez :

    - Pour la liste déroulante *Type d’entité*, sélectionnez **Hôte**.
    - Pour la liste déroulante *Identificateur*, sélectionnez **Nom d’hôte**.
    - Pour la liste déroulante *Valeur*, sélectionnez **Ordinateur**.

1. Faites défiler vers le bas et sélectionnez le bouton **Suivant : Paramètres d’incident>**.

1. Sous l’onglet *Paramètres d’incident*, conservez les valeurs par défaut et sélectionnez le bouton **Suivant : Réponse automatisée >**.

1. Sélectionnez **Suivant : Vérifier + créer >**.

1. Sous l’onglet *Vérifier et créer*, sélectionnez le bouton **Enregistrer** pour créer et enregistrer la nouvelle règle d’analytique planifiée.

## Détection des attaques Windows configurée avec l’agent Azure Monitor (AMA)

Dans cette tâche, vous allez examiner l’incident créé à partir de la règle `NRT` que vous avez créée.

1. Connectez-vous à la machine virtuelle WIN1 en tant qu’Administrateur avec le mot de passe suivant : **Pa55w.rd**.  

1. Dans le navigateur Edge, accédez au Portail Azure à l’adresse https://portal.azure.com.

1. Dans la boîte de dialogue **Se connecter**, copiez et collez le compte **E-mail du locataire** pour l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Suivant**.

1. Dans la boîte de dialogue **Entrer le mot de passe**, copiez et collez le **Mot de passe du locataire** pour l’administrateur fourni par votre fournisseur d’hébergement de labo, puis sélectionnez **Se connecter**.

1. Dans la barre de recherche du Portail Azure, tapez *Sentinel*, puis sélectionnez **Microsoft Sentinel**.

1. Sélectionnez l’espace de travail Microsoft Sentinel que vous avez créé précédemment.

1. Dans `Microsoft Sentinel`, accédez à la section du menu `Threat management` et sélectionnez **Incidents**.

**Remarque** : l’affichage de l’`Incident` peut prendre plusieurs minutes.

1. Vous devez voir un incident qui correspond à la `Severity` et au `Title` que vous avez configurés dans la règle `NRT` que vous avez créée.

1. Sélectionnez l’`Incident`. Le volet de `detail` s’ouvre alors.

1. Sélectionnez **Afficher tous les détails**, puis le bouton **Examiner**.

1. Explorez les `Entities` associées à l’incident `NRT PowerShell Hunt`.

1. Fermez la fenêtre `Investigation` en cliquant sur le bouton **X** en haut à droite de la fenêtre.

1. Sélectionnez l’onglet `Logs` et entrez l’instruction KQL suivante :

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam
    ```

**Remarque** : vous pouvez retrouver cette requête dans l’`Queries History` et l’**Exécuter** à partir de ce menu.

1. Sélectionnez le bouton **Terminé** pour fermer la fenêtre `Logs`.

1. Fermez la fenêtre `Incident` en cliquant sur le bouton **X** en haut à droite de la fenêtre.

## Vous avez terminé la démonstration.
